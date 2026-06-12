---
title: "Web server postfix setup to send to MX server"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by digitalquill on 2010-09-29
Hi All
 
I have searched for a solution to this for ages now but getting no-where so wonder if anyone can help
 
I have two different servers setup, one running my mail and one running my webservers.
 
All my domains point their A record to the web server and their MX record to the mail server
 
This works perfectly until I setup postfix on the webserver to send emails via PHP whcih for any local domain are delivered locally.
 
If I have PHP (or send mail from the command line) send to gmail for example that mail is sent out and delivered, but for any domain hosted on the web server emails are delivered locally and not sent to the MX server.
 
How do I stop postfix keeping its mail for local domains and send them to the MX server? or even better to actually lookup the MX record and follow that for the mail?
 
I am running Ubuntu 10.04 on both web and mail servers
 
Thanks for any help
 
Matt Houldsworth

---

