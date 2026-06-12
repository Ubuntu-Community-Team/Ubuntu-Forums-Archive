---
title: "Problem booting ubuntu 13.10 on Lenovo G505S"
date: 2014-03-22
forum: Installation &amp; Upgrades
---

### Post by martinet2 on 2014-03-22
Hello everyone,

I just got a LENOVO G505S with Windows 8 installed on it. But, since i wanted only Ubuntu, i decided to erase it and downloaded Ubuntu 13.10 in a USB. 
I changed EFI to Legacy, so i could choose to boot on my usb. The installation went well, but when i restarted, i got a purple screen and... nothing!
Even, when i hold SHIFT, i get nothing but this purple screen.

I tried the Boot-Repair on my Ubuntu live-USB but still the purple screen... again!
Here is my Boot-Info if it can help: [B]paste.ubuntu.com/7136211.

Thanks![/B]

---

### Post by ubfan1 on 2014-03-22
So looks like you converted the gpt disk to msdos partitioning and did a standard install.  Only odd things are the boot  flag on the extended partition (which Ubuntu should not care about anyway), and the core.img statement looking at "partition 94"? (but I'm not that familiar with what the normal words are).  Anyway, could be a leftover gpt partition table causing some confusion on disk.  Can you invoke the efi menu to select devices/OSes and see ubuntu?  If you get to a grub command prompt (off live media), can you see the hard disk and its files?  With some typing, at the grub prompt, can you boot the hard disk? (See the grub.cfg file to see what to type, not pleasant, but something to try).

---

### Post by martinet2 on 2014-03-23
Hey, thanks for the answer!
I didn't tried the EFI menu! But i did try to re-install ubuntu 13.10, only this time with 'nomodeset' on (as i read somewhere on this forum). And there's something new! Now, when i start my computer i get this on screen:
```
error: file '/boot/grub/i386-pc/normail.mod' not found.
Entering rescue mode...
grub rescue>
```

Any idea of what does that possibly mean? My guess is the grub is wrongly installed!!? Because, i do have the 'grub' repertory but not the 'i386-pc' one!

---

### Post by fantab on 2014-03-23
> **ubfan1 said:**
> So looks like you converted the gpt disk to msdos partitioning and did a standard install. ... could be a leftover gpt partition table causing some confusion on disk.

ubfan1 is probably correct. Windows8 is usually shipped with UEFI machines and is pre-installed accordingly. To be able to utilize UEFI, GUID Partition Table [GPT] is a must. So your HDD most likely was partitioned with GPT.
[GPT has many advantages]("https://wiki.archlinux.org/index.php/GUID_Partition_Table"). It is recommended that you stay with UEFI and GPT.

UEFI is a replacement for older BIOS. 
You have installed Ubuntu in a 'Legacy/BIOS' mode, with 'msdos/MBR' Partition Table. When the change from GPT to MBR happens there is back up GPT table which is left over on the HDD. And this backup table confuses GRUB.
[Fixparts]("http://www.rodsbooks.com/fixparts/") can effortlessly fix this.
Also check in your UEFI/BIOS menu to see what mode is it booting in, UEFI or 'Legacy/BIOS/CSM'... 

However, I suggest that you go UEFI way with GPT. UEFI interacts better with newer hardware.
Re-Format your HDD as a GPT drive;
Create first partition as ESP [EFI System Partition] of about 200-500Mb - FAT32 - 'boot' flag.
Install Ubuntu.
Or create more partitions as instanced below:
25Gb Primary Ext4 Ubuntu /
25Gb Primary Ext4 Free
2-4Gb Primary SWAP 
'All the remaining Gb' Primary Ext4 /home (or just a simple ext4 'data' partition).
Boot Ubuntu USB/DVD in EFI mode only:
Install Ubuntu - At the 'Installation Type' dialog choose 'Something Else' option. Select the partition you want to install Ubuntu to, say first 25Gb partition, and set it up with following:
Use as= Ext4 journaling system
Mountpoint= /
Format= yes

Similarly set up /home, just choose '/home' as mountpoint.
Continue with installation.

Regarding 'nomodeset': 'nomodest' boots the OS in 'failsafe graphics' mode and only temporarily for the booted session. If you reboot you will have to append 'nomodeset' again to the kernel line.
Once you install Ubuntu and connect to the Net then you can install proper drivers.

By the way, what graphics card(s) do you have on your machine?

---

### Post by martinet2 on 2014-03-23
Thanks for this reply! I'm beginning to understand why it's not working!

Graphic card: AMD RADEON HD 7640G and Proc is AMD A8 4500M!

Since GPT is a table introduced by Intel, won't it be a problem with my AMD configuration!?

---

### Post by fantab on 2014-03-24
Both GPT and UEFI are Standards. All different manufacturers follow it. So it makes no difference which manufacturer's product you choose.

I don't have Radeon graphics so I don't know how it fares... you can search this forum or web and see what solutions users have followed.
You can use 'nomodeset' until you install Ubuntu, then in 'System Settings' you'll find 'Additional Drivers'... Select the appropriate driver to activate it.

---

### Post by martinet2 on 2014-03-24
Sorry for the late reply! Anyway, your solution worked very well! I did exactly like you said and now i can use my computer!
You're my hero lol! 
Thanks again! :)

---

### Post by fantab on 2014-03-24
I'm Glad that you have installed Ubuntu and able to 'use your computer'.

Did you use 'fixparts' or did you install in EFI mode?

---

### Post by martinet2 on 2014-03-25
In fact, i didn't used Fixparts at all. I went directly to this point:
> **fantab said:**
> 
Re-Format your HDD as a GPT drive;

And i did it with [http://gparted.org/](http://gparted.org/) because i had it on hand. Then, i installed Ubuntu in EFI mode.

---

### Post by fantab on 2014-03-26
Excellent! you've made a right choice.

---

### Post by frank18 on 2014-03-26
> **martinet2 said:**
> Hello everyone,

I just got a LENOVO G505S with Windows 8 installed on it. But, since i wanted only Ubuntu, i decided to erase it and downloaded Ubuntu 13.10 in a USB. 
I changed EFI to Legacy, so i could choose to boot on my usb. The installation went well, but when i restarted, i got a purple screen and... nothing!
Even, when i hold SHIFT, i get nothing but this purple screen.

I tried the Boot-Repair on my Ubuntu live-USB but still the purple screen... again!
Here is my Boot-Info if it can help: [B]paste.ubuntu.com/7136211.

Thanks![/B]

I don't understand why people keep going to ubuntu 13.10! which if you check the forum threads you see that it only has bugs and problems why not either use Ubuntu LTS as 12.04 or now 14.04 and keep it simple not to invent stuff, since i started to do this i had no issues whatsoever, first check if your hardware can handle this or that distro then install  from iso image, not upgrades,some people start to use software that doesn't  belong to this distro for the simple fact that it makes it pretty and pretty doesn't mean efficient,if you're not an expert on  testing or building an OPS then stick with stuff that is built from the images available,since i started to use this way i never had  problems with my OPS.

---

