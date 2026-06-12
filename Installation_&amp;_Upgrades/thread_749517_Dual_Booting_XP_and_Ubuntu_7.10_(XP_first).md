---
title: "Dual Booting XP and Ubuntu 7.10 (XP first)"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by madnutter56 on 2008-04-08
Hi, I am trying to dual boot my xp machine and Ubuntu 7.10 (x86 edition), I already have XP installed, and tried to install ubuntu as a dual boot, I went through the setup, and when I got to the disk partitioning part, I selected to resize the partition where windows is installed, and then clicked forward, then, it said  "resizing partitions" and then came up with an error, saying it had failed. The partition in question is a 73GB ntfs partition with XP service pack 2 installed.

Any help would be appreciated, 

Thanks.

---

### Post by Pumalite on 2008-04-08
This might help:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by madnutter56 on 2008-04-08
No, not really. You see, I already have XP installed, and XP does not have any partition resizing tools bundled with it, so I cannot use that. I do exactly as the first link says about the manual partition table bit, but I can see the ntfs parttion of XP. When I try to resize this, it just comes up with an error, and then stops.

---

### Post by Pumalite on 2008-04-08
Ok: Try this then. Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP, choose 'resize' from the menu. In the 'free space left; make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (in laptops /swap=RAM if you want to hibernate)
The rest for /home.
Install Ubuntu, go 'Manual' and choose the partitions already prepared.

---

### Post by madnutter56 on 2008-04-08
Ok, I'll try that in the morning when I have some more time, got some work to do right now. I'll let you know how I get on.

Gotta find a CD for gparted first...

---

### Post by Pumalite on 2008-04-08
Good luck.

---

### Post by madnutter56 on 2008-04-09
Right, the results.

It installed, and I have dual booted Ubuntu and XP, I'm using Ubuntu to type this, so it definetly works, there are a few issues that need sorting out though.

1. I have no sound through the line in, I use this for my iPod, as you cannot get iTunes on Ubuntu.
2. Hibernation, It seems to hibernate Ok, but when you switch it back on, it just loads fine, and then goes to a green screen. If you click where applications is normally (or system), it opens that menu, and some of the green changes shade.
3. Resolution, the default resolutions do not fit my monitor brilliantly, How can I set a custom resolution?

Hope someone can help me.

Thanks.

Alex :)

---

### Post by Pumalite on 2008-04-09
Let's check your sound. Post:
lshw -C sound

---

### Post by madnutter56 on 2008-04-10
```
  *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
```

---

### Post by madnutter56 on 2008-04-10
OK, Sound problem fixed.

I just need the answers to the resolution and the hibernation problems now.

---

### Post by phenest on 2008-04-10
Can I just point out that your original error to do with resizing the NTFS partition, was probably due to you using the Live CD. When you use the live CD, it mounted the NTFS partition so you could access it. It is not possible to resize a partition when it's mounted.

---

### Post by madnutter56 on 2008-04-10
OH, right. Thanks. That makes more sense now.

Have you got any ideas on the Hibernation and Screen Resolution issues?

---

### Post by popsbear on 2008-04-10
Sorry to interrupt but you seem to have the set up I aspire to.

I am going to set up a new machine with XP pro and Ubuntu 7.1 (absolute novice).  Will have a 500Gb drive, what are suggested partitions and formats.

---

### Post by madnutter56 on 2008-04-10
Well, first I would get hold of a Gparted live cd (link in earlier post).

Burn that then boot from it.

I would say, 10 gb mounted at "/"
100GB mounted at "/home" or whereever you want your files to be.
1-3GB for "/swap" set the drive filesystem to "linuxswap"

Then  leave the rest for xp, btw.

Install XP first.
Then take ubuntu and install that, but in hard drive section of the live cd, select manual and select the partition you made earlier, the "/" 10 GB one that is.

Hope you have some luck.

Good Luck

---

### Post by madnutter56 on 2008-04-11
Has anyone got any more ideas on my Hibernation and Screen Resolution problems?

---

### Post by phenest on 2008-04-11
> **madnutter56 said:**
> Has anyone got any more ideas on my Hibernation and Screen Resolution problems?

What is the make, model, and spec of your computer? Then we have something to work with.

As for partitioning, there is one thing that everyone fails to mention. To install Ubuntu, make all partitions Logical. You can only have a maximum of 4 primary partitions, and considering Windows wants to be on a Primary partition (Vista MIGHT install to a Logical), is makes sense not to use them all up in a hurry.

