---
title: "Dual boot Acer Aspire D250 - recovery partition"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by David_UK on 2010-11-13
I'm thinking of buying an Acer Aspire D250 loaded with Win7 and then adding a version of Ubuntu.

The netbook will come with the Acer recovery facility to reinstall Win7 from a recovery partition in the event of OS failure.  This means that the MBR and subsequent loaders need to be preserved for this function to remain (I don't have a Win7 disc and don't want to have to buy one).

I'm happy with a basic Win/Linux dual boot setup but I'd value any comments/suggestions as to how to preserve the recovery function when I add Ubuntu.

---

### Post by azedddine on 2010-11-13
hello,

i have the same netbook (acer aspire one D255) with windows xp home edition sp3, it comes with the same recovery partiton that you are talking about, i installed ubuntu 10.10, grub knows the recovery partition without any problems, i suggest that you install it.

good luck

---

### Post by lmarmisa on 2010-11-13
Hi David,

I strongly recommend you to use virtualization. I love [VirtualBox]("http://www.virtualbox.org/"). It worlks really great.

These two videos are a bit old but interesting:

[http://www.youtube.com/watch?v=c9ObBRh2M1I](http://www.youtube.com/watch?v=c9ObBRh2M1I)
[http://www.youtube.com/watch?v=79bOzMd4Vww](http://www.youtube.com/watch?v=79bOzMd4Vww)

If you use virtualization, you do not change at all the disk partitions or the MBR. The virtual disks of the virtual machines are simply normal NTFS files. Even more: you can create as many virtual machines as you want running Ubuntu or any other operating system. An Ubuntu virtual machine is simply a program running in your Windows 7 system like any other.

---

### Post by laurenbanjo on 2010-11-13
I have Ubuntu 10.10 on my Acer AspireOne D255 with Windows 7. 

When it turns on, it lets you switch between Ubuntu, Ubuntu Safe Mode, Windows 7, and Windows Vista, which I think is the recovery part. On my other Acer AspireOne (different model) I used the "Vista" to reset to factory defaults, if this is what you mean.

---

### Post by lmarmisa on 2010-11-13
More recent videos about VirtualBox and Ubuntu:

[http://www.youtube.com/watch?v=9wxwkF6Ml1A](http://www.youtube.com/watch?v=9wxwkF6Ml1A)

[http://www.youtube.com/watch?v=AQo5bRRoQM0](http://www.youtube.com/watch?v=AQo5bRRoQM0)

---

### Post by David_UK on 2010-11-13
> **lmarmisa said:**
> An Ubuntu virtual machine is simply a program running in your Windows 7 system like any other.
Thanks.  I don't want to boot into windows first.  The intention is to offer a fast boot alternative.

> **azedddine said:**
> ...i installed ubuntu 10.10, grub knows the recovery partition without any problems...
> **laurenbanjo said:**
> ...I used the "Vista" to reset to factory defaults...
Thats very encouraging.  So have you managed to access the restoration facility since installing GRUB?  I'm wondering where in the boot chain the hidden restoration partition is accessed.

---

### Post by laurenbanjo on 2010-11-13
> **David_UK said:**
> 
Thats very encouraging.  So have you managed to access the restoration facility since installing GRUB?  I'm wondering where in the boot chain the hidden restoration partition is accessed.

Yeah, it was pretty weird. At first I saw it and thought I had Windows Vista and was confused. but then I looked at it an realized it was a recovery partition.

I don't know how to access it other than through GRUB, but I also never tried.
Although I saw it in the partition manager. It's about 17 gigs or something.

---

### Post by lmarmisa on 2010-11-13
Wubi is another alternative if you do not want to modify partitions or MBR.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

In this case, the Windows loader starts up Windows 7 or Ubuntu. 

The files for the Ubuntu OS are stored in the NTFS file system. Each partition of the Ubuntu installation (root, swap, etc) is stored in one NTFS file.

---

### Post by David_UK on 2010-11-14
> **lmarmisa said:**
> Wubi is another alternative if you do not want to modify partitions or MBR.
Thanks!  I'll have a look at that.

> **laurenbanjo said:**
> ...I don't know how to access it ...
The [_[COLOR="Blue"]manual[/COLOR]_]("http://support.acer.com/acerpanam/Manuals/acer/2009/UserGuides/AO_D250_JV01_User_Guide_Eng_OLM_0227.pdf") gives a brief overview, though some forum posts describe using different keys.
The recovery function can be accessed via the start menu if the system boots, or if it doesn't it's selected by keyboard action during the first seconds of power-up.  Let's hope you never need it!

---

### Post by David_UK on 2010-11-14
> **David_UK said:**
> I'd value any comments/suggestions as to how to preserve the recovery function when I add Ubuntu.
Update: Ok, I can see now from more searching that if the MBR is changed at all (by Multiboot, Windows upgrade etc) then the Acer restore function will fail.  However, the restoration partition will still be there in my scenario, so it is possible using MBR utilities to make it active and therefore to reboot into the recovery function.
Thanks for your input guys - SOLVED.

---

### Post by David_UK on 2010-12-30
UPDATE: (for anyone finding this thread doing something similar)
Ok, I've now installed Ubuntu (Netbook 10.10 - pretty funky looking!) so here's what I found.
Firstly, if your netbook comes with Android as a dual boot - switch it off in the windows management app before installing linux.  Android was no longer available after linux install  - I haven't tried enabling it again in windows for fear of breaking the bootloader chain.

Install ubuntu as normal.  I'd normally use a seperate partition for /home, but after doing this ubuntu would not boot up - with an error that the home partition was not available - so I reinstalled allowing ubuntu to make the partitions.

In Grub, linux is listed as normal, as is Windows7 (the version installed on this netbook).  Also listed though it Windows Vista - this is the recovery partition.  DO NOT BOOT INTO THIS OPTION UNLESS YOU ARE PREPARED TO LOSE GRUB, as doing so, even if you do not run the recovery application alters the boot flags in the chain and ubuntu does not boot.  I did, to try it, and because I am not adept at reinserting grub2 into the MBR I just did a reinstall of linux to sort it out.

Apart from that, all goes just fine.  The netbook installation runs pretty well, though it does appear to all go blank and rebuild the desktop occasionally (is this the shell crashing?).  Incidentally, a bootable USB of ubuntu desktop runs just fine on this laptop and did not exibit any odd behaviour (but the screeen is getting pretty narrow from top to bottom if you use desktop).  I tried moving the panel to the edge - that was a mistake - it's so cramped there was nowhere to click to move it back to the top and I couldn't select the system menu as the firefox icon was superimposed on it.  I had to reset the panel via terminal to sort that.

Oh, btw, wireless was detected and works reliably.

---

