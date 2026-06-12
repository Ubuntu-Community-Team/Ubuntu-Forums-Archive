---
title: "Upgrade crashed on pcmcia"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by zeppelin06 on 2006-06-01
Upgrading through sudo package-manager -d worked great unitl it got to the configuring of pcmcia.  It stalled and I noticed that the lightbulb in the corner said to reboot so I did.  Now ubuntu crashes on startup on starting PCMCIA services.  I can not find out how to get to a login screen and do not know what to do there once I do.  

Note that it is a desktop so I do not even need the PCMCIA service to be activiated.   Thanks in advance

---

### Post by bluevoodoo1 on 2006-06-01
See this... [http://ubuntuforums.org/showpost.php?p=1073476&postcount=2](http://ubuntuforums.org/showpost.php?p=1073476&postcount=2)

A temporary solution *should* be to press Ctrl+C to skip that process at bootup.

---

### Post by zeppelin06 on 2006-06-01
unfortunately that did not work
it does not say fail at starting pcmcia services it just stops
the code before it is...

/etc/rcS.d/S40ifrename: lline 12: /sbin/ifrename: No such file or directory
*Configuring network interfaces...  [OK]
*Starting PCMCIA services...             then it stops and stalls at this point

---

### Post by bluevoodoo1 on 2006-06-01
[QUOTE=zeppelin06]unfortunately that did not work
it does not say fail at starting pcmcia services it just stops
the code before it is...

/etc/rcS.d/S40ifrename: lline 12: /sbin/ifrename: No such file or directory
*Configuring network interfaces...  [OK]
*Starting PCMCIA services...             then it stops and stalls at this point[/QUOTE]

Did you read the link? You should be able to turn off PCMCIA services with it at bootup.

This guide is what the link above points to... [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by zeppelin06 on 2006-06-01
I did read it but my problem is that I can not get to a command line to do the first step in the post you linked.  Sorry for any confusion.

---

### Post by zeppelin06 on 2006-06-01
I figured out what was wrong.  Basically it ubuntu crashed half way through installing dapper.  This made booting impossible.  For anyone else who has this problem these are the steps I used to fix it.

1) when restarting you have 3 seconds to het escape while grub is booting
2) then I got a list of the different kernals 
3) I booted off of a old kernal and got into GDM
4) press control+alt+F1 to leave the gui and login
5) then run 
sudo apt-get -f install
sudo dpkg --configure -a 

this will redownload dapper
thanks to bluevoodoo1 for getting me to think about this problem before panicing

---

