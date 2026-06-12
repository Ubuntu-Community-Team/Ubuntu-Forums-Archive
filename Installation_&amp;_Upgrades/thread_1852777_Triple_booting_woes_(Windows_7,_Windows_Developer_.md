---
title: "Triple booting woes (Windows 7, Windows Developer Preview, Ubuntu 10.04.3 LTS)"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by JoeHeinemeyer on 2011-09-30
I am having difficulty getting the three operating systems to work together without constant attempted prison shanking.  I am attempting to triple boot:
   --Ubuntu 10.04.3 LTS (Desktop version, 64 Bit)
   --Windows 7 Home Premium (64 bit)
   --Windows Developer Preview (64 bit) (Before you ask, it's pre-beta Windows 8 - [http://msdn.microsoft.com/en-us/windows/apps/br229516]("http://msdn.microsoft.com/en-us/windows/apps/br229516") )

Grub2 is working perfectly, but the chainbooting through the Windows Bootloader thingy is completely hosed in this case.  Neither Windows 7 or 8 control which options appear on the boot menu, nor for how long it is displayed. (30 seconds, ugh)  As such, is there any way I can get either a workaround for the bootloader to co-operate with Grub2, or just any way I can get this to work without looking like a diseased whale vomited into my bootsector?

Any help is appreciated.

Technical info:

Installation order:
   --Windows 7 (It was OEM)
   --Windows 8 (It somehow maliciously eradicated my previous Ubuntu install)
   --Ubuntu 10.04.3 LTS

Current Partitioning Scheme:
   --sda1: System Reserved (Always installed with Windows 7, but now it seems like the bootloader is has somehow migrated out of this partition)
   --sda2: Windows 7 Installation (It seems the bootloader has made this it's new residence)
   --sda3: Windows 8 Developer Preview (IDK what this thing was trying to do.  It removed my previous linux install, and might have moved it's bootloader into sda2, which overwrote the Win7 one for a while)
   --sda4 Extended partiton:
     --sda5: partition I used to store ISO files, so I could have grub2 boot them even if I somehow broke the Ubuntu partition (See how well that turned out?)
     --sda6: swap space, about 2 gigs
     --sda7: current Ubuntu partition, flagged as boot, and Grub2 is installed here.

The computer is a ASUS U53Jc upgraded with 8 gigabytes of RAM.  sda is a 640 gigabyte hard drive.

I have already done startup repair with a Win7 install disk 3 or 4 times, through various attempts to repair the bootloader clusterf***, but to no avail.  The windows bootloader was originally in sda1 before Windows 8 was installed, where it was overthrown with one shoehorned into sda2.  I have not yet attempted to reinstall anything other than Ubuntu, but I do have backups of the Windows 7 partition if I need to.  Finally, yes I /HAVE/ called *shudders* Microsoft Support.  They were incredibly unhelpful.

I will add any further technical info as requested, thank you.

---

### Post by Hakunka-Matata on 2011-09-30
Hi, Welcome;
Please download, install and run boot_info_script.  Post results.

---

### Post by oldfred on 2011-10-01
+1 on Hakunka-Matata suggestion of boot script.

Understand that grub does not use boot flag, Windows has to have a boot flag to know the active partition which in windows is the boot flag. Windows only boots from the active partition which should have been sda1. Perhaps 8 was able to find the install in sda2 and in effect repair it. Second installs of windows normally move boot files to the active partition and are not direclty bootable from grub as they have no boot files.

While this is Vista, 7 and I maybe 8 work the same way.
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Do you have a Windows repairCD or USB?

---

### Post by JoeHeinemeyer on 2011-10-01
Excellent advice, Oldfred!  I got so frustrated (It's been 10 hours so far) that I deleted all partitions except for the once containing Windows 7, and am repartitioning as we speak.  Hopefully I can report positive results tomorrow morning (It's 10:11 pm, here), otherwise I will probably use some choice language to describe certain people at Microsoft and post the outputs from that boot info script.  

Thanks for the help!

---

### Post by oldfred on 2011-10-01
Have not seen many Windows 8 installs, will be interesting to see how it works for you. Most triple installs have been XP & 7 or Vista & 7 with grub2 able to boot everything.

I prefer keeping Windows on one drive and Ubuntu on other drive(s). That helps avoid issues between the systems.

---

### Post by Mark Phelps on 2011-10-01
It's become standard practice now for new Windows OS installs to use any older Windows install partition for its loader files.  Vista did this with XP.  Win7 did this with Vista.  It's to be expected that Win8 will do the same thing with Win7.

As for any damage done -- this is after all a PRE-Beta, so just about anything goes at this point.

---

### Post by JoeHeinemeyer on 2011-10-01
Haha! I succeeded in erasing everything and got it to boot right into Windows 7.  (After much startup repair and use of diskpart.)  I am going to run on the assumption that the bootloader will get shoved into either the boot or active partition, so before I move on and install Windows 8, I will have a partition for it marked both boot and active.
I will keep you all informed of the progress.
Thanks!

---

### Post by JoeHeinemeyer on 2011-10-01
Victory!  All OSes are booting properly, and the only remaining problem I have is due to my own stupidity! (I installed the NVIDIA restricted drivers in Ubuntu, and when it boots, all I get is a black screen.) Thanks for the great advice and suggestions, I only wish I had posted my problems here 6 or 8 hours sooner!

---

### Post by oldfred on 2011-10-02
Great.

Normally once I install the nVidia drivers everything works.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

