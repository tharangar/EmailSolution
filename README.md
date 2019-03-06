# EmailSolution


This Email solution is dockerized email solution.


## Functionalities
- Core
  - [x] ESMTP Server 
    - [POSTFIX](http://www.postfix.org/) : a modular mail transfer agent.
  - [x] IMAP Server and POP Server
    - [DOVECOT](https://www.dovecot.org/) : secure open-source IMAP and POP3 server.
  - [x] WEBmail client
    - [RAINLOOP](https://www.rainloop.net/) : Webmail client with basic features.
  - [x] Spam Filter
    - [RSPAMD](https://rspamd.com/) : Fast, free and open-source spam filtering system. You may find a comparison of spam filters [here](https://rspamd.com/comparison.html).
  - [x] Antivirus 
    - [ClamAV](https://www.clamav.net/) : is an open source antivirus engine for detecting trojans, viruses, malware & other malicious threats.
  - [x] Security enhancement
    - [DKIM](http://www.dkim.org/) : DomainKeys Identified Mail (DKIM) lets an organization take responsibility for a message that is in transit.


## How to Setup

### Before We Start

Make sure any other application does not use ports that we are going to listen to

```
$ netstat -tulpn | grep -E -w '25|80|110|143|443|465|587|993|995|4190|11334'

//check each port

$ sudo lsof -i :25
```

### Firewall

Unblock following ports

| Service | Software | Protocol | Port |
| ------- | -------- | -------- | ---- |
| SMTP | Postfix | TCP | 25 |
| IMAP | Dovecot | TCP | 143 |
| SMTPS | Postfix | TCP | 465 |
| Submission | Postfix | TCP | 587 |
| IMAPS | Dovecot | TCP | 993 |





## Installation

1. Clone this Repository

```
$ git clone https://github.com/tharangar/EmailSolution.git
```

2. Edit .env file to replicate your settings


## Running

Build and run the image
```
cd emailserver
docker build -t emailserver .

docker run -p 127.0.0.1:25:25 143:143 587:587 --name emailserver -d emailserver

```
Run the application using docker composer.
```

$ docker-compose build
```
```
$ docker-compose up -d 
```



This email solution user baed is openldap by default.
But it is expected to improve it with postfixadmin stufs.
Openldap solution is not included hear.
It has to be built externally.
      
                      
## References 
- Email solution initiated by Prabod Rathnayaka. url :   
  https://github.com/prabod/email-solution/tree/master/docker

- Email solution with rspamd
  https://github.com/tomav
  
- openLdap solutions
  https://github.com/osixia/docker-openldap#quick-start

<!-- Prometheus container pull and run: 
    sudo docker pull prom/prometheus
    docker run -p 9090:9090 prom/prometheus

Grafana pull and run
    docker pull grafana/grafana
    docker run -d --name=grafana -p 3000:3000 grafana/grafana -->
    


