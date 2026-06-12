---
title: "Upgrade to Gutsy Gibbon gone wrong"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by MMoudry on 2007-10-18
Hi,
I have upgraded a 7.04 Feisty Server installation to 7.10 Server today. The upgrade didn't show any errors except for tomcat packages. However when I tried to restart here what I got :

[IMG]http://www.roleplayer-legacy.org/IMG_2391_resized.JPG[/IMG]

My hardware :
AMD X2 4400
ASUS M2N32 WS PRO
ADAPTEC SATA RAID
4GB ram
TV tuner card

Does anybody else have similar problem? I manaed to boot the old kernel and hence I am able to write this message (the server is my router). Guess this will tech me not to upgrade a system that works.....

MM

---

### Post by mattpker on 2007-10-18
You could try backing up and uninstalling tomcat and then redo the upgrade and see if that works.  But those errors don't look like they have much to do with tomcat, your even getting a usb drive error. Let me know if you figure it out.

---

### Post by MMoudry on 2007-10-19
Well I know that this error is not linked to tomcat. It seems like that the kernel configuration failed and it is passing wrong parameters to modules or some modules are corrupted......

---

### Post by MMoudry on 2007-10-19
gah too bad... I am going to backup everything and head for a clean reinstall from Gutsy CD....

This sucks, it took me 3 months of work to get the server configured the way I wanted it to ](*,)

Gues this will teach me never to upgrade when everything runs.... arrrrgh

---

