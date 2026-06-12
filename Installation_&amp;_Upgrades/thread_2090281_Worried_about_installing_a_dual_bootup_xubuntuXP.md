---
title: "Worried about installing a dual bootup xubuntu/XP"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by SmalekTF on 2012-12-01
Hello community,

I am in need of using Linux at work and currently I have a laptop with Windows XP on it.  I would like to install Linux to work along with XP in a dual boot setup.  I have already used Linux on the laptop via VMWare Player, however I have come to find that this method can also limit me.  Due to this case I decided to do this installation.  

I tried installing Xubuntu on an older personal laptop that I was going to give away anyway, and going through installation it became stuck during disk partitioning.  After a long while I decided to just reboot the machine, of course this caused issues with accessing Vista on that machine.  That's fine that PC was expendable.

Having said this I CANNOT lose my current XP setup.  Of course I plan to make backups, boot CD,...etc.  I am even going to purchase ghost image software to backup an entire image.  Yes I am paranoid about this.  I have a lot of software/configuration that I don't want changed.  Data can be backed up and that's fine, but setting up tools, making special configuration to tools, and setting many drivers can take a while...etc.etc.
I cannot afford that nightmare.  Of course a hard drive failure/crash can always bring this, but that's not my direct doing :P

OK, what is my best approach in doing this?  Of course the Xubuntu setup failure has raised alarms for me.  I am wondering what the advice of you good folks is for me :)

If there is a chance of something going wrong and I cannot recover my XP in it's exact state, I would rather purchase a separate laptop just for Linux.  But I think that would be too much!

I have 2 weeks to do this since my next project will likely require me to use a Linux OS for my work.

Anyway, thank you for any feedback on this :)

---

### Post by sudodus on 2012-12-01
It is risky to edit partitions, which you need to do in order to make a dual boot system. So you need a reliable backup.

But you don't need to buy Ghost. You can download *Clonezilla*, which is also a free linux program (actually as a live CD/USB drive). You can make clones and images of whole drives or partitions with Clonezilla (similar to what you can do with Ghost).

When you have the backup, you can start to edit the partitions with *gparted* (before you start the installation). This way you have 'full control' of the partitioning. It can take hours depending on the size of the data to be moved. (Maybe it was working slowly, not stuck, during your installation).

But the simplest thing is to use the xubuntu install disk and let the installer do the partitioning 'almost' automatically.

---

### Post by oldfred on 2012-12-01
Besides clonezilla there is this:

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
What partitions have you used. The 4 primary partition limit is often an issues with MBR(msdos) partitioning. Although most Windows 7 system use all 4, it just may depend on what partitions you have created on your system.

Post this from LiveCD/DVD or flash drive.
sudo fdisk -lu

I prefer to partition in advance with gparted and then use manual install to choose which partition is /, /home & swap. Swap is usually  automatically found if created in advance. I also suggest a separate NTFS shared data partition. Then you can mount the Windows system partition as read only and only read write into the shared data partition.

Do not shrink Windows too much. NTFS really likes at least 30% free space to work well. At 10% free it just about stops working.

---

### Post by zvacet on 2012-12-02
Read [this]("https://help.ubuntu.com/community/DualBoot/Windows") and after that you can try to install Xubuntu on your old comp just to become familiar with partitioning.later you can go for dual boot with your XP.

---

### Post by gwilson on 2012-12-20
First of all, I think the chances of Xubuntu ruining your XP installation are pretty small, but that depends on your comfort level. Maybe the best thing to do is buy a USB portable hard drive and backup XP to that.

Another option is one I have tried with success. You can buy a TINY SanDisk Cruzer Fit USB flash drive and put a bootable installation of Xubuntu onto that. If you install GRUB on your hard drive, you can choose to boot either XP or Xubuntu on powerup. If you don't want to touch your hard drive at all, you can simply use the BIOS of your computer to cause it to boot to either the hard drive or the USB drive.

The USB drive will have plenty of room for Linux programs and configuration data and will still have access to the main hard drive for data, music or whatever.

---

