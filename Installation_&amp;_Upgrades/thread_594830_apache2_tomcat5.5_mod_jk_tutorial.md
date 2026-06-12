---
title: "apache2 tomcat5.5 mod_jk tutorial?"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by ture_atlantis on 2007-10-28
Does anyone have a tutorial or howto on installing tomcat5.5 and mod jk for it?  

root@atlantis-laptop:/usr/share/tomcat5.5# /etc/init.d/tomcat5.5 start
 * Starting Tomcat servlet engine tomcat5.5                              [ OK ] 
root@atlantis-laptop:/usr/share/tomcat5.5# /etc/init.d/apache2 start
 * Starting web server (apache2)...                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
root@atlantis-laptop:/usr/share/tomcat5.5# netstat -tupan | grep -i listen
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     22270/apache2       
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     22270/apache2       
tcp6       0      0 :::22                   :::*                    LISTEN     5227/sshd           
root@atlantis-laptop:/usr/share/tomcat5.5# 


It seems like its starting ok, but i have nothing listening on port 8180, and no error logs showing up in /var/log/tomcat55

It looks like the 'jsvc' process is running, but i dont know hwo to debug this problem with no logs/errors anywhere.  Any help on debugging why its not working would be great.  Thanks.

---

### Post by gtducati on 2007-11-09
Are you using Gutsy, Feisty ...?

---

### Post by gtducati on 2007-11-09
Have you done the following?

sudo apt-get install apache2
sudo apt-get install tomcat5.5 tomcat5.5-admin tomcat5.5-webapps
sudo apt-get install libapache2-mod-jk

The default port is set to 8180 ...

You can check to see if everything install correctly by opening your web browser to [http://localhost:8180/](http://localhost:8180/)

---

