---
title: "Installing Ubuntu on a newer laptop with UEFI with secure boot."
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by irv on 2014-04-01
I have a few questions on installing Ubuntu on a newer laptop with UEFI with secure boot.
The questions aren't on installing as much as getting Windows 8 and Ubuntu to play nice with each other. First, I am not new to Ubuntu. I have been using it since 2005 and have it installed on my server and desktop.
When I turn off secure boot and install Ubuntu everything goes okay but when I boot it will only go into Ubuntu. For some reason the grub does not setup right. (by the way I was installing in 12.04 at that time). Now for the questions.
Does anyone know if 14.04 fixed the problem with the grub? And if not will there be a work around to install it on the newer laptops? Also, will 14.04 support secure boot? And one more question. Will 14.04 work on ARM PCs because there is no control over the secure boot?
I have been holding off on installing ubuntu on my Asus 3632QM i7 2.20Ghz 8GB laptop so I am hoping some of these issues have been address.  I would love to try to install it on a Asus Transformer 300T but I have no idea where to start or if it is even possible. 
Right now I run 13.10 in a virtual machine or just boot with a USB drive. Here is a screenshot of it running on this laptop.
[ATTACH=CONFIG]251644[/ATTACH]

---

### Post by sudodus on 2014-04-01
> **irv said:**
> I have a few questions on installing Ubuntu on a newer laptop with UEFI with secure boot.
The questions aren't on installing as much as getting Windows 8 and Ubuntu to play nice with each other. First, I am not new to Ubuntu. I have been using it since 2005 and have it installed on my server and desktop.
When I turn off secure boot and install Ubuntu everything goes okay but when I boot it will only go into Ubuntu. For some reason the grub does not setup right. (by the way I was installing in 12.04 at that time). Now for the questions.

I'll to reply to a few of your questions ...
> 
Does anyone know if 14.04 fixed the problem with the grub? And if not will there be a work around to install it on the newer laptops?

I have recently installed 12.04.4 LTS, and it has improved a lot concerning UEFI compared to earlier point versions. See this link of an installed (grub based) system for USB, that can boot in UEFI as well as BIOS mode.
[URL="http://ubuntuforums.org/showthread.php?t=2213631"]
Portable installed system that boots in UEFI as well as in BIOS mode[/URL]

I think all current Ubuntu versions have improved. The best work around I can think of is Boot-Repair according to this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

> 
Also, will 14.04 support secure boot?

This part is edited:

1. I think so for 14.04 LTS. 
I tested an install USB drive (made from the 64-bit desktop iso file) and it will boot my Toshiba in secure mode.

2. and also for 12.04.4 LTS
2.1 I tested an install USB drive (made from the 64-bit desktop iso file) and it will boot my Toshiba in secure mode.
2.2 I tested also my Ubuntu 12.04.4 pendrive, and the computer complains in secure mode and stops, so probably I missed something when making the pendrive. It works in UEFI mode but not with secure boot.
> 
And one more question. Will 14.04 work on ARM PCs because there is no control over the secure boot?

I don't know. [COLOR=#ff0000]Let us hope someone who knows chips in and tells us[/COLOR] :-)
> 
I have been holding off on installing ubuntu on my Asus 3632QM i7 2.20Ghz 8GB laptop so I am hoping some of these issues have been address.  I would love to try to install it on a Asus Transformer 300T but I have no idea where to start or if it is even possible. 
Right now I run 13.10 in a virtual machine or just boot with a USB drive. Here is a screenshot of it running on this laptop.
[ATTACH=CONFIG]251644[/ATTACH]

---

### Post by oldfred on 2014-04-01
Did forum create duplicates or did you post three times in two minutes? 
Forum has been intermittent slow then ok for me. 
Closed other threads.

Do not know about ARM systems, most are locked down. Some have new UEFI class 3 which is only UEFI with no BIOS. 

You can install with secure boot since 12.04.2, but usually best not to have secure boot on. Grub does now have bug with 8.1 as it will not boot Windows from grub menu if secure boot is on.

Did you install Ubuntu in UEFI mode not BIOS/CSM?
Grub2's os-prober also had a bug where it only created BIOS type chain load entries with UEFI. Those do not work as you must chain to efi partition not directly to Windows install like BIOS does.

You cannot dual boot from grub menu unless both systems are UEFI. UEFI & BIOS are not compatible and once you start booting in one mode you cannot change. Or you cannot use a grub in Ubuntu in BIOS to boot WIndows in UEFI.

Both vendors & Linux are making major UEFI fixes. Intel added many kernel, support software & video driver updates to Linux and many are in 14.04. So if you have a new system with Haswell 14.04 may be a lot better. And even third gen Intel chips may work better with 14.04 as the updates help across the board.  Some of the fixes for the next gen Intel chips due in a couple of months are in newer kernels, but not yet in standard distributions yet.

---

### Post by sudodus on 2014-04-01
Hi oldfred,

I had some strange errors too with the UF page when trying to edit my post (editing about booting in secure mode after testing).

