---
title: "Can't Install ANY Distro of Linux"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by pentiumwetwired on 2008-06-01
Hi, my first post here. I've been semi-interested in Linux in any flavor for a few years now. I'm having a problem installing virtually any distro of Linux on this computer. I've also tried using Wubi. 

When I try installing from a CD (I've tried several from many different sources, friends, downloads, etc.), I select the option to install and the screen goes black with some random garbled characters running along the bottom of the screen. Sorry, I don't have any info on what those characters are at the moment, if they are important I can add those in another post. 

When installing using Wubi, the installation goes through just fine but when I reboot and select Ubuntu the system hangs right after loading the Ubuntu splash screen, XP Pro loads fine. 

My system specs are: HP Pavilion a705w, 2.93GHz Celeron, 1GB of DDR 333, ATI Radeon 9250 256, LITE-ON COMBO SOHC-4832K optical drive, Seagate ST340015A 40GB ATA hard disk (jumper set to master), and a Maxtor 4D040H2 40GB ATA hard disk (jumper set to slave). 

Any help with this would be greatly appreciated.

---

### Post by tamoneya on 2008-06-01
try selecting the safe graphics mode install.  This should handle the graphics issues that are introduced by your ATI card which has spotty linux drivers.  On the hardy CD i believe you have to go into boot options in order to select the safe graphics mode.

---

### Post by pentiumwetwired on 2008-06-01
Thanks for the quick reply, but I guess I should have said that I'd like to use Wubi so I don't destroy the data already on both the drives. Is this possible?

---

### Post by tamoneya on 2008-06-01
okay so get you wubi install setup again and when grub loads hit escape. This is one of the first screens you see after the bios.  Select the recovery option and see if you can boot into the CLI.  From there type ```
/etc/init.d/gdm start
```

---

### Post by pentiumwetwired on 2008-06-01
Thanks! I'll try this a.s.a.p.

---

### Post by pentiumwetwired on 2008-06-01
Ok, so I installed with Wubi, restarted the machine, selected Ubuntu, hit esc and got a menu with a few choices, safe graphics mode, with APACI (I think) workarounds, start normally, verbose mode, and Live CD.

With safe graphics mode the start-up stalls and displays:

> init: rcS main Process (5434) killed by SGEV signal
init: Unable to execute "bin/sh" for rc-default: Permission Denied
init: rc-default main process (6568 ) terminated with status 255 

With the workarounds selection I get:
> init: rcS main Process (5434) killed by SGEV signal
init: Unable to execute "bin/sh" for rc-default: No such file or directory
init: rc-default main process (6568 ) terminated with status 255 

Any ideas?

---

### Post by pentiumwetwired on 2008-06-01
Any help on this? Uncharted territory?

---

### Post by sparo007 on 2008-06-01
Bump.  I too have a similar problem with an HP m7060n.

---

### Post by alzie on 2008-06-01
Its been a while since I used wubi...

I searched around and the HP Pavilion a705w does seem to have issues, the workaround is to add the parameter " acpi=off " (without the quotes)

From the wubiguide
> Sometimes the ACPI is not fully supported and can hang the boot process or you may experience video problems (black screen). In such cases, after you select "Ubuntu" at boot, press "ESC" and choose one of the other options  You should be able to set acpi=off there.

Link to wubi guide is : [https://wiki.ubuntu.com/WubiGuide#head-f6c266ddcf7323c8f74bdbb03ac9b0f3860f194b](https://wiki.ubuntu.com/WubiGuide#head-f6c266ddcf7323c8f74bdbb03ac9b0f3860f194b)

Link to the wubi forums is :[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

I recommend the wubi forums,  the people there do a great job.

I hope this helps you :)

---

### Post by alguin2 on 2008-06-01
Have you tried the Live CD (HH 8.04), just to check if Ubuntu can boot?  That's how I installed Ubuntu. I think that there's an option of installing Linux within the Windows filesystem from the LiveCD.  I myself installed by creating a real partition.

Try booting from a cold powerdown, safe graphics, etc, if the default LiveCD boot doesn't work.

Good luck.

---

### Post by Pumalite on 2008-06-01
This is an HP thread that might explain some of the problems:
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by pentiumwetwired on 2008-06-01
> **alzie said:**
> Its been a while since I used wubi...

I searched around and the HP Pavilion a705w does seem to have issues, the workaround is to add the parameter " acpi=off " (without the quotes)

From the wubiguide
  You should be able to set acpi=off there.

Link to wubi guide is : [https://wiki.ubuntu.com/WubiGuide#head-f6c266ddcf7323c8f74bdbb03ac9b0f3860f194b](https://wiki.ubuntu.com/WubiGuide#head-f6c266ddcf7323c8f74bdbb03ac9b0f3860f194b)

Link to the wubi forums is :[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

I recommend the wubi forums,  the people there do a great job.

I hope this helps you :)
I just tried this option just 5 minutes ago and got a "Bad string or file command" or something of the sort

> **alguin2 said:**
> Have you tried the Live CD (HH 8.04), just to check if Ubuntu can boot?  That's how I installed Ubuntu. I think that there's an option of installing Linux within the Windows filesystem from the LiveCD.  I myself installed by creating a real partition.

Try booting from a cold powerdown, safe graphics, etc, if the default LiveCD boot doesn't work.

Good luck.
I've tried every option on the esc menu including the live CD, no dice

> **Pumalite said:**
> This is an HP thread that might explain some of the problems:
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
That thread is about laptops, this is a desktop.

I think I'm stuck, I'm giving up unless someone has a fix I haven't tried. Thanks for all your help everyone.

---

### Post by sparo007 on 2008-06-03
Bump.  He may have given up, but I sure haven't, I will continue to bump this thread until someone answers my cries for help or this forum shuts down.

---

### Post by pentiumwetwired on 2008-06-04
Good luck sparo007, I'm just gonna install it on another computer I have laying around. I have this thread subscribed so if it ever gets solved I'll be sure to change the title to reflect its status.

---

### Post by alzie on 2008-06-05
I've been googling.  I did find this link:
[http://www.uluga.ubuntuforums.org/showthread.php?t=799725](http://www.uluga.ubuntuforums.org/showthread.php?t=799725)

It was suggested to the poster to try and install ubuntu using vmware.  The poster was able to but was unable to work with wubi or from the live cd.

Another poster, Ago said 

> If you have the same problems when you boot from live CD it is not wubi related. It is unlikely that you have a bad ISO since wubi checks the md5.

The fact that you can install to vm suggest that it might be an incompatibility with your hardware. There are workarounds for that via boot parameters like xforcevesa or acpi=off or irq=poll.

Such workarounds can be enabled from the Live CD (see boot options) or Wubi (press esc at boot). You will have to search for the make and model of your machine to find the appropriate parameters to use.

Also, if you do not find any existing bug in launchpad, open a new one, reporting your hardware issues, so that it can be addressed for good.

I'm hoping this will help.  If you think you've found a bug, report it and you help others.

---

### Post by Luser2 on 2008-06-22
> **sparo007 said:**
> Bump.  He may have given up, but I sure haven't, I will continue to bump this thread until someone answers my cries for help or this forum shuts down.


I'm trying to run 8.04 from the disk on an HP Pavilion a705w as well.  No answers yet, and it's fair to guess by my user name that I may not be the one to solve the problem.

The latest message I got was:

---
/etc/init.d/rc: 317: sed: not found  (<--- this one over and over)
---

on hitting <enter> I got:

---
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (7572) terminated with status 255
---

Just another data point.  I will work on figuring out how to implement the suggestions mentioned in messages above.  Of course, any help is gratefully received...

---

### Post by Luser2 on 2008-11-01
"Bump"

Anyone?

---

