---
title: "Best way to partition new ssd and move installation?"
date: 2015-04-02
forum: Installation &amp; Upgrades
---

### Post by Thomas_Price on 2015-04-02
I'd like to move my existing 12.04 installation (Ubuntu only. No dual-boot) from my current drive to a new ssd (120GB).  My / and /home are on different partitions.  I tried following these instructions [HTML]http://askubuntu.com/questions/40372/how-to-move-ubuntu-to-an-ssd[/HTML], but was having trouble getting grub to find any kernels.  I believe I might have had an issue with the correct flag on my /boot partition on the new drive.

What is the best way to partition the new drive?

What flag and format for /boot should I use?

Any advice on how to install grub on the new drive?

Thanks!

---

### Post by oldfred on 2015-04-02
I do not believe in moving an install.
Better to have new clean install as then everything is also housecleaned.
Also then able to reconfigure. Most desktops do not need a /boot partition and now gpt is a better partitioning system but cannot easily be copied from MBR partitioned system.

Grub does not use boot flag, that is a Windows requirement. A few motherboards need to see a boot flag, so we suggest you have one, but not normally used in a Linux only system.

Best to see details. You do have to edit fstab, and some other entries to have system reconfigured correctly. Are you keeping old install and/or old drive? How did you copy. Did you change UUIDs. Or lots of issues on moving an install.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Thomas_Price on 2015-04-08
So, if I do a clean install on a gpt system, how should I partition the drive?  

Do I no longer need a /boot partition?   How would I find out if I need a boot_flag?  This is my motherboard - [http://www.biostar-usa.com/app/en-us/mb/introduction.php?S_ID=546](http://www.biostar-usa.com/app/en-us/mb/introduction.php?S_ID=546)

I am keeping the old drive, which also has my /home partition on it (and I would likely keep it there unless there is a benefit and good way to split the user data and configuration files), but would delete the existing / and /boot and /swap partitions once I've moved to the new drive.

---

### Post by oldfred on 2015-04-08
You can keep /home on hard drive. And it can be MBR even though install on SSD is gpt. But if you use gpt then you can only install Windows to a gpt partitioned drive with UEFI. I planned a new UEFI system several years ago, so started changing all drives to gpt whenever reconfigured or purchased. But just built new UEFI system a few months ago.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)

I do prefer to keep /home inside / on the SSD, so the user config data is also loaded quickly. But I use a data partition on hard drive for all the normal data folders in /home like Documents, Music, Videos, etc. And I link those back to /home so system sees all the standard partitions.

If you have 4GB or more of RAM you may never use swap. I might keep it on hard drive. All the old arguements over life of SSD are now obsolete, but if you never use swap it is moot anyway. I suggest just 2GB then to have some. Some with lots of RAM have no swap.

---

### Post by gordintoronto on 2015-04-09
If it were my computer, I would do a fresh install of 14.04 (or even 15.04, which has major advantages on my particular system) and leave the swap on the hard drive. Then again, I would only use half the SSD, so I could use the other half to fool around with other versions or distros.

---

