---
title: "Problem with Ubuntu 8.04 Live CD/Upgrading to 7.10"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by Sniget on 2008-05-04
I am currently Using a Averatec 3200 Series Laptop that has Ubuntu 7.04 (fully updated) on it and would like to upgrade to 8.04 LTS, but when I both upgrade 7.04 to 7.10 or use the 8.04 Live CD my computer will boot into the command line once I get onto the actual OS (rebooting (update) or proceeding to the Live Session/install (Live CD)).  I have no idea how I should fix this, please help.

-Snigs

---

### Post by bdwill on 2008-06-13
Experiencing the same problem here. Any help is appreciated!

---

### Post by GeryonD on 2008-06-16
I have the EXACT same problem.  I am still trying to troubleshoot this and it appears to be a problem with X detecting the LCD display properly.  Every mode it tries it fails with an error saying that the display doesn't support that mode.  I have to fiddle with it some more but it may have something to do with DDC.  Perhaps disabling or enabling this might have some kind of effect.  I don't have the laptop handy to try this but I'll give it a shot next time.

---

### Post by GeryonD on 2008-06-17
Okay, so I investigated this further and it's definitely a problem with DDC.  DDC detects what monitor you have and what modes it supports.  Unfortunately the default driver "openchrome" can not read the DDC values from the LCD.  I tried this with the VESA driver and got the exact same results.

The problem is X can't figure out what mode is safe for the monitor.  It tries different modes but finds none so it fails to load leaving you at a console.  

If you look in '/var/log/X.log.0' you will see the error.  I tried disablings DDC with 'Option "NoDDC"' to no avail.  I also manually entered in all the monitor settings with no luck either.  The latest version of X relies heavily on DDC.

So I think the real question is why isn't the DDC module in X reading our LCDs values properly?

I'll keep hacking away at this and leave my results on here.

---

### Post by Pumalite on 2008-06-17
What Monitor do you have?

---

### Post by GeryonD on 2008-06-18
We all have Averatec 3200-based laptops which have standard, 12.1" XGA LCD displays, 1024x768 max resolution at 60Hz.

I did discover that the 'vga' driver will start X up, but it's pretty much unusable.  My next shot is getting Ubuntu installed via the text-based installer so I can stop running off the CD, bringing up networking and mounting my drives every time I reboot.  This will also allow me to experiment with an updated version of Xorg.

I was also troubleshooting my desktop, which I decided to reinstall as well at the same time.  It too had problems with my ATI card in X.  I grabbed some recent updated, restarted the computer and X came up beautiful with full 3D acceleration.  So I can now FINALLY browse again with a graphical browser, no more w3m :)  yay

---

### Post by omega13a on 2008-06-22
> **GeryonD said:**
> Okay, so I investigated this further and it's definitely a problem with DDC.  DDC detects what monitor you have and what modes it supports.  Unfortunately the default driver "openchrome" can not read the DDC values from the LCD.  I tried this with the VESA driver and got the exact same results.

The problem is X can't figure out what mode is safe for the monitor.  It tries different modes but finds none so it fails to load leaving you at a console.  

If you look in '/var/log/X.log.0' you will see the error.  I tried disablings DDC with 'Option "NoDDC"' to no avail.  I also manually entered in all the monitor settings with no luck either.  The latest version of X relies heavily on DDC.

So I think the real question is why isn't the DDC module in X reading our LCDs values properly?

I'll keep hacking away at this and leave my results on here.

This problem doesn't seem to be with LCDs. I'm having the same problem with the old fashion bulky monitors (whatever they are called). Its so annoying. My hard drive failed unexpectedly and I can't reinstall Ubuntu on a new hard drive because of this problem... :mad:

---

### Post by GeryonD on 2008-07-03
I am giving up on installing Ubuntu on this laptop.  

