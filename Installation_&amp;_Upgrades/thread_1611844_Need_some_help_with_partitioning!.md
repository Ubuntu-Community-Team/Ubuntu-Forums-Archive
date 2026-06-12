---
title: "Need some help with partitioning!"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by na5h on 2010-11-02
Hi! I'm helping a friend out with a dual-boot installation. The hard-drive has Ubuntu 10.04 on it (it is the only OS on the hard-drive), and he wants to install Windows 7 on it as well. Could somebody please give me some step-by-step instructions on how to set up an NTFS-partition to install Windows on?

---

### Post by Megaptera on 2010-11-02
Hope this helps:
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

Note this though:
##This guide does not work for Karamic or future releases, For that see page 14 and follow the link provided by presence1960 for how to dual boot with Grub2 (requires some reading)

---

### Post by na5h on 2010-11-03
Thanks! :) Your thread gave me a better overall picture...but what I actually need help with is how to do the partitioning itself (what to do/click when I use gparted or disk utility). I've done some partitioning before, but I'm not 100% sure about what to do if I want to turn part of an ext4 (ubuntu) hard-drive into NTFS. Am I supposed to shrink the hard-drive and then create a new partition somehow...or something like that??? :confused:

---

### Post by Quackers on 2010-11-03
Does Ubuntu 10.04 occupy the whole disc? If there is no free space (unallocated) you will need to resize the Ubuntu partition. This should not be done while Ubuntu is running (for safety reasons). I would recommend using Gparted Live CD, which you boot from then do the changes.
I would recommend that you first backup your /home partition to external media as any partition changes carry a risk!

---

### Post by na5h on 2010-11-03
Yes, the whole hard-drive is Ubuntu 10.04... so there is no unallocated space. What exactly is it that I should do with gparted from the livecd (resize, shrink, etc)? I can create an NTFS-partition without having to format the whole hard-drive, right?

---

### Post by na5h on 2010-11-07
bump!

---

### Post by Quackers on 2010-11-07
Boot from the GParted Live cd or from the Ubuntu live cd and run Gparted. Select the Ubuntu partition and choose re-size, then select the appropriate sizes and click on the green tick in the toolbar to apply the changes. Then boot the Windows disc and choose to install to the new unallocated space.
As Windows is being installed after Ubuntu you may need to install EasyBCD or something similar to get the choice of which OS to boot from rather than just being able to use grub for that.

---

### Post by na5h on 2010-11-07
Thank you very much for your help...I will try it out!!! :P Do you think it will be enough if l just reinstall GRUB2 after the Windows installation? I already know how to do that part.

---

### Post by Quackers on 2010-11-07
If Windows is installed first, then grub will give you a grub menu to choose OS from. However, if Windows is installed second I believe you will need a program such as EasyBCD to do that. I'm not 100% sure, but this seems to be the consensus of what I've read. Maybe somebody else could confirm or deny this for you.

---

### Post by na5h on 2010-11-07
> **Quackers said:**
> Boot from the GParted Live cd or from the Ubuntu live cd and run Gparted. Select the Ubuntu partition and choose re-size, then select the appropriate sizes and click on the green tick in the toolbar to apply the changes. Then boot the Windows disc and choose to install to the new unallocated space.
As Windows is being installed after Ubuntu you may need to install EasyBCD or something similar to get the choice of which OS to boot from rather than just being able to use grub for that.

Thank you very much for your help...I will try it out!!! :razz: Do you think it will be enough if l just reinstall GRUB2 after the Windows installation? I already know how to do that part. (Sorry for the double-reply...I haven't figured out how to delete one of them)

---

### Post by na5h on 2010-11-07
> **Quackers said:**
> If Windows is installed first, then grub will give you a grub menu to choose OS from. However, if Windows is installed second I believe you will need a program such as EasyBCD to do that. I'm not 100% sure, but this seems to be the consensus of what I've read. Maybe somebody else could confirm or deny this for you.

Thanks again! :) I've understood that you can reinstall grub2 from the livecd. It's needed "when the MBR of the booting device is altered and GRUB2 is removed, such as when Windows is installed after Ubuntu".

---

### Post by uRock on 2010-11-07
I'd back up data, then start a new partition table with Has the Windows partition 1st, then create the / partition, then creat a logical partition for the rest of the disk, then create the /home and swap partitions within the Logical partition.

If you don't want to delete partitions, then you can use the Ubuntu LiveCD or any other up to date partitioning disk to shrink the Ubuntu partitions enough to get whatever size is planned for the NTFS partition at the beginning of the disk.

Either way, backups of data are a must.

---

### Post by na5h on 2010-11-07
> **uRock said:**
> I'd back up data, then start a new partition table with Has the Windows partition 1st, then create the / partition, then creat a logical partition for the rest of the disk, then create the /home and swap partitions within the Logical partition.

If you don't want to delete partitions, then you can use the Ubuntu LiveCD or any other up to date partitioning disk to shrink the Ubuntu partitions enough to get whatever size is planned for the NTFS partition at the beginning of the disk.

Either way, backups of data are a must.

Ok! Thanks! :)

---

### Post by oldfred on 2010-11-07
Make sure the NTFS partition is a primary partition or windows will not see it. You can/should put a boot flag on it also. Windows uses boot flag to know what partition to boot. Grub does not use a boot flag but some BIOS require a boot flag on a primary partition (they only assume windows).

You can reinstall grub2 and after booting run 

```
sudo update-grub
```

That will rescan entire system for new operating systems and add them to your menu.

---

### Post by srs5694 on 2010-11-08
> **oldfred said:**
> Make sure the NTFS partition is a primary partition or windows will not see it.

Windows must *boot* from a primary partition (or at least have one involved in the boot process for some critical files), but Windows can *see* logical partitions just fine.

> You can/should put a boot flag on it also. Windows uses boot flag to know what partition to boot.

This isn't necessary with most recent versions of Windows, at least if GRUB is in the MBR. Earlier versions of Windows (9x/Me) wouldn't boot unless the boot flag was set, but modern versions are fine without it. IIRC, anything based on NT, including XP and later, doesn't need the boot flag set.

---

### Post by oldfred on 2010-11-08
> Windows must *boot* from a primary partition (or at least have one involved in the boot process for some critical files), but Windows can *see* logical partitions just fine.Correct and a few here have even made XP boot from a logical partition with lilo directly or with grub, even though windows boot loader does not support it.

> This isn't necessary with most recent versions of Windows, at least if  GRUB is in the MBR. Earlier versions of Windows (9x/Me) wouldn't boot  unless the boot flag was set, but modern versions are fine without it.  IIRC, anything based on NT, including XP and later, doesn't need the  boot flag set.     If your are using grub to boot you do not have to have a boot flag, but some BIOS will not let anything boot unless there is  a boot flag on a primary partition. Both the windows boot loader and Lilo use the active partition (boot flag) to know what partition boot sector to load next. Windows only seems to want to repair the active partition, so we need the flag if we have to fix it.

How windows & MBR(msdos) & partition boot sectors work
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by srs5694 on 2010-11-08
> **oldfred said:**
> If your are using grub to boot you do not have to have a boot flag, but some BIOS will not let anything boot unless there is  a boot flag on a primary partition. Both the windows boot loader and Lilo use the active partition (boot flag) to know what partition boot sector to load next. Windows only seems to want to repair the active partition, so we need the flag if we have to fix it.

It's been a while since I've used LILO, but my memory is that it did *not* use the active/boot flag if you put LILO in the MBR. You would, however, need to have that flag set on a Linux partition if you installed LILO in the Linux partition and relied on a DOS/Windows-style boot loader in the MBR.

---

