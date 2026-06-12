---
title: "I have just about freakin' had it!"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by twoseids on 2006-07-06
After countless failures at installing Dapper through the Live CD, and several failures at installing the alternate installation, I finally got it installed (the alternate, that is). Couldn't mount /windows during the install, but I can deal with that later.

Anyway, my X server seems incapable of getting up and running. I've tried countless fixes mentioned in the forums, most of which include **dpkg-reconfigure xserver-xorg** blah blah blah. I can't even list specifics, I've tried so much. But still no dice.

If someone out there is knowledgeable and willing to walk me through it, I can give you a call. I suppose a last resort is to install Breezy and hope that 1) it works and 2) upgrading to Dapper would work. But that's a last resort.

Help!

---

### Post by bobby19 on 2006-07-06
Are you sure you have selected don't autodetect my chipset and then selecting  VESA in the list in the sudo dpkg-reconfigure xserver-xorg tool. Because if you did then I don't know what the problem would be. You could maybey try fresh installing dapper again.

---

### Post by woedend on 2006-07-06
what is your video card, post your /etc/X11/xorg.conf contents, and what is the error message?

---

### Post by twoseids on 2006-07-06
VESA is never an option; I only have neomagic, siliconmotion and voodoo. I also have nvidia now, after installing an nvidia driver.

I have the Nvidia GeForce Go 6600. The pertinent (I think) section in xorg.conf says:

Identifier: "Intel Corporation Mobile Integrated Graphics Controller"
Driver: "neomagic"
Bus ID: "PCI:0:2:0"

**EDIT:** I changed the Driver to read "nvidia" but still no dice.

---

### Post by woedend on 2006-07-06
have you tried driver to user driver
"nv"
?

what is your error message?  it should point you to a log file...post it?

---

### Post by twoseids on 2006-07-06
[QUOTE=woedend]have you tried driver to user driver
"nv"
?

what is your error message?  it should point you to a log file...post it?[/QUOTE]
Okay, I tried changing it to "nv" but same problem.

Regarding the log file, it says:

Log file: "/var/log/Xorg.0.log"

Does that help?

**EDIT:** Opening up that file with vi, I see it's quite big - and I can't copy and paste since it's on another computer. What in that file should I be looking for?

---

### Post by confused57 on 2006-07-06
Maybe this thread could help:
[http://www.ubuntuforums.org/showthread.php?t=33142&highlight=onboard+graphics+nvidia](http://www.ubuntuforums.org/showthread.php?t=33142&highlight=onboard+graphics+nvidia)

Probably not, but possibly worth a read...

---

### Post by woedend on 2006-07-06
any lines starting with I believe its (EE)
also, the last few lines, as it will probaly tell you the error towards the end of the log.

---

### Post by alynx on 2006-07-06
Dont know if im right on target here , but i had a simmilar problem. I use nvidia 6600GT and Ubuntu always starts of with the nv driver in /etc/X11/xorg.conf when i reinstall my computer . My X is then scrambled with colors looking like a tv test signal. ctrl+alt+f1 then. then I do the sudo apt-get install nvidia-glx and change the /etc/X11/xorg.conf to read nvidia instead of nv. Then i go back to my scrambled x by alt+f7 and restart it with ctrl+alt+backspace. And there it is , the lovely nvidia logo , and then my X looks normal again=D> Maye you have allready tried this , but it helps for me anyways. Hope it works out for you 
Cheers

---

### Post by alynx on 2006-07-07
Yesterday i installed debian 3.1 r2 on my computer at home. GFORCE 6600 GT , and i had to use VESA driver to actually get the X to start.

---

### Post by twoseids on 2006-07-08
Well, I finally tried again yesterday with a fresh install of the Desktop version, and for some reason it worked. I got this one from a torrent, and burned it from a different computer, so maybe I just got lucky.

Thanks to those of you who tried to help me figure out what was wrong!

---

