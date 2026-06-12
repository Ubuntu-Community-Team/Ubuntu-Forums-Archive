---
title: "I want to install Ubuntu on a virus-infected computer."
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by geekchic9 on 2006-11-19
Hello, everyone!

I want to install Ubuntu on a Windows Compaq Presario laptop that got a virus on it last week. Unfortunately, we didn't realize there was a virus on it until this Thursday, and by then, we suspect, the boot sector on the hard drive got corrupted. I was unable to boot to the Ubuntu Desktop installation CD without the computer crashing. I have tried the CD before this computer got a virus, and it worked perfectly.

We were unable to remove the virus as of yesterday. We don't know if it can boot a Windows CD, as my (very disorganized) boss can't find the Windows CD. The virus in question creates hundreds of threads that use up 99% of the CPU's power. The computer can't print, either. However, we were able to back up some material off of the computer onto a CD and a USB flash drive. 

Question:
Should we take this computer to a place like CompUSA and let them handle this mess, or is there some sort of possibility that we could still wipe the drive and install Ubuntu ourselves?

By the way, I don't have access to the computer at this moment, but I promised my boss that I would ask on this forum for help. I will have access to it again tomorrow (Monday).

Thank you for your advice.

---

### Post by Jussi Kukkonen on 2006-11-19
It is very unlikely that a virus would prevent you from booting from a CD. Have you checked that the CD drive is before hard drives in BIOS boot order?

---

### Post by geekchic9 on 2006-11-19
> **Jussi Kukkonen said:**
> It is very unlikely that a virus would prevent you from booting from a CD. Have you checked that the CD drive is before hard drives in BIOS boot order?
Well, let me correct myself: It can boot to the Ubuntu CD's first screen. However, when I select "Run or Install Ubuntu" or "Run or Install Ubuntu safe graphics mode", the computer crashes. Like I said before, this is very strange to me, because before the virus was there, the Ubuntu CD worked perfectly, and even detected all the hardware.

---

### Post by Jussi Kukkonen on 2006-11-19
That's probably not related to a virus... Two choices that I can see:
1. the ubuntu install doesn't work on your hardware for some reason (you could try an *alternate CD* install, but there's no guarantees). This would not be related to your windows problems.
2. Some hardware (memory or main board maybe) on your machine is broken and that screws both ubuntu and windows. If you are 100% that the windows problems are because of a virus, this probably is not true.

---

### Post by zoidburg016 on 2006-11-19
Have you repartitioned the hard drive? If there is a virus the repartitioning the hard drive should delete it.

---

### Post by geekchic9 on 2006-11-19
> Two choices that I can see:
1. the ubuntu install doesn't work on your hardware for some reason (you could try an alternate CD install, but there's no guarantees). This would not be related to your windows problems.


I'll try the alternative CD installation disk Monday.

> 
2. Some hardware (memory or main board maybe) on your machine is broken and that screws both ubuntu and windows. If you are 100% that the windows problems are because of a virus, this probably is not true.

How can I check to see if the hardware is broken? I figure I can possibly run the memory test from the Ubuntu installation CD, but what if something else, like the processor, for example, is broken? The processor has been overheating lately because it's been using 99% of its processing power from all of the threads created by the virus (we assume). I suppose I could google this, but it would be nice to have some recommendations.

---

### Post by aysiu on 2006-11-19
> **Jussi Kukkonen said:**
> That's probably not related to a virus... Two choices that I can see:
1. the ubuntu install doesn't work on your hardware for some reason (you could try an *alternate CD* install, but there's no guarantees). This would not be related to your windows problems.
2. Some hardware (memory or main board maybe) on your machine is broken and that screws both ubuntu and windows. If you are 100% that the windows problems are because of a virus, this probably is not true.
Or the CD itself (or the ISO it was burned from) is corrupt.

---

### Post by mutantapple on 2006-11-19
Let's assume that it is a virus, if this is truely the case, and you don't mind cleansing your hard disk, then I suggest reformatting the entire hard disk. However the only way I can think of doing that is by using some Operating System CD like Windows to reformat it though the BIOS or commandline or something.



Does anyone have any imput to this idea?

---

### Post by Teroedni on 2006-11-19
assuming that the disc has no error
You probably need to write noapic or some other arguments to the boot options before booting the installer.
I know that you can press F1 at the boot screen to see what arguments you can add in order to make the installer work on troublesome hardware.

---

### Post by bigken on 2006-11-19
If your going to wipe the drive 1st just use the gparted liveCD

---

### Post by scrooge_74 on 2006-11-19
My opinion, if there is anything important in the disk, take it out and hook it to another computer that either has XP with antivirus or a Linux manchines that does work. Take the data out or clean it.  

i have done this with disks that had bad sectors or that were infected

---

### Post by Swab on 2006-11-19
Zero fill the entire drive, then repartition.  The manufacturer of the drive may provide a utility to do this.  For instance Maxtor has something called MaxBlaster which is a bootable floppy/CD full of disk utilities.

---

### Post by drphilngood on 2006-11-19
IIWY, I would want to write zeros to the drive; this is the only way to be sure that you are really starting with a clean machine.

---

### Post by geekchic9 on 2006-11-19
I think I will DBAN the computer's hard drive, then install Ubuntu.

While googling, I learned about Stress Linux, which is a distro explicitly created to test hardware. I'll try that, too. It's at [www.stresslinux.org](www.stresslinux.org).

Thanks, everyone.

---

### Post by indigoshift on 2006-11-19
> **mutantapple said:**
> Let's assume that it is a virus, if this is truely the case, and you don't mind cleansing your hard disk, then I suggest reformatting the entire hard disk. However the only way I can think of doing that is by using some Operating System CD like Windows to reformat it though the BIOS or commandline or something.



Does anyone have any imput to this idea?

I would suggest Darik's Boot & Nuke:

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

An excellent tool for wiping a hard drive clean.  Of course, you'll need another computer to download it and burn it to CD.

---

### Post by geekchic9 on 2006-11-20
It turns out it was a hardware problem, probably the processor.

Thanks again.

---

### Post by feign on 2006-11-20
What is your long-term goal here to run Ubuntu on the laptop?  If so the alternate install seems like your best bet.  You will want 

You reference take it to CompUSA, if you took it there you potentially would go in a different direction with a Win OS on it.

If you plan on going back to Windows you might be better off locating a good knoppix distro and booting into that and attempting to recover your data first.  While you are working on that I would call HP and get a copy of your original discs.

just my opinion...

---

