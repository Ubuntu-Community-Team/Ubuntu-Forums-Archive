---
title: "Installing Gutsy Gibbon but keyboard unrecognised"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by pritcharded on 2008-02-01
I successfully loaded Xubuntu (Gutsy Gibbon) on an old recycled Pentium II PC of mine. Using the same CD (.iso file) I tried to do the same on a friend's Celeron PC. I opted to wipe the lot and instal Xubuntu on the whole HDD. 

For some reason something seemed to go askew as the install was just finishing (it was showing 100%) and it froze. The only way we could proceed was to cut the power, never a good idea and it seems to me that the bios may have become corrupted. Previously the HDD had Windows XP installed and two partitions. 

When I try to reboot (from the HDD or the CD) it loads up OK, but the key board isn't recognised (hence I can't get past the password screen when booting off the HDD). When booted from the CD I get to the desktop but if I try to use the wordprocessor, the keyboard is unrecognised.

I've tried the safe screen mode without success.

This is my first experience with Linux (in any of its distributions).

Is there some way to reinstall a clean copy or is there some other way to fix this?

Thanks for your help.

Ted

---

### Post by Julita on 2008-02-01
What type of keyboard do you have?

---

### Post by Julita on 2008-02-01
I have found this thread: [http://ubuntuforums.org/showthread.php?t=186689](http://ubuntuforums.org/showthread.php?t=186689) It might help you.

---

### Post by pritcharded on 2008-02-01
Julita

The keyboard is of the old multipin variety (ie: not USB). I looked thru the links you suggested, entered the BIOS and disabled "USB keyboard" as someone else found change that helpful. Unfortunately it made no difference. I couldn't see anything else that related to keyboards in the BIOS.

Thanks anyway, Ted

---

### Post by erginemr on 2008-02-01
The second explanation would be that maybe your keyboards is dead. Does the lights on the keyboard light on and off during the boot? And doesn't the BIOS protest during the boot with and F1: keyboard error? 

And also make sure that all the pins on the PS2 plug of the keyboard are straight and it is plugged in firmly...

---

### Post by pritcharded on 2008-02-01
Some progress has been made. The multipin keyboard is OK - it won't work in the Xunbuntu environment but it's fime while operating the BIOS or another PC. However I tried an USB keyboard and that works fine so I've been able to reinstall Gutsy Gibbon off the .iso file I downloaded onto a CD.

Xubuntu seems to work this time except I can't get Firefox to access the internet.
The PC has an ethernet connection to an ADSL/router and the network icon tells me a I have a high speed connection. I can get an internet connection on my newer PC coming off the same router.
While it's not obvious from the documentation all this suggests that Firefox may not correctly configured.

Any suggestions?

Ted

---

### Post by Julita on 2008-02-02
Ted, regarding your Internet connection... Have you tried another browsers? Opera, for example? It can be installed form the repositories...
I have also ADSL, and the configuration in Ubuntu in your case is made automatically, so there should not be any problems. However, I have another question - do you have dynamic or static IP address?

---

### Post by pritcharded on 2008-02-03
Update:
I've downloaded the "alternate" .iso file, confirmed its accuracy with MD5SUM, and checked the disc after burning.
This time Xubuntu loaded OK and the keyboard works OK, but even though the network icon says I have a ethernet connection with the router, Firefox will not connect to the internet.
The settings within Firefox are the same as on my other computer (connected to the same router) and that works perfectly. The settings also align with those indicated in the Ubuntu documentation.
Julita, re your questions, I haven't been able to download Opera.
I selected Add/Remove Applications and got a message saying updating required (or similar). I selected that and got a box titled "Download Package Info" and at last count 13 or 33 files had been downloaded. Selecting the option "show Progress of single files" all but one downloaded shows as failed. 
The only one that downloaded successfully was:
cdrom://Xubuntu7.10_Gutsy Gibbon_-Release i386 (20071016) Gutsy Release

Most of those that failed have the word "security" in them such as:
[http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security release

This suggest to me that I'm reaching the internet OK but a security system somewhere is locking me out.
Any suggestions?

Ted

---

### Post by Julita on 2008-02-03
You may go to the Synaptic and to the "Repositories" option in order to check the server you have downloaded from, and you can change it.

---

