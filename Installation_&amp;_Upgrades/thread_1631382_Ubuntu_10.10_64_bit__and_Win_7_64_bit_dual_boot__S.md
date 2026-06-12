---
title: "Ubuntu 10.10 64 bit  and Win 7 64 bit dual boot  SEPARATE DRIVES Install Instructions"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by TheDevilYouKnow on 2010-11-26
Hello!
I just recently cobbled together a bunch of old parts on my workbench and installed Ubuntu 10.10 on it FLAWLESSLY and I was quite impressed! I am picking up a new Hard Disk today after work and wish to Install Ubuntu on it so that I can Dual boot between the two OS'es on My existing Win7 64 bit desktop. Each OS will live on it's OWN SEPARATE HARD DISK in a system where Window 7s has already been installed. My Desktop is built with an MSI Motherboard, AMD Phenom II 970 Quad core CPU,8 gigs of DDR2 ram,an MSI/ATI video card (5830), and has two hard drives in it right now - a 72 gig WD Raptor ( Win 7 lives there) and a 500 Gb WD Caviar (Data Drive).  I also have a Linksys wireless N card ( dual channel ) and I will be adding another Caviar (320Gb to 500 Gb) Drive specifically for Ubuntu. 
 
[COLOR=magenta]Where can I find instructions to properly set up a dual-boot system with separate Drives?[/COLOR]
 
Will I be able to see the contents of the NTFS formatted Data Drive?
 
Are there any concerns I should have?
 
All drives concerned are SATA and the Data drive and Win 7 drive are formatted NTFS.
 
Thanks for your time gentlemen! I am looking forward to diving in to Ubuntu!
 
 
TDYK.

---

### Post by oldfred on 2010-11-26
The main issue becomes where grub2 gets installed. It normally defaults to sda, which usually is the windows drive. If you only have one drive that works but with multiple drives you may want to have grub2 in the MBR of the Ubuntu drive and in BIOS set that to be the boot drive as grub will give you the choice to boot Ubuntu or windows. Also if you do not install grub to the windows MBR then that drive can be directly booted via BIOS if needed.

The issue with Maverick is that you only get the choice of where to install grub if you use manual partitioning. So you need to partition in advance or manually as you install. I always partition in advance so I have control over partition sizes and locations.

Ubuntu will read and write NTFS partitions without issues, but sometimes the windows system install does not like too much activity that it does not control. Plus with Ubuntu you see all the hidden files & folders, so it is possible to damage the windows install accidentally. With separate shared NTFS partition you should not have to write into the windows system partition and can mount it read only so you do not accidentally cause issues.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

I may have given you too much info at one time, it you have specific questions please ask and someone will have answers.

---

### Post by sikander3786 on 2010-11-26
Welcome to the forums :-)

Installation on 2 different drives is much easier than installation on a single drive so, I couldn't find a guide specifically written for that.

This is worth reading though.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

What you need to do simply is to install Windows on one drive and Ubuntu on the other. It would be better to install the Ubuntu bootloader to its own drive (you'll be given a choice under manual partitioning). But, if you are unsure where to install that, just disconnect your Windows drive prior to the installation of Ubuntu and everything will go well automatically as there would be a single drive to install the bootloader to ;-)

Later, connect your Windows drive, make your Ubuntu drive first bootable drive, boot Ubuntu and run this command to add Windows to your Grub menu for dual boot.

```
sudo update-grub
```

Regarding NTFS, yes NTFS is well supported in Linux and you can have a shared data partition for both the OS. You can mount that partition using the NTFS Config Tool (GUI) or by adding an entry in /etc/fstab.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

There should really be no concerns :P

Post back if you've any doubt regarding any thing, whatsoever.

---

### Post by TheDevilYouKnow on 2010-11-26
So if I understand correctly, If I simply disconnect my main ( Win 7 ) OS drive, leave my data drive connected and physically install the new blank drive, I can Install Ubuntu on the new blank drive I just installed, Install GRUB 2, then reconnect the Win 7 drive and all will be well...Meaning the system will then boot off the New Ubuntu install - will then show me GRUB 2 - then I choose whether or not I want to boot into Ubuntu or Windows and all will be well?
 
 
 
Thank you all!
 
 
TDYK.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2010-11-26
> **TheDevilYouKnow said:**
> So if I understand correctly, If I simply disconnect my main ( Win 7 ) OS drive, leave my data drive connected and physically install the new blank drive, I can Install Ubuntu on the new blank drive I just installed, Install GRUB 2, then reconnect the Win 7 drive and all will be well...Meaning the system will then boot off the New Ubuntu install - will then show me GRUB 2 - then I choose whether or not I want to boot into Ubuntu or Windows and all will be well?
 
 
 
Thank you all!
 
 
TDYK.

Once you've reconnected the Win7 HDD, boot into Ubuntu. (Both drives should be connected at this point) After your desktop-environment loads, invoke the following command using a shell. 

```
sudo update-grub
```

During the execution of this command, the os-prober script within GRUB should 'map' your Windows drive accordingly. 

You can quickly reboot your machine to verify everything is setup correctly, and, whether or not you're able to boot into Windows!

Please confirm results! 

Thanks,

---

### Post by TheDevilYouKnow on 2010-11-28
Well,
         I read all the info everyone kindly posted for me to read, then I just disconnected my Win 7 64 bit drive,
disconnected my Data drive,Installed the new blank Hard Disk,Installed Ubuntu 10.10,Rebooted,then shut down,reconnected the two disconnected drives,Rebooted ( into Ubuntu ),started a terminal and entered the GRUB commmand as given,Rebooted again and there it was...the gRU loader giving me my choices as to what to boot into. Works GREAT and Ubuntu absolutely FLIES on my desktop system!


Thank you all so much...I can Tell that I am going to enjoy this community!




TDYK.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2010-11-28
Excellent! Good to hear that everything is working well on your end. 

Cheers!
O:)

---

