---
title: "Install questions after previous problems vie installed alongside Windows XP..."
date: 2014-10-30
forum: Installation &amp; Upgrades
---

### Post by drhans2 on 2014-10-30
Hello,

I'm helping my neighbor and ran into problems with a dual boot sys.

About 2 years ago I installed Ubuntu alongside Windows XP.. It worked fine for a few years.. then Ubuntu would not boot, all she got was a screen with the choice of Windows or Ubuntu. Windows booted, but Ubuntu would not..

I tried to look for options to correct but did not understand most of them. I figured the best option would be a fresh install. I uninstalled Ubuntu vie the Windows Uninstall Program & then had problems with the boot option screen after that.. (Windows (default) did not work, but (Windows XP Media Center Edition) did start up the computer.)

The Desktop spec's are:
Dell XPS 720
2 GB memory
Intel Quad Q6600, 2.4 GHz CPU
NVIDIA GeForce 9800 GTX+ video card


I'm starting the fresh install and now have some questions.. Here' what I did so far..

I booted to a live CD of Ubuntu 11.10, used G-Parted to shrink Windows down to 64 GB and create a new partition (sda4) and this is what I now have:
sda1 = fat 16, 54 mb & Dell Utility.
sda2 = ntfs, C:\ 64 GB with Windows XP & boot 32 GB unused.
sda4 = ntfs, E:\ 159 GB unused.
sda3 = fat32, Unknown partition & Dell Restore 4.63 GB & 1.5 GB unused.
unallocated =  8.65 mb.

When installing Ubuntu can I choose "Someplace else" and then install Ubuntu on the vacant sda4 partition I created?

Will the install program create any swap or home partitions if needed?

Is this my best option for a future trouble free system dual boot system? If that's even possible...

As a afterthought..

Are the computer spec's good enough for Ubuntu 11.04 and later versions?

Should I check the box... Get Updates during the install process?

Should I use a earlier version?

Much thanks in advance..

---

### Post by Bucky Ball on 2014-10-30
> I uninstalled Ubuntu vie the Windows Uninstall Program

... suggests you were using a Wubi install. No longer supported by Canonical or these forums, sorry.

11.10 is well out of life and is no longer supported by Canonical or these forums (was EOL a year ago and a half ago). Please use a supported release, I suggest 14.04 LTS for your scenario, supported until 2019, and get back to us. We can't give support for such an old release and you are only going to have problems.

Please read [THIS]("https://help.ubuntu.com/community/EOLUpgrades"). Good luck.

---

### Post by fantab on 2014-10-30
> **Bucky Ball said:**
> ...Wubi install. No longer supported by Canonical or these forums, sorry.

11.10 is well out of life and is no longer supported by Canonical or these forums (was EOL a year ago and a half ago). Please use a supported release, I suggest 14.04 LTS for your scenario, supported until 2019, and get back to us. We can't give support for such an old release and you are only going to have problems.

Please read [THIS]("https://help.ubuntu.com/community/EOLUpgrades"). Good luck.

+1.

> When installing Ubuntu can I choose "Someplace else" and then install Ubuntu on the vacant sda4 partition I created?
...sda4 = ntfs, E:\ 159 GB unused.
Linux/Ubuntu will not install to a NTFS formatted partition. You will need to create a partition with linux filesystem, like ext4 etc.

Get your self a supported version of Ubuntu like Bucky instructs, and get back to us.

---

### Post by drhans2 on 2014-10-31
Thanks for the feedback,

 I will change the NTFS partition to EXT4 but as to installing a currently supported version of Ubuntu.. that's were I ran into a problem..  The "old" computer only has a CD drive and the size of the current version of Ubuntu will not fit on a CD..

My plan was install 11.10 as it fit on a CD, then upgrade online. I should have referenced that in my question.. but did ask if the computer spec's were good enough for later versions of Ubuntu.

I'm not looking for support for or keeping version 11.10 on the computer.. it's just the means to justify the end result.  I'll try other options.. just lay them out.

much thanks..

---

### Post by Bucky Ball on 2014-10-31
You probably won't be able to upgrade online. Too old and repos down. You don't need to use a disk. You can install from a USB dongle. If you're using Windows, then use something like Univeral USB Installer to create the bootable USB from the ISO (works in Ubuntu too I think) or in Ubuntu I use UNetbootin (and I THINK that works in Windows also).

Either way, you don't need to use a disk. Wouldn't bother attempting the upgrade from 11.10. If you're lucky you can go from 11.10 to 12.04 then directly to 14.04 LTS (LTS upgrades to LTS), but unsure what shape you're system will be in by the time you get there. You've come from a long way back and more trouble than it's worth, I'd imagine, if it's possible at all.

