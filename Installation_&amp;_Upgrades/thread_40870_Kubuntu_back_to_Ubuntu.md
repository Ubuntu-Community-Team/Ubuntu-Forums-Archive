---
title: "Kubuntu back to Ubuntu"
date: 2005-06-10
forum: Installation &amp; Upgrades
---

### Post by Uta on 2005-06-10
I installed Kubuntu as stand alone OS on a Dell C800 laptop. I like Kubuntu but after 3 days of struggling and failing to get printing from my print server I want to go back to Ubuntu which has a more funtional printer (setup) manager. What do I do? Do I merely boot from the Ubuntu install disc, reformat the hard drive and install a new system? If that is possible, since I am only running Linux how do I get it to boot from the CD? I went into the Dell bios and it is set to look at the CD drive first but when I tried it with a Ubuntu Live CD it completely ignored it and booted into the KDE desktop? Thanks in advance!

---

### Post by Xian on 2005-06-10
I would imagine you could just install Ubuntu from your present system and then after you get that running it would be no problem to remove the Kubuntu packages. 

This is the command to install Ubuntu on apt:
```
$ sudo apt-get install ubuntu-desktop
```


If you have the Hoary CD you should be able to install it from that:

insert Ubuntu 5.04 CD
Ubuntu CD detected choose Cancel
sudo apt-cdrom add
Ubuntu CD detected choose Cancel
sudo apt-get install ubuntu-desktop
logout | end session

---

### Post by Uta on 2005-06-10
Thank you for your quick response...the situation has changed a bit. the reason I wanted to install Ubuntu was because of printing issues. I did manage to boot from the LIVE Ubuntu CD and ran into the same printing issues, which is strange because when I boot the Ubuntu PPC version on my iBook laptop I have no printing issue but booted on a Dell laptop it can't connect to the print server? Could it be permission issues? When I localhost:631 it refuses the connection... tho the printer is set to my print server 192.168.0.100 it says the server is busy, within the LIVE CD and from within the KDE environment it simply can not connect? Any ideas? Thanks!

---

