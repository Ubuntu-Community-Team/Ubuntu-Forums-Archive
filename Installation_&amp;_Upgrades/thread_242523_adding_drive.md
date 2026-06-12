---
title: "adding drive"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by SpikeyMike on 2006-08-23
Hi all

I have a dual boot system with windows XP and Ubuntu dapper drake. It works fine but I want to add an extra hard drive, when I connect it my system will no longer boot, it just gets to the point where grub loads then stops.  I tried booting using the live cd to edit grub but I can't seem to get to edit the file.  I have tried the following commands from a terminal window:

sudo gedit /etc/grub.config
sudo gedit /boot/grub.config

but I get the following message followed by an empty pop up window:

gedit: 7741): GnomeUI -  WARNING **: While connecting to session manager:Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

a friend advised me to use the pico editor but I just get an empty window, any advice greatly appreciated

Mikey

---

### Post by TLE on 2006-08-23
I'm not excactly sure if that's what you're asking for. But the configuration file for GRUB is in this location
/boot/grub/menu.lst

---

### Post by SpikeyMike on 2006-08-23
Hi TLE

yup sorry wasn't very clear about what I wanted, I now have 2 sata hard drives, one with winxp and the other with ubuntu, I added an extra IDE hard drive but my system wouldn't boot, I need to know how I can boot my system with this hard drive installed and then how I can get to the grub configuration file and how I need to edit it to allow my system to boot, I presume adding the extra drive has changed the drive letters so thats why I can't boot the system but I don't know what exactly I need to change to correct this.

Mikey

---

### Post by TLE on 2006-08-23
Ok first of all. If you do not reach grub at all when you try to boot, so that the only thing that happens at boot-time is that you get an error saying that it can't find any system to start up. Is that what happens ?

---

### Post by SpikeyMike on 2006-08-24
Hi again, what happens is that grub starts to load then gives an error as follows:

GRUB Loading stage1.5.
 
GRUB loading, please wait...
Error 17

and then it stops, if I shutdown and disconnect the IDE hard drive grub boots normally to the menu and I can select linux or xp

Mikey

---

