---
title: "Unmount at /"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by xpowerfulxx on 2010-08-02
I wish to unmount my partition so that I can reformat it to NTFS instead of ext4. Problem is, its always mounted and when I try it says "Device is busy" or something of that sort. Is there a way I can reformat it and dual boot Windows and ubuntu on it? I have Ubuntu 10.04 Lucid.

[IMG]http://img191.imageshack.us/img191/909/mountq.png[/IMG]

---

### Post by sikander3786 on 2010-08-02
Hi.

Why you want to format root to NTFS?

It will be mounted until you are running the Ubuntu install.

You need to boot from a live cd in order to unmount the root partition.

**But reformatting / to NTFS will leave your system unsable.** Did you know that?

Linux only installs on ext partitions.

Regards.

---

### Post by xpowerfulxx on 2010-08-02
> **sikander3786 said:**
> Hi.

Why you want to format root to NTFS?

It will be mounted until you are running the Ubuntu install.

You need to boot from a live cd in order to unmount the root partition.

**But reformatting / to NTFS will leave your system unsable.** Did you know that?

Linux only installs on ext partitions.

Regards.
[IMG]http://2.bp.blogspot.com/_ub2McBBxqCw/TAdBQoBCVPI/AAAAAAAAAHo/U8aCtv2Z4P4/s1600/RageGuy.jpg[/IMG]
So is there a way that I can split it in half and make 1/2 of it into NTFS?

---

### Post by QuinnHarris on 2010-08-02
The only reason to use NTFS with Linux is to exchange data with Windows.  The most common case is installing Ubuntu after installing Windows in which case the installer will easily allow installing them side by side and Ubuntu will provide access to the Windows NTFS partition.  I would recommend for dual boot installs like this to install Windows first because the Ubuntu installer will resize the NTFS partition if necessary and setup the boot loader (GRUB) properly.  The Windows installer doesn't play nice with others and will not setup a boot loader to boot anything but Windows.

Installing Windows after Ubuntu can be done but it is a bit trickier.  Is this what you are trying to accomplish?

You can resize the root partition after install but if you are shrinking an ext(234) partition it must be done offline.  (the new experimental btrfs can do online shrink and enlarge) So you you need to boot an install/live CD.  I think you can use gparted to do the resize or use resize2fs with carefull use of fdisk.

What exactly are you trying to accomplish?

---

### Post by xpowerfulxx on 2010-08-02
> **QuinnHarris said:**
> The only reason to use NTFS with Linux is to exchange data with Windows.  The most common case is installing Ubuntu after installing Windows in which case the installer will easily allow installing them side by side and Ubuntu will provide access to the Windows NTFS partition.  I would recommend for dual boot installs like this to install Windows first because the Ubuntu installer will resize the NTFS partition if necessary and setup the boot loader (GRUB) properly.  The Windows installer doesn't play nice with others and will not setup a boot loader to boot anything but Windows.

Installing Windows after Ubuntu can be done but it is a bit trickier.  Is this what you are trying to accomplish?

You can resize the root partition after install but if you are shrinking an ext(234) partition it must be done offline.  (the new experimental btrfs can do online shrink and enlarge) So you you need to boot an install/live CD.  I think you can use gparted to do the resize or use resize2fs with carefull use of fdisk.

What exactly are you trying to accomplish?
I want to dual boot Windows XP on the big partition
What are YOU trying to accomplish?

---

### Post by oldos2er on 2010-08-02
The only way Ubuntu will run on NTFS is with a Wubi install, which is something resembling a demo not meant to be permanent.

I think there is software for Windows that will allow it to read an ext3 partition, so you might want to consider that.

---

### Post by xpowerfulxx on 2010-08-02
> **oldos2er said:**
> The only way Ubuntu will run on NTFS is with a Wubi install, which is something resembling a demo not meant to be permanent.

I think there is software for Windows that will allow it to read an ext3 partition, so you might want to consider that.
:confused: What's Wubi

---

### Post by oldos2er on 2010-08-02
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by JustinR on 2010-08-02
I'm not sure if this is possible but could you just create a separate EXT4 partition for Ubuntu, a separate NTFS partition for /home and then Install windows next to it so you have access to your files?

