---
title: "Acer Aspire 7720 update issue Gusty Gibbon"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by lazy gun on 2008-03-30
I had an interesting problem.  I was installing the latest release of Kubuntu Gusty (kubuntu-7.10-dvd-i386.iso obtained from [http://nginyang.uvt.nl/kubuntu/gutsy/](http://nginyang.uvt.nl/kubuntu/gutsy/)) onto a new Acer laptop (specs below). 
Windows Vista was already loaded onto one of the hard drives and so I wanted a dual boot with Gusty installed on the other drive. 

The install from the live DVD went perfectly. The only issue I had was no sound but wireless was up and running out of the box.  I used adept to run updates on the system after the fresh install. After the updates were installed I had a message stating that they could not be applied (sorry I can&#8217;t remember the exact text of the message). When I shutdown and rebooted the system sometime later I was presented with the grub 15 error. 

I used the live DVD to reinstall grub from the command line. Rebooted and still the same error. 
Since the install was fresh and I had nothing to loose I decided to re-install. Again everything was perfect and the system booted without any issues. After trying to apply updates again (security etc&#8230;) I had exactly the same problems and again the grub 15 error when trying to boot Kubuntu. 

Presently writing this from Vista.:(

I am thinking of waiting for the Hardy release before trying things again. I would be curious to know if something similar has happened to anyone else.  

LG

System Specs:
Acer Aspire 7720G-602G50MN Notebook
Intel® Core&#8482;2 Duo processor T7500 
2GB DDR II RAM (2x 1GB)
2x 250GB HDD 
Gigabit & Wireless LAN 802.11a/b/g/n, (Intel wireless chip)
Bluetooth
NVIDIA® GeForce® 8600M-GT 512MB

---

### Post by Pumalite on 2008-03-30
Check this:
[http://ubuntuforums.org/showthread.php?t=632151&page=3](http://ubuntuforums.org/showthread.php?t=632151&page=3)

From another thread:

 Re: freezes at boot
I have also an Acer Aspire 5520.

The SOLUTION is very simple:

- just add the option all_generic_ide to the grub boot option

We will never have that problem again.

---

### Post by lazy gun on 2008-03-31
Thanks for the quick reply!

I'll have a look, see what I can do and post the results. 

Best regards, 


LG

---

### Post by lazy gun on 2008-03-31
I played around with the grub, incuding the addition of the above, but to no avail. A little strange that even reinstalling grub made no difference and still provided me with an error 15.... file not found on trying to boot. I also tried booting with supergrub. That also failed when attempting an auto boot of kubuntu and a live boot. 

To try and resolve this reinstalled again but this time with ubuntu (not kubuntu). As before the install went fine straight of the live CD. After first boot I updated the system (no errors this time), booted again and....


:guitar:


I am writing this from ubuntu on the laptop. 

No problems yet. For those of you with this model that may wish to install ubuntu I can report that so far the only problem is no sound. Everything else seems to be functioning (wireless, bluetooth, Nvidia card etc) and importantly there are no issues with the system fan or power settings... I have none of the over heat issues reported in other posts. I will finish testing the system and post the results in the laptop testing pages ([https://wiki.ubuntu.com/LaptopTestingTeam/Acer](https://wiki.ubuntu.com/LaptopTestingTeam/Acer)).

Best regards, 

LG

---

