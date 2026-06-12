---
title: "grub2 with 2 disks drives"
date: 2016-08-06
forum: Installation &amp; Upgrades
---

### Post by pepinillofordewin on 2016-08-06
hi, i'm planning install ubuntu and use it with windows, but windows in one drive and ubuntu in other, both in the same pc, but i'm not sure of what can happen with the grub menu. It's ok if i do?

---

### Post by Bashing-om on 2016-08-06
pepinillofordewin; Hello;

> **pepinillofordewin said:**
> hi, i'm planning install ubuntu and use it with windows, but windows in one drive and ubuntu in other, both in the same pc, but i'm not sure of what can happen with the grub menu. It's ok if i do?

Sure it is OK .
However, might I suggest that grub be installed to the drive that contains ubuntu - leave Windows alone. That way you have the choice of which drive boots .
Setting the boot priority to boot ubuntu's drive; boot into ubuntu and one can then chainload Windows onto the grub boot menu.
In terminal execute:
```

sudo apt update
sudo apt upgrade
sudo update-grub 

```

This way .. if ubuntu is broke for some reason .. you can still independently boot Windows .

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by pepinillofordewin on 2016-08-06
thanks a lot :D , i will start the instalation now (local time 2:25 xD)

---

### Post by pepinillofordewin on 2016-08-06
so... question, is advisable update the grub when install ubuntu? i usually only do the 2 other commands

---

### Post by Bashing-om on 2016-08-06
pepinillofordewin; Well ..

Yes and no for the update/upgrade.
IF one chooses to have the installer do the updates ( check box ) then the updates "should" have been done ...
Me I am not the trusting type .. I want to see .
so I always always as soon as the install completes check and install all updates.

Update/upgrade is the very 1st action .

[INDENT][INDENT]redundancy can be a good thing
 [/INDENT][/INDENT]

---

### Post by pepinillofordewin on 2016-08-08
thanks for the info, i will follow your example, but one other question: what's the difference between apt & apt-get? i always done sudo apt-get upgrade/update, but only apt is also valid.

P.D: Ubuntu successfully installed, the only issue is an "D: disk need to be analysed" when i boot from windows

---

### Post by Bashing-om on 2016-08-08
pepinillofordewin; Hey;

As to 'apt', It is the rewritten 'apt-get'.
See:
[https://www.reddit.com/r/linux/comments/26q2sm/apt_vs_aptget/](https://www.reddit.com/r/linux/comments/26q2sm/apt_vs_aptget/)
[http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/](http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/)
[https://mvogt.wordpress.com/2014/04/04/apt-1-0/](https://mvogt.wordpress.com/2014/04/04/apt-1-0/)

Now your D: drive is an alternate operating system .. though linux has some light tools to deal with the Windows operating system they are not even close to what native Windows can do for you . I highly suggest that you look/repair that file system from Windows.

One thought ... we often see that in Windows it is often "hibernated" ( fast boot !) .. such that Windows still has control of the file system on that drive. As such 'buntu will not interfere with Windows operations and will not mount the file system.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by yancek on 2016-08-08
> P.D: Ubuntu successfully installed, the only issue is an "D: disk need to be analysed" when i boot from windows 				

What you do depends upon what is on D.  I've never known a windows system to assign a drive letter by default to a Linux partition and usually (even with windows 10) the only way you can see that a partition is there is in something like Disk Management.  If it's a windows partition, probably run chkdsk.

---

### Post by ubfan1 on 2016-08-08
Is this a UEFI machine?  If so, maybe D's the disk's EFI partition.  Is the second disk "removable" like USB?  If so, check that the second disk's /EFI/Boot/bootx64.efi is a copy of grubx64.efi (check sizes against /EFI/ubuntu/grubx64.efi), or is a copy of shimx64.efi with grubx64.efi also present.  bootx64.efi is the default bootloader used on removable media, and the grub installer might not set it up correctly.  Manually running grub-install with the --removable switch will work, using a copy of grubx64.efi for bootx64.efi, but adding the --uefi-secure-boot did not correctly use shim, last time I looked.

---

### Post by pepinillofordewin on 2016-08-09
in order: it's a windows 7 so should not be problems with "fast boot", but anyway I&#8217;m actually disabled the hibernate option cause it&#8217;s installed on SSD. I ran the chkdsk /f and the issue still there, is not an option that windows say that like do ever that i put an usb connected previously in Linux? And last, but not least, the ubuntu #f1 fan: i am studding computing, but that pass my level, so many consonants xD . the things that i understand and can answer  (i need more English lessons also) are: the machine use ahci (i think you look for that, but i'm not sure), D it's an integrated HDD, and even if it is not necesary, i checked and there no EFI folder in the root directory

---

### Post by pepinillofordewin on 2016-08-09
well, thanks a lot for the info but in 2-3 hours i'll go to a village without internet (the nearest is like 10Km) from holidays, so i'll can't reply in 1-2 weeks. sorry for let the thread thereby, but i can't do anythig. thanks again and... [*"Hasta la vista, baby"*]("http://www.youtube.com/watch?v=LRxaXmXvjnU")

---

