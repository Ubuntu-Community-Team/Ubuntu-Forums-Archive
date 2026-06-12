---
title: "Tomcat 5 init.d"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by torbennorling on 2006-10-24
Hi,
I just begun using Ubuntu and I have installed the latest 6.10 RC and now I'm about to get my working Tomcat 5.5.20 installation to autostart during system boot.

Tomcat already have suitable scripts for starting / stopping Tomcat located at following path (on my system):
[COLOR="Blue"]/usr/lib/apache-tomcat/bin/startup.sh[/COLOR]
[COLOR="Blue"]/usr/lib/apache-tomcat/bin/shutdown.sh[/COLOR]

Also, I don't want root to execute these scripts for security reasons. I have a dedicated [COLOR="Navy"]tomcat [/COLOR]user for this with "Tomcat-stuff-only-access". I realize this should be done using init.d but as I'm kind of a newbie in the Ubuntu / Debian area I would like some tips how to create this script correct to make sure the tomcat user is executing the scripts and also I would like (if possible) the Tomcat process to start before Apache due to that I use the jk module to connect Apache to Tomcat.

// Torben

---

