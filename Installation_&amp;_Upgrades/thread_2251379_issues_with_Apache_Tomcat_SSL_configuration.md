---
title: "issues with Apache Tomcat SSL configuration"
date: 2014-11-03
forum: Installation &amp; Upgrades
---

### Post by chaitra on 2014-11-03
Hi Everyone,
I'm a newbie. I was trying to configure SSL onto Tomcat. Everything seemed fine. But when I give [http://localhost:8080](http://localhost:8080) it works but wen I give https//localhost:8443, it just shows loading and nothing turns up. 
I made the following changes in the server.xml file

   <Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true"
               maxThreads="150" scheme="https" secure="true"
               clientAuth="false" sslProtocol="TLS" 
                keystoreFile="key_store"
                keystorePass="password" />

When i check netstat -tupan| grep 8080, I get
tcp6       0      0 :::8080                 :::*                    LISTEN      10444/java

But netsta -tupan | grep 8443 gives me 

tcp        0      0 127.0.0.1:48131         127.0.0.1:8443          ESTABLISHED 10235/libpepflashpl
tcp        0      0 127.0.0.1:48545         127.0.0.1:8443          ESTABLISHED 2161/firefox    
tcp6       0      0 :::8443                 :::*                    LISTEN      10444/java      
tcp6     293      0 127.0.0.1:8443          127.0.0.1:48129         CLOSE_WAIT  -               
tcp6     163      0 127.0.0.1:8443          127.0.0.1:48340         CLOSE_WAIT  -               
tcp6     292      0 127.0.0.1:8443          127.0.0.1:48545         ESTABLISHED -               
tcp6     392      0 127.0.0.1:8443          127.0.0.1:48131         ESTABLISHED - 


I'm not sure of this output. I'm not sure what I did wrong in the modifying the file that I'm not able to connect to 8443 port.
Can anyone help me out with this please?

---

