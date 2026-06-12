---
title: "Installation issue trying to install alongside Windows 7"
date: 2015-03-16
forum: Installation &amp; Upgrades
---

### Post by DrZoo on 2015-03-16
I'm trying to install Ubuntu 14.04.2 alongside my Windows 7. I have 50 GB of unallocated space made by using the Windows Disk Management. Whenever I boot to the Ubuntu Desktop DVD I choose install. However I never get the option to install alongside Windows. Whenever I choose to continue and create my own disk partitions, the list just shows 1 partition of 750 GB (full size of my disk). It does not show my 50 GB of unallocated space or anything. I've tried looking into a few things, but I've had no luck. 

I can't get it to make a logical partition or make it into "free space" either. Each time I format the unallocated space it becomes an NTFS primary partition. 

If anyone has any insight or help, it would be greatly appreciated.

Thanks!

---

### Post by Bucky Ball on 2015-03-16
Welcome. Are you booting Windows in UEFI? If so, you need to switch off fastboot/smartstart, can't remember what it's called. You may need to go to the BIOS to do that.

Problem is that Windows hibernates with it on and you can't do much.

* Perhaps try [this]("http://sourcedaddy.com/windows-7/using-quick-boot-feature-of-bios.html"), but in reverse because you want it off, not on. ;)

---

### Post by DrZoo on 2015-03-16
I went into the BIOS and checked a few things. The laptop originally came with Windows 8, but I wanted to use my Windows 7 instead. So I changed it from UEFI to "Legacy Support" boot. The deep sleep feature is disabled as welll. I'll take a look at the link you shared and see if it leads to any breakthroughs.

---

### Post by Bucky Ball on 2015-03-16
The Ubuntu install media is set to Legacy also? If Win is installed in legacy, Ubuntu must be also. And same with UEFI. They both must be installed in the same mode.

All pre-installed Win8 are UEFI, so maybe there's a setting left over from that. There is also something you can switch off in Windows. Sorry, not au fait with Win so can't be more specific, but you need to boot into Windows to tweak that setting. That might be fastboot (which basically means 'hibernate'). If the Win partition is hibernating, it won't be seen by the Ubuntu installer. 

When you do get there, choose 'Something Else' at the partitioning section of the Ubuntu install and create partitions manually. We can give you a hand with that. ;)

---

### Post by DrZoo on 2015-03-19
I believe that there is two options when booting to my optical drive. One being legacy and the other being UEFI. I'll give that a shot this weekend. Thanks for you input

---

### Post by ubfan1 on 2015-03-20
You should also have run chkdsk a few times on the resized Windows partition.  If you didn't, that might be causing some problems.

---

