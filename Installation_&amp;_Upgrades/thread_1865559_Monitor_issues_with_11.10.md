---
title: "Monitor issues with 11.10"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by louis.roux on 2011-10-20
I just upgraded to 11.10 and when I log in the computer freezes at the desktop and the whole left half of the screen has a white strip going down it.  At the top of the white part it says "Could not apply the stored configuration for monitors"  then it has a whole list from top to bottom of different tests it did.  for examle the first line says the following:

CRTC 434: trying mode 1280x1224@50Hz with output at 2560x1024@100Hz (pass 0)

and each line then has a slight change in it.

I am running a duel screen on my pc with a NVDA graphic card.  Never hasd this issue before.

---

### Post by dino99 on 2011-10-20
from a terminal:
sudo rm /etc/X11/xorg.conf
sudo apt-get purge nvidia-current
sudo apt-get purge nvidia-settings

sudo apt-get update
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings

sudo dpkg-reconfigure -phigh -a
(can take a while, patience)

then reboot and run nvidia-settings to set the dual screen as you need

or

boot in recovery mode (hold "shift" key down at bios end process to get the grub menu on single OS system) then select "repair packages"

---

### Post by louis.roux on 2011-10-20
It says it can't remove the /ext/X11/xorg.conf file cause it doesn't exist

---

### Post by Immolatus on 2011-10-20
> **louis.roux said:**
> It says it can't remove the /ext/X11/xorg.conf file cause it doesn't exist

Thats because there is no "ext" and xorg.conf is in xorg.conf.d

so: sudo  rm /etc/X11/xorg.conf.d/xorg.conf

---

### Post by louis.roux on 2011-10-20
Sorry my post was a misprint.  I did do etc not ext.  But I just tried it the way you said with the conf.d but it still says there is no such file or directory

---

### Post by ckazimie on 2011-10-20
I had a similar issue and what helped was deletion of ~/.config/monitors.xml

---

### Post by louis.roux on 2011-10-20
Ck thanks that did it

---

### Post by MAFoElffen on 2011-10-20
> **Immolatus said:**
> Thats because there is no "ext" and xorg.conf is in xorg.conf.d

so: sudo  rm /etc/X11/xorg.conf.d/xorg.conf
??? 

The current X.Org release is [X11R7.6]("http://www.x.org/wiki/Releases/7.6")... 

The default for the X configuration file is:  /etc/X11/xorg.conf unless X is user configured with a custom path to...

Now then-->  If he had Arch-Linux, it would be located in the directory you said: /etc/X11/xorg.conf.d/xorg.conf...

Ubuntu and others- There is no directory xorg.conf.d under /etc/X11/...

---

### Post by ORF1000 on 2011-10-23
> **ckazimie said:**
> I had a similar issue and what helped was deletion of ~/.config/monitors.xml
ckazimie's method worked great for me.  Very simple.

---

### Post by pedro1295 on 2012-06-08
[ckazimie]("http://ubuntuforums.org/member.php?u=1361821") thanks, removing of the xml file worked for me.  Cheers.

---

