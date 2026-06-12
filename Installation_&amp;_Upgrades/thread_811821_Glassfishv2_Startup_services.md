---
title: "Glassfishv2 Startup services"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by joeinazusa on 2008-05-29
I would love to just be able to setup Glassfish server by installing Hardy 8.04LTS and installing glassfish via apt-get.

My Procedure:

apt-get install sun-java6-jdk glassfishV2
(Accept all dependencies)

Voila all is good and it is running... Ok.. Now I reboot.. 
No service running.  I can't find the startup script in /etc/init.d/ (Or not looking hard enough) and if I do asadmin start-domain it goes through the process of creating domain1 which was already created via install.

I don't know if I am supposed to run a specific script for Ubuntu, run it as a different user, or set different environment variables.  

I can install Glassfishv2 via standard install (download and creating the scripts myself) and all it good, but I have yet to configure the repository version.

Also this is a clean install.. and it is for live deployment, not development, I use netbeans 6.1 and it works great, but this server will only be a J2EE server.

:confused:
Any help would be appreciated!

Jose

---

