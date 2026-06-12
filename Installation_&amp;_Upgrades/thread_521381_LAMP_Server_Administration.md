---
title: "LAMP Server Administration"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by scantoria on 2007-08-09
I am new in the Linux world and not intimidated of the command line. I do not know a lot of the commands and I have just installed the Ubuntu 6.2 LAMP Server.

After the installation, the system booted into the command line. I tested the username and password I keyed-in during the installation to see if I can login and it worked. Questions below should help me get this server in production.

Questions:
1) I do not remember entering a password for root so I am not sure how I would make any changes. Will I be able to configure the server with my login?

2) How do I manage the ftp users that will need to access the website or websites? I am assuming this is just a simple process of creating a group and assigning this group to the website folder. I have created a user and a group using the GUI in linux before but never done it from the command line.

Any help is much appreciated.

Thank you,

Steve

---

### Post by mizar001 on 2007-08-09
1) root user is disabled by default, but anyway you can perform superuser tasks with 
'sudo'. Ex : sudo vim /etc/hosts  (open the hosts file in read write mode even if you don't have permissions in /etc folder)

2) afaik ubuntu lamp server does not comes with an ftp installed. It's up to you to decide what type of ftp server to install. I recommend you vsftpd because it's simple to configure and really powerful. Perhaps you should study some general documentation first.

---

