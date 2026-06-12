---
title: "'Install Now' does nothing on Installation Type screen"
date: 2017-06-13
forum: Installation &amp; Upgrades
---

### Post by ausbushman on 2017-06-13
Hi guys,

I'm trying to install Ubuntu 16.04.2 LTS for my first time, from my USB stick to my external USB hard drive, using Dell laptop released 2016. I don't want to touch my internal hard drive (Windows 10).

I choose 'something else', and wasted an hour learning how Ubuntu partitions should work when I stupidly thought should be smart enough to do it for me, get an error about 'minimum alignment', so I 'go back' and try and do what it suggested, continue to get error, cannot fix it, so 'continue' click 'Install Now', the cursor thinks for a split second and nothing happens.

Is this a feature of Ubuntu? I have put off using this for many years for reasons like this, I stupidly thought they'd have it together by now, but apparently it's still not designed for ordinary human beings.

So what am I doing wrong? Is there some secret I should apparently know about?

Can I also suggest:
- Make the computer do the work for the user. If there's a general standard to have '25GB for /(root)', '2x RAM for Swap', 'all other space for /home', then make the installer do that or at least suggest it for the user! Having to research all this for simply installing Ubuntu is a massive waste of time and pain in the ass.
- I'm nor sure if 'TO Exter nal' is meant to be code or English, but perhaps at least try testing your software before releasing it. See pictures.

---

### Post by oldfred on 2017-06-13
Did you unplug your Windows drive?
You are not showing a new UEFI type install of Windows that a new Dell would have.

With external drives, and UEFI you have to partition in advance as grub only installs boot files to the ESP on sda, and does there for does not create the ESP on second drive.

 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 

   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
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
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

