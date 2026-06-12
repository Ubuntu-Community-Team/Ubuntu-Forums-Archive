---
title: "Restore Win 8.0, upgrade to 10, and dual boot Ubuntu"
date: 2016-03-05
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2016-03-05
My wife's computer runs 12.04, soon to be upgraded. When we bought the computer, it had Win 8.0 and she hated it (no middle ground with her. She flat-out hated it.) So I just installed Ubuntu 12.04 fall-back over it. That was before 8.1, which I consider a significant improvement over 8.0, and more importantly, the free upgrade (during the current one-year long offer period) to Win 10, which gets pretty good marks from most of what I read.

So I plan to restore 8.0, upgrade it to 10, then install 16.04 in April or May as a dual boot. Reason for this post has mainly to do with the dual boot side of this. It is a UEFI BIOS, so I want to better understand what measures I should take, and when, to allow for any UEFI issues?

I expect nothing needs to be done in this respect until the dual-boot install, but thought it might be a good idea to throw it out there now in case earlier steps need to be taken?

Would a description of SSD and HDD and all partitions be helpful in responding? (Haven't included here already because screenshot is broken under fall-back and I will need some guidance. It isn't too much info to retype if needed, but don't want to spend time on it if not useful.)

---

### Post by Bucky Ball on 2016-03-05
> **Odyssey1942 said:**
> 
I expect nothing needs to be done in this respect until the dual-boot install ...

You expect right. Take care of the Windows install and upgrade first, get that up and running, then we'll get to it. Nothing really to add. As far as I know you can install Windows in BIOS or UEFI. That is up to you and would dictate which method of installing Ubuntu you would research.

At this point, a description of partitions would be redundant as your question is "... what measures I should take, and when, to allow for any UEFI issues?" Doesn't make much difference what you have on there now as you are about to install Windows and probably change things around and doesn't effect whether you boot in UEFI or not.

---

### Post by Odyssey1942 on 2016-03-05
Sounds good.

I mentioned it now because it occurred to me that since her /home directory is already on her HDD in an EXT4 partition, that I might want to preserve it (yes, and having backed it up), which might dictate using all the existing partitions and their formats. I would not expect to get much guidance from a Windows forum that would be useful in anticipating the later stage linux install, and so this seems a better place to discuss a comprehensive plan.

---

### Post by yancek on 2016-03-05
The official Ubuntu documentation on dual booting UEFI with windows at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by vidtek on 2016-03-06
Odyssey-
Just do the windows install, leaving enough room for your linux stuff later.
I would choose UEFI for future-proofing and allow windows to partition the drive as it wants, then when you have windows 10 running as you want you can resize the drive to give yourself room for Linux.
Don't worry about linux and UEFI, as from Ubuntu 15.04 you shold have no difficulties with dual-booting windows and linux in UEFI.

Cheers, Tony.
Yancek-  That link is broken.

---

### Post by oldfred on 2016-03-06
If bit older hardware with UEFI, be sure to update UEFI/BIOS from vendor. They also had fixes for many issues when first using UEFI.

If drive is gpt partitioned, Windows will only boot in UEFI mode.
If drive is now MBR, Windows will only boot in BIOS mode, or you have to convert to gpt for UEFI.
All drives should be the same gpt or MBR.
But Ubuntu can boot from gpt with BIOS, so if Ubuntu not on Windows drive or second drive is only data, often better to use gpt partitioning whether Windows is BIOS or UEFI.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Odyssey1942 on 2016-03-06
Great. UEFI guidance noted. thanks.

I am assuming that during the Windows install the EXT4 might/will get reformatted to NTFS (or whatever MS uses these days) which will necessitate a repopulation of /home after the series of Win 8.0 reinstall and the Win 10 upgrade / U 16.04 install steps. Not being comfortable in the CLI, I prefer a GUI backup/copy of /home with the plan that it will be used to repopulate.

My reading/research on backup leads me to BackInTime, but I am happy to hear other GUI ideas (just don't know how to create scripts, get them to run automatically, etc.) 

From other threads, I understand that it is better not to restore the 12.04  system configuration directories since they might conflict with the new 16.04 install files. 

Any guidance on what needs restoring (I assume all data directories) and what does not?

---