---

### Post by ubfan1 on 2014-04-01
There are some Transformer threads over on xda-developers. Try starting at:
[http://forum.xda-developers.com/wiki/ASUS_Eee_Pad_Transformer/How_to_install_Ubuntu](http://forum.xda-developers.com/wiki/ASUS_Eee_Pad_Transformer/How_to_install_Ubuntu)
My install last year on a Toshiba i7 3630QM had no problems even with secure boot on, other than not being able to boot Windows from the grub menu (bug 1091464) but I finally turned off secure boot after 9 mo, and then even the grub boot worked.

---

### Post by irv on 2014-04-03
> **oldfred said:**
> Did forum create duplicates or did you post three times in two minutes? 
Forum has been intermittent slow then ok for me. 
Closed other threads.

Do not know about ARM systems, most are locked down. Some have new UEFI class 3 which is only UEFI with no BIOS. 

You can install with secure boot since 12.04.2, but usually best not to have secure boot on. Grub does now have bug with 8.1 as it will not boot Windows from grub menu if secure boot is on.

Did you install Ubuntu in UEFI mode not BIOS/CSM?
Grub2's os-prober also had a bug where it only created BIOS type chain load entries with UEFI. Those do not work as you must chain to efi partition not directly to Windows install like BIOS does.

You cannot dual boot from grub menu unless both systems are UEFI. UEFI & BIOS are not compatible and once you start booting in one mode you cannot change. Or you cannot use a grub in Ubuntu in BIOS to boot WIndows in UEFI.

Both vendors & Linux are making major UEFI fixes. Intel added many kernel, support software & video driver updates to Linux and many are in 14.04. So if you have a new system with Haswell 14.04 may be a lot better. And even third gen Intel chips may work better with 14.04 as the updates help across the board.  Some of the fixes for the next gen Intel chips due in a couple of months are in newer kernels, but not yet in standard distributions yet.
Yes it was me Oldfred, For some reason I waited and waited and it seemed that my computer was not responding so I clicked on the Submit Post, and again it sat there. I think it was the third time that I had to wait for (like 7 second to submit my post) so I waited again and re-submit it again.
Now on to UEFI problems. Since these new systems have come out, it sure makes it hard to boot with more then one OS. I didn't want to take Windows 8.1 off my laptop. (I did an install, trying to get both OS' booting and running off one hard drive, and ended up reinstalling Windwos 8 then upgrading to 8.1 again). So I went a different avenue. I just booted from a USB by turning off Secure Boot and booting off the live OS. Now what I plan on doing is installing it on a SSD via a USB, and booting off it and run Ubuntu 14.04 that way. This way I can save all my installs and settings. I order a SSD 32gig and it should be here sometime today. I have a case with a SATA to USB connection. From everything I have read I see this is better then using a USB thumb drive. Here is what I read:
> While SSDs cost a lot more than USB flash drives, they are also more reliable. Both types of drives use NAND flash memory to store data, but not the same kind. USB flash drives use multi-level cell memory, which is much cheaper to produce than the single-level cell memory used in SSDs. The MLC memory used in USB flash drives can store 2 bits of data for every cell, resulting in larger possible storage capacities. In fact, some hybrid SSD drives use MLC memory to increase their storage capacities up to 1GB. While SLC memory does not allow for such large storage capacities, it endures much better than MLC memory. Generally speaking, you can only read or write data to a MLC memory cell about 5,000 times. SLC increases the number of possible read/write cycles to about 50,000. The controller boards found in SSDs support wear leveling, which helps to spread read/write operations across more of the cells in the memory chips to make the drives last longer. Controllers in SSD drives also enable advanced hard drive features, such as native-command queuing that optimizes read/write requests and SMART, which enables the computer BIOS to monitor the drive in real time for potential anomalies of problems. There are many other technical reasons why SSDs perform better and are more durable than USB flash drives. However, the bottom line is that SSDs are faster and more reliable than USB flash drives.
To be honest with you, booting the live USB on this laptop is almost as fast as booting and running off the hybrid that that Windows is running on. When I get it all setup I will post how things went and some speeds. This i7 processor, 8 gig of RAM and SSD should run fast even through a USB port. (USB 3).

---

### Post by oldfred on 2014-04-03
Do not know about SSD with USB3 port, but it still should be pretty fast.

I have a 64GB flash drive in my Desktop with two / (root) partitions, one for current 12.04 and one soon for new working 14.04. All my data is in two data partitions on rotating drive, one NTFS (still) from when I ran XP and one Linux formatted for all new data.

While a flash drive, you install could be similar, you may not need BIOS, but then could use SSD on older system also.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

You will want gpt partitioning, efi partition on SSD and make a few settings to reduce writes. 
I used ext4 but turned off journal. Some say now that even that is not needed.
I also use a script for trim which I understand 14.04 will implement automatically. Mine is daily but Ubutu's seems to be weekly.
I also changed to noatime in fstab, but one or two apps may have issues. Another althernative is relatime.

---