---

### Post by drhans2 on 2014-11-01
Thanks for the instructions.. 

I used the program "Universal USB Installer" and created a bootable USB memory stick with Ubuntu 14.04.1 LTS... 

I then booted from the USB to the "Try Ubuntu" option and using "GParted" I changed the partition sda4 from ntfs to ext4. Below is my current partitions.


sda1 = fat 16, 54 mb & Dell Utility.
sda2 = ntfs, C:\ 64 GB with Windows XP & boot 32 GB unused.
sda4 = ext4, E:\ 159 GB unused.
sda3 = fat32, Unknown partition & Dell Restore 4.63 GB & 1.5 GB unused.
unallocated = 8.65 mb.

Now can I just install Ubuntu to the sda4 partition, or do I need to create a swap & home partition or will the install program do all that for me?

When all is said and done I hope to have a dual boot system of Ubuntu & Windows xp.

thanks again,,,

---

### Post by yancek on 2014-11-01
> Now can I just install Ubuntu to the sda4 partition

You have four partitions and if they are primary, you will not be able to create a separate /home or swap partition unless you delete sda4 and then re-create it as an Extended partition which you can do in GParted.  You can then create a logical partitions for the filesystem, another for home if you want but not needed and a third for swap.  For simplicities sake, just making a partition for the filesystem of 20-25GB and 2-4GB for swap should be enough.  If you want a separate /home, use the rest or leave it unallocated and later create a separate data partition.  The first link is to a tutorial on using GParted and the second link is to the GParted Manual.  If you have questions after reading these links, post back. 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

---

### Post by drhans2 on 2014-11-02
Much thanks for the info and links to the GParted instructions.. It was a big help..

I deleted the sda4 partition and then made it a Extended partition, and then made the swap area.

This is what I ended up with.

sda1 = fat 16,   54 mb & Dell Utility.
sda2 = ntfs,     C:\ 64 GB with Windows XP & boot   32 GB unused.
sda4 = extended   159 GB unused.
sda5 = ext4,      29.38 GB    24.77GB unused.
sda6 = linux-swap    4.49GB.... 
unallocated = 125.81GB
sda3 = fat32, Unknown partition & Dell Restore 4.63 GB & 1.5 GB unused.
unallocated = 8.65 mb.

I then booted to Ubuntu vie the USB drive... I installed Ubuntu on sda5.   During the install one of the "error screens" asked about needing to make a boot area.  Guess I got lucky when I guessed at the optioned to partition the drive with a " \  ".    All went well and Ubuntu is now installed, same for Windows.. 

Oddly after the install I looked in Ubuntu for GParted to view my partitions.. It was not one of the 87 plus programs offered with the top icon on left side of screen.. I went to the Ubuntu Software Center and downloaded it from the web. 

 Thanks to all... for the help..

---

### Post by Bucky Ball on 2014-11-02
Excellent news. Please use the second link in my signature to help future travellers. Good luck and enjoy! ;)

---

### Post by mastablasta on 2014-11-03
you made it unnecessarily complicated but in the end you got what you wanted.

it is a lot easier to just create empty unformated space and then install to largest free emtpy space - installer will do the rest...

> **drhans2 said:**
> 
Oddly after the install I looked in Ubuntu for GParted to view my partitions.. It was not one of the 87 plus programs offered with the top icon on left side of screen.. I went to the Ubuntu Software Center and downloaded it from the web. 



it's not odd at all. gparted has to be run in livesession. otherwise you can mess up your sysetm if you handle mounted disks with it. for example windows disk manager work a bit differently. it somehow writes the changes to disks (e.g. in partitions) and then only makes them on reboot.

ther eis somethign called disks in ubutnu i believe that shows disk space and such data. there is also df -h command which will output it all in terminal in a nice way.

---

### Post by drhans2 on 2014-11-03
(unnecessarily complicated)??

Maybe so with my original intent to install Ubuntu mentioned in post # 4.  But after being told that was a bad plan... 

I did as instructed.. (For simplicities sake, just making a partition for the filesystem of 20-25GB and 2-4GB for swap should be enough)... & like you said.. ended up with my goal met.. and I learned some in the process.. 

Much thanks to all involved.. 

As to running GParted after installing Ubuntu.. I only noted that I didn't find the program included as part of Ubuntu after it was installed. That was different from other computers I've installed Ubuntu on. 



..

---

