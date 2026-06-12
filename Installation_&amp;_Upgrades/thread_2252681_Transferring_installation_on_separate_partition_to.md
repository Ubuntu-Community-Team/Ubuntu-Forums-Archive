---
title: "Transferring installation on separate partition to separate hard drive"
date: 2014-11-13
forum: Installation &amp; Upgrades
---

### Post by Sega dude on 2014-11-13
Currently, I am dual booting my main Desktop with Windows 8.1 and Ubuntu. Ubuntu and Windows are installed on separate partitions. I am very low on space on my Windows partition. Since I don't use Ubuntu as often as I use Windows, I would like to transfer my Ubuntu installation to a separate 320GB hard drive I have laying around. After transferring the ubuntu installation to the "new" hard drive, I want to remove the ubuntu installation from the drive it was on so I gain back the space for Windows. Is this possible? How would I do this? I have everything I need to connect the "new" hard drive internally or via USB (for transfer purposes). I would also need to modify my grub so that it would point to the "new" hard drive for Ubuntu, correct?

Here's what the partitions look like if it helps:
[IMG]http://i59.photobucket.com/albums/g292/segadude/Screenshot.png[/IMG]

---

### Post by nerdtron on 2014-11-13
You want to transfer your current Ubuntu OS or just want to copy/backup the files of you ubuntu install and perform a new install of ubuntu?

---

### Post by Sega dude on 2014-11-13
I want to transfer my current Ubuntu OS. Although I don't have much on Ubuntu installation, so I could backup the important things and preform a new install, which is probably much easier. Either way, I'll still need to reconfigure GRUB and remove the old installation from the Windows drive.

---

### Post by yancek on 2014-11-13
If you don't have a lot of data on the current Ubuntu partition, it would be easier to just install it to the new drive.

Some of the steps you would need to do what you want would be to boot an Ubuntu or Linux CD/DVD/flash drive and use GParted or another partition manager to create a partition of the size you want on the 320GB drive and format it, ext4 or whatever you want.  When you have done that, create a mount point for the current Ubuntu partition on the first drive, then create a mount point for the partition on the 320GB drive.  After doing that, you need to mount both partitions.  Then you would need to copy the first partition to the new partition.  I did this once and I think the command I used was:  sudo cp -ax /mnt/sda1/* /mnt/sdb1/  You would have to change the mount points as well as device names to suit your system and no guarantees this will work.  If it does work, you would need to run the blkid command on the 320GB drive to get the uuid for the new partition and you would then have to mount the new partition and as root, go to the grub.cfg file and modify all the uuid entries as well as the set root lines so they are pointing to the correct partition.  You would also need to modify the /etc/fstab file so that the device and/or uuids are correct for the new partition  and then install Grub to the master boot record of the 320GB drive.  If that doesn't do the job, you might have to chroot into the new partition and modify Grub and run sudo update-grub. 

If this is all familiar to you and you understand the steps, go for it.  There are other ways to do this which might be easier so you might want to wait for someone else to suggest something.  It might be easier to do a new install.

---

### Post by Sega dude on 2014-11-13
> **yancek said:**
> If you don't have a lot of data on the current Ubuntu partition, it would be easier to just install it to the new drive.

I think I will go that route instead. It will be much easier that way.

---

### Post by oldfred on 2014-11-13
As yancek points out, the UUID is embedded in multiple places in the install. While possible to do a lot of manual editing from another install or live installer. It often is just easier to do a new install and copy important data from /home over.

With a new drive you also have some other advantages. You can restore Windows boot loader to Windows drive, and install grub to "new" 320GB drive. And then set BIOS to boot it. Since now a separate drive you could also use gpt partitioning which is replacing the 35 yr old MBR(msdos) partitioning. The gpt is only required for drives over 2TB or if UEFI booting. Windows only boots from gpt drives with UEFI, but Ubuntu will boot with BIOS or UEFI if you have correct partitions.

I would use gparted, create partitions you want and use Something Else. Only something Else gives the option on where to install grub2 boot loader which probably should be drive that is sdb.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)


 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

You can either create a separate /home and copy your data to that separately or create data partition(s). If you have installed a lot of applications, you may want to export the list to make it easy to reinstall.

      
 One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)


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

There are a lot of options on partitioning and it depends on how you may want to use system. I like to have another / (root) or 20 or 25GB so I can test new versions or experiment with settings without messing up my main working install.

      
 Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Sega dude on 2014-11-13
I installed the second hard drive into the computer and removed all the partitions so it's just unallocated space now. I also backed up all the important stuff from the Ubuntu install onto a flash drive. I am all ready to do a clean install on the second hard drive.

---

### Post by nerdtron on 2014-11-13
You can remove the 1st HDD and install Ubuntu on the second hard drive.

After that you boot on to the second drive (the 1st drive should be attached by now) then run "sudo update-grub". This will scan all partitions for available OS, and will add entry for the windows and first Ubuntu on the First hard drive.

Now once you are sure that you can boot into windows, you can now delete the partition of the first Ubuntu on the first hard drive and expand it for windows use.

---

### Post by Sega dude on 2014-11-13
I just performed a clean install on the second hard drive, leaving the original hard drive untouched. I actually had both hard drives connected during the installation. All that's left to do now is delete the the Ubuntu partitions on the original hard drive and extend the windows partition into the unallocated space. I was planning on deleting all the Ubuntu partitions from Windows using Disk Management, then extending the Windows partition into the unallocated space. Will this work? Grub is still installed on the 1st hard drive, /dev/sda. I guess I should have selected the other drive during installation... What do I about grub now?

---

### Post by yancek on 2014-11-13
>  Grub is still installed on the 1st hard drive, /dev/sda.  I guess I should have selected the other drive during installation...  What do I about grub now? 		

The important question is with Grub on sda, can you boot the new system on the second drive?  If you can't what you need to do is to boot the old Ubuntu and run:  sudo update-grub and watch the output to see if the second drive install is detected.  If it is, reboot to the new Ubuntu.  You can then install Grub from the new Ubuntu to the mbr of the second drive and/or the first drive.  Are you planning to keep the second  drive permanently attached?  If you are planning to keep both drives attached, install to sda.  Installing to both would work also.  If you have Grub in the mbr of the first drive from your original installation you need to make sure the new Ubuntu Grub is on the mbr of sda if you leave it as first boot priority unless you have a windows installation CD/DVD to install windows to the mbr of its drive.

I think you made a wise decision doing the new install.  I only copied a system once and only because I had messed something up on a friends computer on which he had a lot of personal data.  It was a real chore.

---

### Post by oldfred on 2014-11-13
If from install you selected or let it default to sda, then on major updates it will reinstall grub to sda.

You can check if that is how it is set and reset where grub reinstalls.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
It will show drive model & serial number


 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

You can then rerun the debconf to see that default has changed.

Then if from BIOS you can boot Ubuntu ok, you can install a Windows boot loader to sda.
You can use Windows and fixMBR or from Linux install syslinux or lilo boot loaders which work just like Windows. Windows boot loaders only check  which partition has boot loader and jump to that partition for more boot code.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by Sega dude on 2014-11-14
> **yancek said:**
> The important question is with Grub on sda, can you boot the new system on the second drive?

Yes I can, the new install shows up as Ubuntu at the top of the list, like the former installation used to. The former installation now shows up further down the list as "Ubuntu 14.04.1 LTS (14.04) (on /dev/sda5)". The option for Windows 8 and Memtest are there as well, just like before.

> **yancek said:**
> Are you planning to keep the second drive permanently attached?

Yes I am.

---

### Post by yancek on 2014-11-14
Then you should be good.

---