I tried the alternate image, it starts to install, gets past the base install and then hangs.  Looked in to it and the kernel panics.  I was able to solve the kernel panic problem by including 'noapic' and 'nolapic' as kernel boot options.  I also use 'vga=771' to get around the text mode issues.  So, with that in place the installer gets further along but then randomly dies.  I enabled debugging 'DEBUG_MODE=5' or something like that and started tailing '/var/log/syslog.log'.  I can see all the packages installing and then the entire system just hangs.  No error messages, nothing apparently wrong, it just stops.  

So, I tried downloading that latest beta version of Ubuntu that was released a few days ago and I have the exact same problem.  

I am stumped at this point.

---

### Post by GeryonD on 2008-07-03
> **omega13a said:**
> This problem doesn't seem to be with LCDs. I'm having the same problem with the old fashion bulky monitors (whatever they are called). Its so annoying. My hard drive failed unexpectedly and I can't reinstall Ubuntu on a new hard drive because of this problem... :mad:

Correct.  The problem is with the DDC support of the monitor.  DDC (Display Data Channel) is a serial connection that can be read and written to by the OS to get all the information for the monitor attached to it as well as change the settings of a montior.  The video controller must support this as well, which means the driver must support it.  It works over a standard analog 15pin VGA cable, DVI and HDMI.  So the problem is the DDC implementation in the monitor is faulty or the video card doesn't support it properly or the driver. 

In the case of our Averatec's, it's either the controller or the LCD display's implementation of DDC since the VESA driver does not support, which as of 1998 became part of the standard.

---

### Post by GeryonD on 2008-07-03
Okay, so the random hanging, I think it's my hardware.  I am running a memory test now.

Try downloading the alternate CD with the regular Debian text-based curses installer.  Then, once the system is running do an apt-get to update everything.  That may work.r

---

### Post by bennmann on 2008-07-15
I have the same problem, and GeryonD might be on the right track with the memory test - except it's probably not faulty.

My 3200 only has 256MB ram which is a hindrance to all 8.04 versions (even xubuntu). I'll also have a peak into this DDC problem, maybe now with a few more collaborations we can make some progress. Ubuntu is my distro (basically synaptic is the best thing since Windows 95 - only tons better), I don't plan on switching. I want to make this work so I can give the aging Alveratec hard drive a rest while I merely browse the interwebs. 

It does nearly the same thing with my USB persistent Xubuntu install too, but I'll be happy getting live or USB running.

---

### Post by GeryonD on 2008-07-16
Well, at this point I downloaded and tried what was working, 6.06LTS and it works.  I am posting from it now.  Everything appears to be working fine.  The install went flawless through the GUI.  So my lockups were due to some changes in the newer kernels it appears.  I have 512MB RAM in here and I ran the test for a good 18 hours and it came back just fine.  

So, even if we got X on the LiveCD to run, would the system install without hanging?  I can not see any debugging information being dumped anywhere at all.  I think it may purely be an incompatibility with hardware and perhaps a module.  I am certain there are some kernel parameters or a module that can be unloaded that will solve the problem.  I just don't know if I want to bother at this point.  The system works fine under 6.06LTS.  So perhaps come April 2009 I'll give it another shot.

---

### Post by jfare on 2008-07-21
I am able to get my xubuntu going.... more or less....

To get the video working, I need to follow the instructions [here to change xorg.conf]("http://www.linuxcompatible.org/Averatec_3225HS_c12097.html")  THEN I type xinit followed by x-session-manager and IT WORKS!!!

However, all these changes are LOST when i reboot.  AAAAAAAAAAaaaa!!!!!!!

WHY are hard disk changes not persistent?
[J.F.]

---

### Post by zvacet on 2008-07-22
```
gksudo gedit xorg.conf
```

make your changes and after that save and close file.

---

### Post by jfare on 2008-07-24
I actually did NOT have it installed per se, just the boot configuration was intalled.  the thread [http://ubuntuforums.org/showthread.php?p=5450062#post5450062](http://ubuntuforums.org/showthread.php?p=5450062#post5450062) has details on how I got the install to continue.  Also, I was _installing_ 8.04.01 -- not _upgrading_.

[J.F.]

---

