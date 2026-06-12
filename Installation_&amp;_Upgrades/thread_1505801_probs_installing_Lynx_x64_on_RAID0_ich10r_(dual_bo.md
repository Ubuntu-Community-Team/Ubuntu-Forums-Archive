---
title: "probs installing Lynx x64 on RAID0 ich10r (dual boot)"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by iDen on 2010-06-09
Hi everyone.
I've planed to install Ubuntu Lucid Lynx 10.04 x64 on my rig.
dual boot setup
windows 7 preinstalled
Intel ICH10R RAID0
manual partition setup
200mb ext3 /boot
2gb  swap
100gb  ext4 /

GUI installer can see my RAID and allows me to create this partitions manually.
But when install begins
i'm getting error :
> The ext3 file system creation in partition #5 of Serial ATA RAID isw_dgaehbbiig_RAID_0 (stripe) failed

parts: #5 - /boot; #6 - swap; #7 - /

things i've tried:
/boot => primary or extended
/boot => ext3 or ext4
same error

fdisk -l from Live cd shows me separated HDDs without RAID0 wrap (sda and sdb)

Also in advanced section where i can configure boot loader default is /dev/sda, which is part of RAId_0. I'm checking isw_dgaehbbiig_RAID_0 as location for loader, assuming that this would be MBR. am i doing this step right ?

Please help. 
Thanks in advance.

---

### Post by ronparent on 2010-06-09
As you have found the 10.04 live cd will be useless to you with the raid. You should be able to use an earlier version live cd to crate and check the raid0 partitions with the proviso that if it is 9.04 or earlier you will have to 'sudo apt-get install dmraid' within a live cd session to do so. I would recommend pre-partitioning the drive with the earlier live cd. Also make sure you are creating the partitions within an extended partition (your results so far suggest that you might be trying to install on another primary partition - win 7 by itself takes two primary and you are limited to four total including the extended).

My own experience was that an install to raid0 extended partitons went flawlessly. You do have to hit the advanced box in step 8 to direct grub2 mbr install to the root of your raid. Look for it in /dev/mapper/. It is the symbolic link normally designated without the partition numbers (ie mine is nvidia_aebhdfib). The install will fatally fail if this last step is not performed (fixable but in you system would require chroot commands).

Post if you have more questions.

---

### Post by iDen on 2010-06-15
googling internets for some info about fakeRAID and linux and some tools for it like DMRAID i've found this very informative help article on Ubuntu Community Help pages:
[B][COLOR=Red][FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")[/COLOR]
[/B]
I'll try tricks from this howto on these weekends, lets see if it gonna help

---

### Post by harak on 2010-06-17
I was able to get it to work. When you get the error in ext4 creation. simply boot out. Create a recent gparted live cd. boot using the gparted live cd. Load the raid volume. You will find that the partition map that you had asked for during the ubuntu install are still intact. Now simply reformat each partition into respective FS-types. Once that is done. reboot remove the gparted live cd; insert the Lucid live cd. Once you reach the partitioning part: select manual partitioning. From here on it is the same procedure as in the fakeraid how to for 9.10. For your convenience I am simply copying it here for you: 

*Run the installer. When it gets to it's partitioner, change the mount point on the first partition to / DO NOT format it! Do NOT make any partition changes! 

** In the installer summary screen right before the copy process starts, click the Advanced button. Change the boot partition (this is the MSDOS-style "parent" partition not the Linux partitions) to /dev/mapper/pdc_feddabdf (or whatever dmraid lists as your fakeraid partition) Make sure the checkbox is clicked to boot from this disk.

After installation is done just reboot. You will not see any grub messages. But the system will boot into Ubuntu.

I haven't tried it with dualboot.
Hope it works for you.

---

### Post by harak on 2010-06-20
I have now tried it with dual boot. Once windows is installed, do the following.
*create a gparted live-cd.(see [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php))
*boot using the gparted live-cd
*gparted detects the raid0 volume as (in my case) /dev/mapper/isw_cdfffdcabb_Volume1. Note the individual devices /dev/sda and /dev/sdb are also detected. 
*From the drop down menu on the top right choose the raid0 volume (/dev/mapper/isw_xxxxxxxx)
*Then create the partitions needed for installing Ubuntu. i.e. swap and /ext4 and any other partitions you desire to have.
* Boot out of the gparted live-cd
* Now boot in using the lucid lynx live-cd.
* When you reach the partitioning stage, do not format them.
* Assign the ext* partition(s) to / (and /home etc.)
* Continue forward
* When you reach the installer summary screen. Click on "Advanced" and Change boot partition to  /dev/mapper/isw_cdfffdcabb_Volume1. 
* Finish the installation and reboot.
When you boot into Ubuntu and run gparted or fdisk, you won't see the volumes as /dev/mapper/isw_xxxxxxxx. Do not worry. There is nothing wrong with your install. However if you are eager to verify it, then open a terminal and run the following code.
sudo add-apt-repository ppa:danwood76/ppa-testing
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gparted 

This upgrades both dmraid and gparted. The last step is necessary if you do not have gparted installed already. Launch gparted. Now gparted recognizes the raid0 Volume. fdisk still doesn't but who cares!

---

