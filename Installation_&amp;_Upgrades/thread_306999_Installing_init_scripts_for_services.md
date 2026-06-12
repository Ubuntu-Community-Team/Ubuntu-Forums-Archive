---
title: "Installing init scripts for services"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by sscotti on 2006-11-25
Hi,

I just installed ubuntu 6.1 from the live CD.  I've been away from ubuntu for awhile, but I like it.

I did choose to install the LAMPP package from Apachefriends instead of using the server packages from Synaptic.  Everything is installed and running without too much trouble, although I'm having to start everything manually using launchers that I created for my desktop.

I also noticed the ubuntu is using a new scheme for managing inits and services.  How can I create a service that will start up when I boot the machine and that will start my LAMPP packages.  These are Apache, MySQL, PHP and an FTP server.  I also installed Apache Tomcat.  That has a launcher as well.  I also installed the Cisco VPN client.  This works fine, but I need to have the module load at boot time and I have to use the launcher to open in terminal so I can type in my informaiton.  It works as well.

I was using Webmin to manage the OS, but it seems to have crapped out when I installed 6.10.  The runlevel for the boot module is stuck at 0 and I can't change it.  Likewise for most of the other settings.  I can't seem to edit the settings in Webmin.

Any pointers to a service or init manager that I could use would be helpful.

I've posted a few other posts about other issues that I'm having.  Not sure if they are bugs or configuration problems.

---

