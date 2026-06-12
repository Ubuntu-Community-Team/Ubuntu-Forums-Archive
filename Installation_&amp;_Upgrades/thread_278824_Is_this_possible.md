---
title: "Is this possible?"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by remle on 2006-10-16
I have installed, and is using dapper along with windows xp in a multi-boot pc. 
I have a project that requires me to have a linux (ubuntu, if possible) server with apache and maybe some ftp server installed. Would it be possible for me to use my current dapper installation and install apache in it without affecting the settings of my original/frequently used installation? Or would it be better if i setup a new partition for the use of the apache server? 

Is it possible for me to install apache, and just add a line in grub menu that will start ubuntu with only the apache server and needed apps running?

---

### Post by ScrewItFix on 2006-10-17
Hi, 
Apache(with PhP) and MySql run in the background. Your system will not be affected "visually" - jet you can loose some performance while this Server are running. I sell CMS-Websites and I use a LAMP-Server on my Notebook to show our CMS-System live. I never feel any difference in the performance of my Notebook. Anyhow, you can configure them not to start on boot and start them manual (like /etc/init.d/apache2 start).

A "LAMP"(LinuxApacheMysqlPhp) HowTo you will find [here ]("http://ubuntuguide.org/wiki/Dapper#Ubuntu_LAMP_.28Linux.22CApache.22CMysql.22CPHP.29_Server")

If you don't need to carry around the LAMP-Server (like me) you can also use an old computer as server in your network. I have an P3 700mhz with 256MB and 10GB disk running a LAMP server, using Ubuntu-Server-Edition. So you can use your Windows also with this Server. 

cu Screw It Fix

---

### Post by remle on 2006-10-18
> **ScrewItFix said:**
> Hi, 
Apache(with PhP) and MySql run in the background. Your system will not be affected "visually" - jet you can loose some performance while this Server are running. I sell CMS-Websites and I use a LAMP-Server on my Notebook to show our CMS-System live. I never feel any difference in the performance of my Notebook. Anyhow, you can configure them not to start on boot and start them manual (like /etc/init.d/apache2 start).

A "LAMP"(LinuxApacheMysqlPhp) HowTo you will find [here ]("http://ubuntuguide.org/wiki/Dapper#Ubuntu_LAMP_.28Linux.22CApache.22CMysql.22CPHP.29_Server")

If you don't need to carry around the LAMP-Server (like me) you can also use an old computer as server in your network. I have an P3 700mhz with 256MB and 10GB disk running a LAMP server, using Ubuntu-Server-Edition. So you can use your Windows also with this Server. 

cu Screw It Fix


Hi! Thanks for the quick response, i read the LAMP HowTo, and it states that LAMP is automatically installed with the Server Edition/ Server Install. What i really want to know is, if it is possible for me to install LAMP Server with my current ubuntu install(not Server Edition), and if it is also possible for me to create a new user, where, when this user logs on will automatically start the LAMP server. 
I don't need a dedicated server as this is only for testing purposes, to let me test how my project website would behave if i were to access it using different computers (pc, mac, etc. using different OS, and assorted browsers).
Thanks in advance for any positive response. :)

---

