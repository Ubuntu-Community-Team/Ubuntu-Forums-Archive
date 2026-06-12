---
title: "Removing windows from a dual boot."
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by DJKEMMET on 2011-08-30
Hey All!
   So I've been playing with ubuntu for week or so and I'm already warming up to it. so here's my thing. I have an old IBM thinkpad that I want to convert solely to ubuntu, but for the sake of learning I'd like to learn how to do the following with the terminal in ubuntu.

1.remove windows and it's partition
2. format the partition it was on
3. add it to my ubuntu install to have one clean disk.

any help would be appreciated! thanks

---

### Post by Iantos on 2011-08-30
back up your system and do a fresh clean install of ubuntu...do not partition, just choose to use the entire disk during installation.

---

### Post by Mark Phelps on 2011-08-30
The mechanics of doing what you want are pretty simple -- you boot into an Ubuntu LiveCD and use the Gnome Partition Editor (Gparted) to do the partitioning work you want.

But first -- do you know for a fact that Ubuntu is installed to its own partitions? Because, if not, if it's a Wubi install, removing the Window partition will remove Ubuntu as well.

---

### Post by YesWeCan on 2011-08-30
Hi and welcome.
For the sake of learning...
parted is the command line partitioning tool: [http://www.gnu.org/s/parted/manual/parted.html](http://www.gnu.org/s/parted/manual/parted.html)
GParted is a graphical version: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

I'm guessing your Windows partition is located before your Ubuntu root (unless you are using Wubi as Mark points out). So you may decide to delete the Windows partition and then resize the Ubuntu to fill the empty space.

If you need more help, and because this is a useful tool to learn about anyhow, you should download and run this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post the RESULTS.txt


BTW it makes things a little easier to read if you put code tags around command line text output. You can do this by highlighting the text and clicking the # symbol.

---

### Post by YannBuntu on 2011-08-30
Hello,
There is now a tool to uninstall any OS in 1 click : [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[IMG]http://pix.toile-libre.org/upload/original/1313035409.png[/IMG]

---

### Post by joaquinx on 2011-08-30
Is it possible to use the Disk Utility that comes with Ubuntu? 

Screen shot of Disk Utility
[ATTACH]201126[/ATTACH]
Will I have a problem with Ubuntu being on an extended partition? Will I be able to expand sda5 to encompass the entire disk?

---

### Post by YesWeCan on 2011-08-30
> **joaquinx said:**
> Is it possible to use the Disk Utility that comes with Ubuntu? 

Screen shot of Disk Utility
[ATTACH]201126[/ATTACH]
Will I have a problem with Ubuntu being on an extended partition? Will I be able to expand sda5 to encompass the entire disk?
Disk Utility is nice to use but it won't resize partitions. GParted will.
It is no problem keeping Ubuntu logical; expand the extended partition and then expand sda5. The extended partition can take up the whole drive.

---

### Post by joaquinx on 2011-08-30
What I want to do is to delete the Windows partition and extent the Ubuntu partition to the entire drive. After running GParted, I noticed that the Windows partition was the only one that was bootable. If I delete that partition, wouldn't the computer not be bootable? 

I have used popey's backup when I moved from a wubi install to my current partition install as seen below.

tar czvf /media/SEA_DISC/Ubuntu_Backup/nick.tgz /home/nick
cp /etc/apt/sources.list /media/SEA_DISC/Ubuntu_Backup/
dpkg --get-selections > /media/SEA_DISC/Ubuntu_Backup/list_of_applications.txt

Wouldn't it be better to zap everything and install ubuntu from the CD. Or is there a method to put a MBR on the extended partition after it was extended.

---

### Post by YesWeCan on 2011-08-30
> **joaquinx said:**
> What I want to do is to delete the Windows partition and extent the Ubuntu partition to the entire drive. After running GParted, I noticed that the Windows partition was the only one that was bootable. If I delete that partition, wouldn't the computer not be bootable? 
The Grub boot-loader doesn't use the boot flag at all so this doesn't matter.

> I have used popey's backup when I moved from a wubi install to my current partition install as seen below.

tar czvf /media/SEA_DISC/Ubuntu_Backup/nick.tgz /home/nick
cp /etc/apt/sources.list /media/SEA_DISC/Ubuntu_Backup/
dpkg --get-selections > /media/SEA_DISC/Ubuntu_Backup/list_of_applications.txt

Wouldn't it be better to zap everything and install ubuntu from the CD. Or is there a method to put a MBR on the extended partition after it was extended.So the MBR is always the first sector of the disk and is independent of the partitions. Part of the Grub program exists in the MBR area and part in the Ubuntu /boot/grub directory. After you resize your partitions Grub will probably still find the Ubuntu partition ok, but you might need to reinstall it to the MBR.

Best to run bootinfoscript for specific help if things don't work.

---

### Post by joaquinx on 2011-08-31
Gparted can not resize the extended partition into the partition that was Windows. What next?

---

### Post by YesWeCan on 2011-08-31
Would you post a screenshot of GParted?

---

### Post by joaquinx on 2011-08-31
[IMG]http://i265.photobucket.com/albums/ii211/jespence97/Screenshot.png[/IMG]

I got a warning from Gparted stating that expanding the extended partition might prevent the boot process from finding /boot directory.

---

### Post by joaquinx on 2011-08-31
[ATTACH]201175[/ATTACH]

Can't seem to get a decient size snapshot to upload or display.

---

### Post by YesWeCan on 2011-08-31
> **joaquinx said:**
> I got a warning from Gparted stating that expanding the extended partition might prevent the boot process from finding /boot directory.
Your GParted situation looks good.
Yes, it always gives that warning when you move the start of a partition. And it is often right because some boot-loaders rely on knowing the where the start of a partition is. I think it is ok to ignore the warning because you can easily reinstall Grub, if necessary.

I reckon you want to resize sda2 by moving its left boundary to the start of the disk and then doing the same with sda5. This could take a long time - like an hour or more to complete - and you must not interrupt it.

Just a caution - messing with partitions is never entirely safe. So if there is any vital data on sda5 you ought to back it up first.

---

### Post by joaquinx on 2011-08-31
This maybe problem with grub has me concerned - a bit. I have all the repositories, and list of applications installed, and my entire directory backed up to usb drive. 

Can I reinstall grub2 from the installation disk? I guess if that fails, I can always do a complete install.

---

### Post by Hakunka-Matata on 2011-08-31
I'm wondering how it would even be possible to resize a partition if the partition is mounted, as shown in gparted screenshot post# 13?
unmount the partitions first and see what happens?

---

### Post by joaquinx on 2011-08-31
> **Hakunka-Matata said:**
> I'm wondering how it would even be possible to resize a partition if the partition is mounted, as shown in gparted screenshot post# 13?
unmount the partitions first and see what happens?

The all the partitions were unmounted before an attempt to resize it.

---

### Post by YesWeCan on 2011-08-31
> **joaquinx said:**
> Can I reinstall grub2 from the installation disk?
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

---

### Post by joaquinx on 2011-08-31
> **YesWeCan said:**
> sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

I'll give it a shot in the morning and post the results. Thanks for your time.

---

### Post by sidzen on 2011-08-31
. . . I'd like to learn how to do the following with the terminal in ubuntu.

1.remove windows and it's partition
2. format the partition it was on
3. add it to my ubuntu install to have one clean disk.
----------------------------------------------------------------------------

Find for sure which partitions are NTFS and/or Windows

sudo fdisk -l

say, for example they are /dev/sda1 and /dev/sda2

 cfdisk /dev/sda1 

 d

 cfdisk /dev/sda2

 d

 p

prints the partition table;  there should be unallocated space where sda1 and sda2 once were

 n

 t

select the partition 1

 L

lists the codes for file system types
type in the code for the partition chosen

 W

writes the partition table

 q

You get the idea, I'm sure!  Now go to [http://www.tldp.org/HOWTO/IBM7248-HOWTO/cfdisk.html](http://www.tldp.org/HOWTO/IBM7248-HOWTO/cfdisk.html) and make sure of what you are doing and to reinforce what you have learned.

Best wishes!

---

### Post by Hakunka-Matata on 2011-08-31
Brilliant!, it only took 20 posts until the OP got an answer to his question!  DJKEMMET you deserve a gold star for being this patient.  I also overlooked the OPs original post............  Sorry DJKEMMET

@lantos, joaquinx, you two really should start your own threads, this is a terrible case of *hijacking *a thread.

---

### Post by joaquinx on 2011-08-31
@Hakunka-Matata
One point is that you made a post that contributed nothing to either the OP's question nor to mine. Plus, you misunderstood my posts or never ran Gparted.

Last point is that my postings are in line with the original posting title. I can't say that about your postings.

---

### Post by joaquinx on 2011-09-01
> **YesWeCan said:**
> sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

The resizing was a success. Booted from the CD and ran Bparted. Unmounted the swap partition and it automaticly unmounted my current ubuntu partition. Resized the ubuntu partition which took around 30 minutes. I was expecting to reinstall grub2 if failed to reboot, however, the boot went without any problems. 

YesWeCan, thank you much for the guidance. I couldn't have done it without your assistance.

---

