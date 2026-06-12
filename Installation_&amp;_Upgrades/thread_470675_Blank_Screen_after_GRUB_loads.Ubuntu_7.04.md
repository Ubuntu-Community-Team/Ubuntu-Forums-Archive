---
title: "Blank Screen after GRUB loads.Ubuntu 7.04"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by gauravp55 on 2007-06-11
OK I heard a lot about Ubuntu 7.04 being the best among Linux distros and I thought of installing one on my desktop with the following config:

Processor: Pentium 4, 2.4 GHz
RAM: 512 MB DDR
Chipset: Intel 845
MOBO: Intel 845GVAD2

So I booted from the Ubuntu CD and I selected Option 1. I then decided to go in for the install.. Once the disk partitioning option was presented I decided to manually do the partitioning since I wanted to dual boot with Windows XP and I had about 10.63 gigs of free space on my HD which I then partitioned as follows:

1> 7168 MB  ext3    Mount point: /
2> 1176 MB SWAP 
3> 3068 MB  fat32  Mount point:/windows 

After that I proceeded with the installation and then rebooted. The GRUB showed the following options:

Ubuntu kernel
Ubuntu kernel (recovery mode)
Ubuntu , memory test
Other Operating Systems:
Microsoft Windows XP

I chose option 1. GRUB says Loading and then the screen goes blank.. No activity for more than 5 minutes. So I restarted the PC and chose option 2(recovery mode). On typing exit, it finally booted and I was able to log on. I also noticed that even while using the LiveCd it takes atleast 5 minutes to boot.

Any idea of what the problem may be??  Thanks in advance.

---

### Post by Infinia on 2007-06-11
I had that problem with 7.04 too... Try Edgy... fixed all my problems sad to say...

---

### Post by breen92uk on 2007-06-13
> **gauravp55 said:**
> 
Chipset: Intel 845

I have a feeling that the problem may be being at least partially caused by your graphics chipset - I have the same chipset and also don't have a loading screen (but after a minute or two I'm brought normally into GDM). What's likely happening in your case is that the system is encountering another problem of some kind, but obviously because you don't have a loading screen you can't see what it is.

I'll post any solution I find here, but in the meantime I can only echo what Infinia says (the Edgy loading screen never worked for me either, but you might have more luck with getting into Ubuntu).

Edit: Still no luck with the loading screen, but if you Ctrl + Alt + F1 when the screen goes blank after GRUB boots you should be able to see the text run-through of the boot process, and hopefully the problem your system is encountering.

---

### Post by gauravp55 on 2007-06-13
> **breen92uk said:**
> I have a feeling that the problem may be being at least partially caused by your graphics chipset - I have the same chipset and also don't have a loading screen (but after a minute or two I'm brought normally into GDM). What's likely happening in your case is that the system is encountering another problem of some kind, but obviously because you don't have a loading screen you can't see what it is.

I'll post any solution I find here, but in the meantime I can only echo what Infinia says (the Edgy loading screen never worked for me either, but you might have more luck with getting into Ubuntu).

Edit: Still no luck with the loading screen, but if you Ctrl + Alt + F1 when the screen goes blank after GRUB boots you should be able to see the text run-through of the boot process, and hopefully the problem your system is encountering.

Ok I installed ubuntu again on my desktop today and after selecting boot option 1 it's the same old blank screen. Then after about 5 minutes GRUB shows up again requesting for a boot choice. I havent tried the suggested but will do so. Thanks

---

