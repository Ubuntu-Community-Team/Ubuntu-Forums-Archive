---
title: "GRUB edit and Sound card not detected"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by kngsze on 2010-08-06
Hi all
 

 I'm a Linux noob, so please go easy on me!  I've been desperate to get rid of my Windows install for a while now and have finally started to make the move over, but have a problem with my Ubuntu 10.04 install.  I've scoured the help documentation and forum for days now without managing to resolve my problem, and have finally resorted to posting my problem. So I'm sorry if this has been covered elsewhere.
 

 1\  Installed Ubuntu on my laptop (Viglen Furtura S200) but the only way I have been able to get it to install and boot properly is edit the GRUB with the following  “acpi=off i915.modeset xforcevesa”.   I had to add these parameters even to boot the live CD as well.  I think I'm right in assuming that this is forcing the use of a generic graphics driver, consequently leaving some visual features unavailable. I'm not really sure what turning acpi off is  doing.  Is it possible to resolve this?  Is this the cause of problem number 2?
 

 2\  After install there is no sound.  Sound preferences shows no hardware and ALSAmixer is empty when opened. I have followed the sound troubleshooting through and it looks like my sound card is actually being picked up on the board, but I fall at the point of checking the loaded ALSA Modules as my report shows that none are loaded?!  Here is the link to my ALSA info:
 

 [http://www.alsa-project.org/db/?f=288d96544a8b1fc15a2f8ec7e29ab37434f51af6](http://www.alsa-project.org/db/?f=288d96544a8b1fc15a2f8ec7e29ab37434f51af6) 
 

 You'll notice that “Loaded ALSA modules” is empty as is “Sound cards recognised by ALSA”.
 

 Running lspci -v | less   reports that Ubuntu can actualy see my sound card, listed as   
 

 “5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)”
 

 I'm fairly sure I've read the ALSA wiki right and that my card is supported.  
 

 Thanks in advance for any advice

---

### Post by lechien73 on 2010-08-06
Welcome to Ubuntu, first of all...don't worry, everyone's fairly easy going round here - and your question gives plenty of detail, which is what we all like :)

I've had ALSA problems before, and usually rebuilding from source fixes the problem.

There's a great thread on the forums here: [http://uri.tl/w](http://uri.tl/w)

I thought that switching acpi off was purely to do with power - such as allowing the operating system to actually switch the machine off, or providing Wake-On-LAN services. I could be wrong on that, though!

---

### Post by dandnsmith on 2010-08-06
You're right about acpi - see:
[wiki info](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)
[industry definition](http://www.acpi.info/)

---

### Post by kngsze on 2010-08-06
Thanks for the quick reply.  Good to know about the acpi - that explains why on shutdown the OS dismounts but doesn't actually power off the laptop!  Not a major issue at all though.

Tried the [http://uri.tl/w](http://uri.tl/w) upgrade the latest alsa but unfortunately still the same - no sound cards detected by alsa   $ aplay -l  "no cards detected by alsa"  ;(

---

### Post by lechien73 on 2010-08-07
Ok, maybe it's that alsa is not detecting the card properly, then.

Could you try the following:

```
gksu gedit /etc/modprobe.d/alsa.base.conf
```

Add the following line to the end:

```
options snd-hda-intel probe_mask=1 model=auto
```

If any other lines begin with "options snd-hda-intel", then put a # sign before them to comment them out.

Save the file and reboot your computer.

---

### Post by kngsze on 2010-08-10
Thanks.  I've tried that but with no success.  My conf file was actually blank/empy - I'm assuming it shouldn't be.  Added the line in anyway, rebooted and still no sound.

---

