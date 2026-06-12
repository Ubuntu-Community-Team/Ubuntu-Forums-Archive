---
title: "Does this noob have unfounded fears?"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by Sagotis on 2006-06-23
Hi All!

I feel that I may have done something wrong with my ubuntu install by the way I installed the 686 linux image/kernel.

Here is what I did:

First I did a sever install. Then I did an apt-get dist-upgrade and then did apt-get installl linux-image-2.6.15-23-16 and apt-get install linux-headers-2.6.15-25-686.

I rebooted the system into the new 686 kernel and then proceeded to uninstall the 386 kernel with: apt-get remove linux-image-2.6.15-25-386 and the 386 headers as well. However, after removing the 386 headers and kernal I got an error message about sys link was broke and that lilo was messed up. Yet when I rebooted everything seemed fine and I did an apt-get install ubuntu-desktop.

After the desktop was installed I issued the startx command and was able to get into Gnome ok. However, while in the desktop environment I never got a message from the update manager that there were updates for my system. This was different from the straight foward install of the live cd, which after one is done (with this type of install) the update manager will state that there is over 70 new updates.

In light of this I must ask the question did I do something that may have broken the update manager (or anything else in my system)?

Everything seems to funtion fine, but it should be noted that when I used Alberto Milone's Nvidia script ([http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)) it was not able to restart the x-server so I just rebooted; and after the reboot I was able to get back into Gnome and all seemed fine. Another thing to note is that nautilus scripts that Automatix ([http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)) installs never shows up when I right click in Gnome.

These two things also make me worry that I may have messed up my linux install.

So does this linux noob have unfounded fears? Did I borke my system by the way that installed the 686 image/kernel to the point that I can not get updates? Also should I be worried about the sys link and lilo errors that I had after I unstalled both the 386 headers and kernel?

Sagotis

---

### Post by arnieboy on 2006-06-23
[QUOTE=Sagotis]Another thing to note is that nautilus scripts that Automatix ([http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)) installs never shows up when I right click in Gnome.[/QUOTE]
you need to right click inside the nautilus file browser.

---

### Post by mscman on 2006-06-23
Can you run update manager manually?  Either from the menu at the top or by pressing Alt+F2 and running update-manager?

---

### Post by Sagotis on 2006-06-23
[QUOTE=arnieboy]you need to right click inside the nautilus file browser.[/QUOTE]

arnieboy, I have tried that still does not work. It shoudl be noted that I could also right click on the desktop and be able to access the nautilus script menu; that is after a Ubuntu Live cd install and the nautilus scripts that Automatix installs.

---

### Post by Sagotis on 2006-06-23
[QUOTE=mscman]Can you run update manager manually?  Either from the menu at the top or by pressing Alt+F2 and running update-manager?[/QUOTE]

I have ran the update manager manually from the system admin menu and no updates are shown - even after I click on check. I find that very strange and I am worried :-k :-k

---

### Post by mscman on 2006-06-23
It sounds like your system is just up-to-date, probably from the server install (usually installations try to install security updates while it's still in the install process to prevent you from having to install them afterwards).  I would wait a few days until another round of security updates comes through and then try updating again.

Another way you could check to make sure everything is working right is simply making sure apt is working right.  Install a small package like ethereal and then remove it afterwards.  Also make sure that apt-get update works fine and returns no errors.

I wouldn't be too worried if I were you.

---

### Post by tseliot on 2006-06-23
[QUOTE=Sagotis]Everything seems to funtion fine, but it should be noted that when I used Alberto Milone's Nvidia script ([http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)) it was not able to restart the x-server so I just rebooted; and after the reboot I was able to get back into Gnome and all seemed fine.[/QUOTE]
Weird... I have never tried my script on a server installation.


BTW why did you do a server install?

---

### Post by Sagotis on 2006-06-23
[QUOTE=mscman]It sounds like your system is just up-to-date, probably from the server install (usually installations try to install security updates while it's still in the install process to prevent you from having to install them afterwards).  I would wait a few days until another round of security updates comes through and then try updating again.

Another way you could check to make sure everything is working right is simply making sure apt is working right.  Install a small package like ethereal and then remove it afterwards.  Also make sure that apt-get update works fine and returns no errors.

I wouldn't be too worried if I were you.[/QUOTE]


mscman

I did as you suggest, installing ethereal via apt, which installs ethereal-common 0.99.0-1ubuntu1 (7.3mb). No errors. I also did as you suggested, removing ethereal via apt, and again no errors. And doing an apt-get update shows no errors as well.

However, if one were to use the live cd as the base of one's experience there is an inconsistency between what was known with the live cd install vs server install. The biggest is that after a live cd install the updates that offered are mostly Gnome updates (over 70 of them).

Yet after a server install and then an apt-get install unbuntu-desktop, and then booting into the Gnome desktop, the update manager has no updates? This is strange and inconsistent from what I have known and expect from previous unbuntu installs. Which may very well point to the fact that I am still a nub :) 

Though, the true test will be when the new round of security updates comes through as you suggested.

Thank you,

Sagotis

---

### Post by Sagotis on 2006-06-23
[QUOTE=tseliot]Weird... I have never tried my script on a server installation.


BTW why did you do a server install?[/QUOTE]

To have the cleanest environment to do a new linux kernel install - also the fact that your (killer, very killer) script adds modules to the kernel.

Im a sucker for the clean room environment for testing 8) 

Sagotis

---

### Post by tseliot on 2006-06-23
[QUOTE=Sagotis]To have the cleanest environment to do a new linux kernel install - also the fact that your (killer, very killer) script adds modules to the kernel.[/QUOTE]

Killer? What do you mean? Dangerous perhaps?

And of course using a driver involves using a kernel module. Is that a problem?

---

### Post by Sagotis on 2006-06-23
[QUOTE=tseliot]Killer? What do you mean? Dangerous perhaps?

And of course using a driver involves using a kernel module. Is that a problem?[/QUOTE]

When I say killer - I do not mean dangerous! Killer is slang (at least in the states ) for good or cool.

---

### Post by tseliot on 2006-06-23
[QUOTE=Sagotis]When I say killer - I do not mean dangerous! Killer is slang (at least in the states ) for good or cool.[/QUOTE]
I didn't know (I'm Italian). Thanks I have learnt a new word ;)

---

### Post by Sagotis on 2006-06-23
[QUOTE=tseliot]I didn't know (I'm Italian). Thanks I have learnt a new word ;)[/QUOTE]


No thank you for one killer script! :D

---

### Post by mscman on 2006-06-24
[QUOTE=Sagotis]mscman
Yet after a server install and then an apt-get install unbuntu-desktop, and then booting into the Gnome desktop, the update manager has no updates? This is strange and inconsistent from what I have known and expect from previous unbuntu installs. Which may very well point to the fact that I am still a nub :) 
[/QUOTE]
Ahh, ok I see the "problem". When you do a full install from CD, you're getting older packages, since it reads them from the CD.  That's why you're not getting any Gnome updates; you already have them.  Apt repositories (should) have the up-to-date packages, and those are what are considered updates.  When you install ubuntu-desktop via apt, you're getting the updates essentially.

It sounds to me like everything's working fine though.  Have fun!

---

### Post by Sagotis on 2006-06-25
[QUOTE=mscman] When you install ubuntu-desktop via apt, you're getting the updates essentially. [/QUOTE]

I never knew that (because it requires the cd to install the desktop) :eek: However, I do remember that there were around 40 files that it did get from the apt repositories.

Again thank you mscman, for you have shown that indeed this linux noob did have unfouned fears ;)

Sagotis

---

