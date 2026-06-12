---
title: "Dual Booting Linux with Windows XP"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by kyndod7 on 2008-08-22
Recently I set off to RAID 1 my computer and decided that while I was messing with my drivers I should go ahead and install Ubuntu 8.04 LTS (64bit AMD and Intel) as well. I decided to create a dual booting system which would allow me to use Ubuntu and the much more familiar Windows XP. After setting the RAID, I went ahead and installed Ubuntu as specified in the following guide: [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty). I followed every single step and the installation went through smoothly. However, at the moment of rebooting the system, there was no dual-booting screen that allowed me to choose between Windows XP and Ubuntu. Instead, it just went ahead and booted Windows XP as if there was no other OS installed.
	
       After doing some research, I found another guide that instructed me to create an addition EXT3 partition and mount it to “/boot” ([http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/](http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/)). I reinstalled Ubuntu but this time I created the boot partition as specified in the guide. Unfortunately, the results were the same.
	
        Since then, I have research the topic further but found somewhat contradictory information. Some sources say that Ubuntu should automatically implement the GRUB as the system’s boot loader while others say that a manual modification of the MBR is necessary. At this point I have no idea what to do. How can I fix this?

Thanks

---

### Post by sandysandy on 2008-08-22
it depends on the boot order and where the GRUB is installed.

post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR] ( from terminal of live CD)

regards

---

### Post by kyndod7 on 2008-08-22
My current RAID set up (RAID 1) mirrors all the data installed in the first hard drive (HD A) to the second hard drive (HD B). Because of this, I just went ahead and installed Ubuntu in HD A which contains Windows XP. When I go to the BIOS, the booting order reads only one HD (I am assuming the RAID setup indentifies both hard drives as one because of the RAID 1 configuration).

I did notice something odd during the Ubuntu installation. At the time of manipulating the partitions to install Ubuntu, the partitioner allowed me to choose between the free space in HD A and the free space in HD B. Even though I installed Ubuntu in HD A to avoid this kind of situation, as far as I know, it shouldn’t allow me that option since all HD B is doing is mirroring whatever is in HD A.

I tried a little experiment a friend suggested. First I disconnected HD A (the hard drive that has Windows XP and Ubuntu) and the RAID setup worked as expected. It announced that HD A was not part of the configuration and it went ahead and loaded the mirrored Windows XP in HD B. However, when I disconnected HD B and booted the computer with HD A I got the dual booting screen allowing me to choose between Ubuntu and Windows XP. That time, however, the RAID setup announced that HD B had “failed”. So I went ahead and booted Ubuntu to make sure everything is fine and then Windows XP. After Windows XP loaded I rebooted the computer both drives connected.  The Intel RAID program did a 2 hour scan to actualize the information in both hard drives. After the scan, I tried disconnecting HD B again to load Ubuntu again but this time the boot screen didn’t appear. The only difference this time is that the RAID setup didn’t say that HD B had failed. Instead it said that it was not part of configuration (basically, that it wasn’t connected).

As of this point it looks to me like I have to decide between keeping my current RAID setup or running Ubuntu. Is there anyway I can do both?

Thanks

---

