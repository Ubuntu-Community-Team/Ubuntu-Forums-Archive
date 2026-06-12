---
title: "BIOS Configuration to boot Ubuntu on 960 Evo and Maximus IX Code"
date: 2017-06-27
forum: Installation &amp; Upgrades
---

### Post by eera5607 on 2017-06-27
Hi! I'm building a PC with one SSD (Samsung 960 EVO) and one HDD (Toshiba SATA). They are both connected to the motherboard (Asus Maximus IX Code). I want to install Ubuntu 16.04.2 on the SSD but I was investigating and now I'm confused. Do I need to do an specific procedure (enable RAID for example) to use the SSD as the boot drive with Linux? Or I can install the OS right out of the box with the default configuration? Deactivate CSM? Change the SATA mode to Intel RST? Thanks for your help.

---

### Post by oldfred on 2017-06-27
Intel SRT will be seen as RAID.
Better just to use AHCI for drives.

And better to install in UEFI boot mode, not the 35 year old BIOS/CSM/Legacy mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

See link below in my signature for UEFI install info & more links.
If issues then post back with a specific issue.

I put / in a 25GB partition on SSD leaving room for another / or two and some data, but have data on HDD which I also configure with gpt. And first two partitions on both drives are the ESP for UEFI boot and a bios_grub for BIOS boot  in case I do want to experiment.

 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 



If new user easier to put /home on HDD. If you use a data partition then you have to configure mount, owership & permissions, where a /home does all that automatically. But evenually you may want more data or other partitions and will need to learn mounting of partitions.

---

### Post by eera5607 on 2017-06-28
Thank you very much for your complete answer. It is not the first time that I install Ubuntu but it is the first time on a SSD. In fact, I was planning to put / in a 25 GB partition (? maybe more. It is a 500 SSD and I will probably be good with Ubuntu alone (no other distributions nor Windows)) and /home and /tmp on the HDD. I found your guide very entertaining and useful. As you well indicate, if I use UEFI mode both have to be configured with gpt and there I get a little confused. In what point (of the installation) do I get to choose gpt or mbr? I mean, do I need to run a live system and use Gparted or it is ok to use the installation wizard to create the partitions? BIOS let me choose to activate CSM - UEFI Compatibility Support Module but I'm not sure if with that option enabled I need to use mbr o gpt. Thanks again for your help.

---

### Post by oldfred on 2017-06-28
I prefer to partition in advance with gparted and first thing in gparted choose gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 

If you activate CSM that is BIOS boot.
But how you boot installer UEFI or BIOS is then how it installs. And then you have to have system set to boot in that same boot mode, or it does not work.
If you boot installer in BIOS/CSM mode, it will default to MBR partitioning unless drive is over 1.5TB and blank. So best to partition in advance if you want gpt. 
Installer does not give any option for MBR or gpt.

With a larger drive and no plans to use all of drive immediately, I like to just leave some space unallocated. I make sure ESP & bios_grub are first two partitions as those will never change, unless you make ESP way too small. And I put swap as last partition, as it will not normally change. Then none of those partitions get in the way if later I to increase one, or add another partition.

---

### Post by eera5607 on 2017-06-29
Thank you very much again. I now understand. I definitely want to use UEFI mode not CSM so now I know that the installer will use GPT partitioning not MBR by default. I was confused basically because of the explanation given in the BIOS. Now I know that the best way to proceed in my case (one OS (Ubuntu) on one drive (SSD)) would be AHCI and CSM disabled.   Now I attach two pairs of images showing why I was confuse. Specially with the CSM explanation at the bottom of the first screenshot. Thanks again. 
[IMG]http://i.imgur.com/oXLZmv9.png[/IMG]

[IMG]http://i.imgur.com/tXKAvrp.png[/IMG]

[IMG]http://i.imgur.com/ZPNrYeB.png[/IMG]

[IMG]http://i.imgur.com/tkIap1M.png[/IMG]

---

### Post by oldfred on 2017-06-29
Please attach screenshots or photos.
Easy to do with Forum's advanced Editor and paperclip icon.

One of my systems had the turn on UEFI mode, under the CSM tab and new menu screen. Which seemed backwards, somehow.

Many want to install the now older Windows 7, but its DVD is BIOS only. It has to be converted to flash drive and files moved/renamed to make it UEFI bootable. And Windows 7 does not support UEFI Secure Boot at all.
Ubuntu supports UEFI secure boot, but you cannot then use any proprietary drivers that are binary blobs. And currently cannot from grub boot Windows with Secure boot on. Only from UEFI boot menu.

---

### Post by eera5607 on 2017-06-29
Thanks. Now I attached the screenshots the usual way. Please refer to the first screenshot. As far as I understand, in this BIOS you can turn CSM on and keep using UEFI. That's was the thing that confused me (Is that what Auto Mode means?). And yes, I was also reading about the issue with some proprietary drivers using UEFI mode, maybe it has to the with Ubuntu not being able to verify a certificate or a signature, I don't know. But I can always use the open source version I think. Thanks again.

---

### Post by oldfred on 2017-06-29
Not sure with your system.
A few actually want CSM on and boot in UEFI mode. 
Most need CSM off and then either Secure boot on or off for UEFI boot.

And boot of hard drive is totally separate from boot of flash drive or DVD. So how you boot install media UEFI or BIOS may install a system that does not boot as system is not set to boot in same boot mode as install. Many threads where users install in UEFI and try to boot in BIOS or install in BIOS and try to boot in UEFI mode.

My Asus Z97 would only boot USB flash drive in UEFI mode with UEFI only setting on USB. Even UEFI first only booted in BIOS/CSM mode.

       Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)
Since my UEFI update resets most of my UEFI settings I have to keep a list (and screen shots).
I enable USB support,USB to full, Next boot after power to full, UEFI only, network boot to ignore, boot storage drives to UEFI, os type to Other (this is really Secure Boot), fast boot has setting that allows a 3 second delay which I set, so even with warm reboot I may have time to get into UEFI or one time boot of my flash drive.

---

### Post by eera5607 on 2017-06-29
Ok, I understand your procedure. Maybe I'm over complicating, now I think I'm clear with the BIOS configuration and going to start testing. Thanks again for all your help, very complete answers. I'll get back to you in case I encounter any issue during the process. :)

---