Personally, I have 3 Logical partitions for Ubuntu, and one Primary for XP.
[LIST]
[*]4GB - Swap (same size as my RAM so I can hibernate)
[*]10GB - root (I've used less than 4GB so far)
[*]The rest for /home (saves having to backup files when re-installing)
[/LIST]

---

### Post by Mattman09 on 2008-04-11
hi i've tried this many times "Dual Booting Windows Xp and Ubuntu 7.10" and i get the same exact error regardless of how i burn the cd. I would say that i've went through 8 cd's to see if that was the problem but still no luck. So i've came to the ubuntu forums, what my question is what is the problem i've put the cd in and booted from it then when the ubuntu loader comes up it loads perfectly i select install or upgrade or whatever ubuntu and then it loads after loading a screen will flash 3 times saying

*Starting deferred execution scheduler atd
*Starting periodic command scheduler crond

---

### Post by Mattman09 on 2008-04-11
hi i've tried this many times "Dual Booting Windows Xp and Ubuntu 7.10" and i get the same exact error regardless of how i burn the cd. I would say that i've went through 8 cd's to see if that was the problem but still no luck. So i've came to the ubuntu forums, what my question is what is the problem i've put the cd in and booted from it then when the ubuntu loader comes up it loads perfectly i select install or upgrade or whatever ubuntu and then it loads after loading a screen will flash 3 times saying

*Starting deferred execution scheduler atd
*Starting periodic command scheduler crond
*Checking battery state...
*Running local boot scripts (/ect/rc.local)

I've left this up for 3 days 1 time to see if it actually would work but still no luck.

So please guys help me i really want to use ubuntu!!!! :KS

---

### Post by Pumalite on 2008-04-11
Do the partitioning with Gparted as I explained earlier. Then install with the Alternate CD

Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x ot less on CD-R, check CD integrity after burn and before install.
Try your CD's in different computers. Clean the lens in your burner.

---

### Post by madnutter56 on 2008-04-11
> **phenest said:**
> What is the make, model, and spec of your computer? Then we have something to work with.

As for partitioning, there is one thing that everyone fails to mention. To install Ubuntu, make all partitions Logical. You can only have a maximum of 4 primary partitions, and considering Windows wants to be on a Primary partition (Vista MIGHT install to a Logical), is makes sense not to use them all up in a hurry.

Personally, I have 3 Logical partitions for Ubuntu, and one Primary for XP.
[LIST]
[*]4GB - Swap (same size as my RAM so I can hibernate)
[*]10GB - root (I've used less than 4GB so far)
[*]The rest for /home (saves having to backup files when re-installing)
[/LIST]

Make : eMachines
Model : 3260
CPU : Intel Celeron D (2.8GHz) 256k L2 Cache 533mHz FSB
CD Writer
1.25GB Ram (1GB, 256MB)
80GB Hard Drive (WDC WD800BB-22JHA0)
Integrated Graphics card. (64MB Memory)

If you need any more details, please ask.

---

### Post by phenest on 2008-04-11
To be able to hibernate, the swap partition must be the same size (or a bit bigger preferably) than your RAM size. Check this first.

As for resolution, what video card is it, would should the resolution be, ond what does Ubuntu report for all this? I need to know what you should have and what Ubuntu thinks you have.

---

### Post by madnutter56 on 2008-04-11
> **phenest said:**
> To be able to hibernate, the swap partition must be the same size (or a bit bigger preferably) than your RAM size. Check this first.

As for resolution, what video card is it, would should the resolution be, ond what does Ubuntu report for all this? I need to know what you should have and what Ubuntu thinks you have.

My Disk setup;
[http://img362.imageshack.us/my.php?image=diskswd9.png](http://img362.imageshack.us/my.php?image=diskswd9.png)
Swap is bigger than my ram in this case.
Graphics Card: Intel 82845G/GL/GE/PE/GV Graphics Controller

Wanted resolution: 1024x768 (already using in XP)
Ubuntu options:
640x480
800x600 (Don't want, makes everything too big)
1156x768 (Currently using this, but it does not fit)
1200x800

Is that what you want?

---

### Post by phenest on 2008-04-11
That png was taken from Windows. It may be big enough, but is Ubuntu using it? From Ubuntu, open System Monitor and see if the swap file is being used (Resources tab). It should show you the size of the swap partition.

As for the resolution, there was a problem with Intel drivers not giving all resolutions with some chipsets. Make sure you have 915resolution installed. If not, install it, reboot, and check your settings again.

---

### Post by madnutter56 on 2008-04-11
> **phenest said:**
> 
As for the resolution, there was a problem with Intel drivers not giving all resolutions with some chipsets. Make sure you have 915resolution installed. If not, install it, reboot, and check your settings again.

What's the 915 resolution?

Do i need to search for it in package manager?

---

### Post by phenest on 2008-04-11
```
sudo apt-get install 915resolution
```

---

### Post by madnutter56 on 2008-04-11
Thanks!

Resolution is now fixed.

About the swap, it's not being used, ubuntu has found it, but says using 0 bytes out of 2.4GB.

How do you enable the swap?

---

### Post by phenest on 2008-04-11
My apologies. I meant to say, make sure it's mounted. Which it is.

I'm glad your resolution is ok, but as for hibernation... I'm afraid that most people have this problem. Mine doesn't work either. I do not know why. Sorry to be unhelpful. Perhaps you ought to do some searching here or start a specific thread for your computer.

---

### Post by madnutter56 on 2008-04-11
Well, the swap is being used when I go over 400MB of RAM or so.

I'm installing WIndows 98 virtually!!

lol...

It's using 400MB RAM and 33MB swap.

LOL.

Don't really need the swap.

Thanks for your help!

---