---

### Post by xpowerfulxx on 2010-08-03
I just want to split the partition in half so 1/2 of it could be Ubuntu and the other half is Windows.

---

### Post by JustinR on 2010-08-03
> **xpowerfulxx said:**
> I just want to split the partition in half so 1/2 of it could be Ubuntu and the other half is Windows.

If I'm understanding you correctly, you can't have two operating systems on one partition.

You can try Wubi though - it comes on the Ubuntu Live CD.

Put the CD in Windows and it will autostart. It installs Ubuntu 10.04 in the NTFS partition.

---

### Post by xpowerfulxx on 2010-08-03
> **JustinR said:**
> If I'm understanding you correctly, you can't have two operating systems on one partition.

You can try Wubi though - it comes on the Ubuntu Live CD.

Put the CD in Windows and it will autostart. It installs Ubuntu 10.04 in the NTFS partition.
Only problem - I don't have Windows. I want Windows. I want to cut my partition in half.

---

### Post by JustinR on 2010-08-03
> **xpowerfulxx said:**
> Only problem - I don't have Windows. I want Windows. I want to cut my partition in half.

Do you have a Windows disk?

---

### Post by jocko on 2010-08-03
Don't listen to the people here, they seem to be stuck in thinking you mean you want both operating systems in one partition. You don't need wubi to set up a dual boot.
Just boot from a live cd and use gparted to shrink your ubuntu partition to leave unpartitioned space for a windows partition.

I think windows xp need to be on the first partition on a drive (not so sure about vista or seven), so you may need to make sure the empty space is "to the left" of the ubuntu partition. This will require moving all of the data from the beginning of the drive to the new start of the partition, which will take quite some time.

The windows partition needs to be a primary partition with the bootable flag, but if you use the windows installer's own partitioner to set up the ntfs partition it should be set up correctly.

One problem you will encounter is that windows will overwrite the bootloader (grub) in the major boot record of the hard drive with it's own boot loader (which is not advanced enough to detect non-windows operating systems), so after windows is installed you will need to reinstall grub to the mbr. [This guide]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") will help you with that.

Edit: A good piece of advice: Make sure you back up any data you want to keep, preferably to another hard drive. Or make a new ext4 (or ntfs if you want to access it from windows) partition at the end of the drive to copy all your important data to before you start installing windows.

---

### Post by JustinR on 2010-08-03
Hi,

Sorry xpowerfullxx, I re-read your first post and you want to dual boot, instead of what I was thinking :redface: 

First method is easiest. 
Do you have anything important in the Ubuntu installation? If not, use the Windows disk to format the HDD, create a partition thats half of the HDD size. When installation it finished, install Ubuntu using the Ubuntu live CD. Voila, your finished and have a dual boot! Use 'ntfs-config' to access your Windows files from Ubuntu if you want (eg. music, movies, and pictures)

Second method.
If you have important things on the Ubuntu installation, or just don't want to have to reconfigure Ubuntu again then do this. (Backup important data to something like a CD first). Bootup your computer with an Ubuntu live cd and use the program **System > Administration > Gparted**. Click on the Ubuntu partition and resize it to half of the HDD size. Restart the computer with the Windows live CD, install Windows. (Windows will overwrite GRUB so when you reboot your computer Ubuntu will be invisible). Restart the computer with the Ubuntu Live CD. Figure out your hard drive name (eg. /dev/sda) with **System > Administration > Disk Utility**. Go to **Applications > Accessories > Terminal**.
```

sudo mount HARDDRIVENAME /mnt

```
Replace HARDDRIVENAME with the name you found from Disk Utility (eg. /dev/sda or /dev/sdb, etc.)

Then type this into the terminal:
```

sudo grub-install --root-directory=/mnt/ HARDDRIVENAME

```

Again, Replace HARDDRIVENAME with the name you found from Disk Utility (eg. /dev/sda or /dev/sdb, etc.).

Your finished! Restart your computer and now you should have a choice between Windows and Ubuntu.

To access Windows files from Ubuntu (eg, Movies, Music, Pictures) install the package 'ntfs-config'.

Good luck!

---

