---
title: "How to move /boot from an existing Ubuntu 12.04.1 installation to a new SSD"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by oscarivera9 on 2013-01-29
I have Ubuntu 12.04.1LTS, Windows 7, Slackware 14 & Fedora 18 installed in my PC.   I've recently added a small SSD to it and would like to be able to boot Ubuntu (which I use more than the other OSs) from the SSD.     I currently have only one partition for Ubuntu which contains everything under root ( / ) including /home.   I cannot put my existing Ubuntu installation in the SSD because it won't fit.  Instead I'd like to move /boot to the SSD if it's possible so I can take advantage of its faster boot-up time.  Is there a way to do so without having to do a fresh install?  If I can avoid it I'd rather not have to reinstall Ubuntu again.


Installation & Upgrades seemed like the best place to post this thread but if it isn't, I'll be glad to move elsewhere.

---

### Post by oldfred on 2013-01-30
How large is SSD?

I have a 60GB SDD with two installs of Ubuntu including my /home. I use about 9GB including the 2GB for /home but have all data on my rotating drive. And my /home is only that large as I still have .wine with Picasa in it.

If you just move /boot, you will only have grub & kernel not system.

Is /home a separate partition on rotating drive? Then a new install but mounting existing /home would be very quick & easy.  If not you can split /home and copy the data to a data partition on rotating drive and the hidden user settings into your SSD.

I prefer to make each drive fully bootable without any other drive. Then when one drive fails I can still boot even if it cannot boot all the data, backup or other linked partitions.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

    
If you want to move /boot it is just like a move of /home. You have to be sure to preserve ownership & permissions and add a new entry to fstab for the /boot partition.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue

---

### Post by lle on 2013-01-31
I have a fairly similar situation: I want to move /boot from /dev/sda1 to bigger partition, /dev/sdb1. I made too small a boot partition during installation, and now the new kernel won't fit.

System is Ubuntu Server 12.04 LTS.

First I made an ext3 partition sdb1 for new /boot. Then copied boot files to it:

```

mkdir /mnt/boot
mount /dev/sdb1 /mnt/boot
cp -a /boot/* /mnt/boot/

```then I made the following changes to /etc/fstab:

```

# /boot was on /dev/sda1 during installation
#UUID=fa813154-3586-494d-9acf-83ce02daee92 /boot           ext4    defaults        0       2
# new /boot, sdb1. 4 GiBs for kernels.
UUID=f016e578-c2f9-4e03-908b-6f043062134d /boot           ext3    defaults        0       2

```Question is, did I forget something, or may I reboot now from my new /boot? Is there some grub2 configuration or updating left to do?


Thank you in forward. I'm new to ubuntuforums, and sorry if the answer is somewhere around. Didn't find the direct answer though.

---

### Post by oldfred on 2013-01-31
I do not know copy command well and find myself getting into trouble on whether trailing / is required or not.

 I think with the / you get one level down?

---

### Post by lle on 2013-01-31
What do you mean? 

I copied everything inside /boot to /mnt/boot. It went okay and everything seems to be in right place. I'm just wondering, did I forget something and end up with non-bootable system.

---

### Post by oldfred on 2013-01-31
I just make sure I have a liveCD, Boot-Repair, or Supergrub handy and try it. Actually whenever I do something like that, I have all three. :)

---

### Post by lle on 2013-01-31
First try didn't work, had to restore fstab with livecd.

Turns out dpkg put the corrupted kernel, which ran out of space, on the boot partition and it won't boot.

I guess I now have to remove that corrupted kernel. However, I wonder why GRUB didnt let me choose which kernel to boot, altough I pressed shift while booting.

Do I have to install grub to same hard disk or partition as /boot?

---

### Post by oldfred on 2013-01-31
Better to have grub2's boot loader in the MBR of the drive you are booting.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by lle on 2013-01-31
Looks like BootInfo uses GUI? I don't have any guis installed on server distribution.

Anyway, I managed to copy GRUB2 configuration to the second hard drive (sdb) where /boot also now is. Also cleared the first hard drive's (sda) MBR, so only sdb's GRUB2 should now be loaded at reboot.

I used following commands. **sda** was my old drive and **sdb** new.

To copy sda MBR contents to sdb MBR. 

[LIST]
[*]446 bytes - Bootstrap.
[*]64 bytes - Partition table.
[*]2 bytes - Signature
[/LIST]
So I backed up all 512 bytes from sda, but only restored 446 of them to sdb to preserve the partition scheme of sdb.

```

dd if=/dev/sda of=/tmp/mbrsda.bak bs=512 count=1
dd if=/tmp/mbrsda.bak of=/dev/sdb bs=446 count=1

```

To clear sda's MBR. Again to preserve partition table, I only cleared first 446 bytes.
```

sudo dd if=/dev/null of=/dev/sda1 bs=446 count=1

```

Now my system boots from the new 4GiB /boot partition. 

I still weren't able to boot to my new kernel, but thats a whole new story;)

---

### Post by oldfred on 2013-01-31
You can use Boot-Repair from its own liveCD/DVD/Flash.

You may be able to boot with Supergrub.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by oscarivera9 on 2013-02-01
> **oldfred said:**
> How large is SSD?

I have a 60GB SDD with two installs of Ubuntu including my /home. I use about 9GB including the 2GB for /home but have all data on my rotating drive. And my /home is only that large as I still have .wine with Picasa in it.

If you just move /boot, you will only have grub & kernel not system.

Is /home a separate partition on rotating drive? Then a new install but mounting existing /home would be very quick & easy.  If not you can split /home and copy the data to a data partition on rotating drive and the hidden user settings into your SSD.

I prefer to make each drive fully bootable without any other drive. Then when one drive fails I can still boot even if it cannot boot all the data, backup or other linked partitions.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

    
If you want to move /boot it is just like a move of /home. You have to be sure to preserve ownership & permissions and add a new entry to fstab for the /boot partition.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue

So, let me see if I got this right.  You are basically recommending that I make a new partition and copy my /home to it, then do a fresh install but keep the (new) /home partition as my /home for the new install, and in theory that should help me keep my settings.  Is that correct?

You gave me some links and I went ahead and read through all of them and it seems like that's what you're suggesting.  I actually thought about that before.  However, the thing with my setup is that not only do I have to add gtk 3.x themes, icons, etc, make adjustments to my software sources including adding certain ppa's, create custom scripts to be run during startup, but I also have some software that I've paid for and I don't want to go through the hassle of reinstalling it. I don't think doing a fresh install but keeping my old /home would save me the hassle of doing everything that I mentioned, but if it works I'll definitely do it.
I was hoping there would be an easy way to keep my existing installation but make it boot from the SSD.  If there's no way to keep my existing installation but have it boot from my new SSD  I'll just keep what I have.  I may be getting a new 500GB SSD hybrid drive which would definitely help me with this situation if nothing else works.

---

### Post by oldfred on 2013-02-01
I do not know about the paid software. It that in / (root) like most software or in /home?

With Linux software is normally installed to the system and user configuration is in the hidden folders in /home. So splitting /home leaves the hidden user settings in /home, but moves just the user data from Documents, Video, Music, Downloads, etc. to a data partition(s). You keep a small /home folder in / (root) and link the data folders back into /home so it looks like a normal configuration.

With that configuration I have a 25GB / on my SSD with 9GB used and two 100GB data partitions on my rotating drive. One is still NTFS from when dual booting with Windows and the other is LInux data.

---

### Post by oscarivera9 on 2013-02-03
> **oldfred said:**
> I do not know about the paid software. It that in / (root) like most software or in /home?

With Linux software is normally installed to the system and user configuration is in the hidden folders in /home. So splitting /home leaves the hidden user settings in /home, but moves just the user data from Documents, Video, Music, Downloads, etc. to a data partition(s). You keep a small /home folder in / (root) and link the data folders back into /home so it looks like a normal configuration.

With that configuration I have a 25GB / on my SSD with 9GB used and two 100GB data partitions on my rotating drive. One is still NTFS from when dual booting with Windows and the other is LInux data.


Ubuntu Software Center installed my paid software in /opt.  I actually do have a separate 1TB data drive formatted as NTFS so that I can access the same data through Windows or Ubuntu.  Then I have a 750GB drive for my operating systems (Windows 7, Ubuntu 12.04.1, Fedora 18 & Slackware 14).
The whole concept of creating links is definitely something I'll be looking into and applying from now on.  I really appreciate the help you've given me.  You've touched on a couple of concepts that I hadn't thought about before but they really make sense.

There's something I just thought about that I hadn't mentioned.  I don't know too much about btrfs, but my current Ubuntu installation is all formatted btrfs.  I understand that one of the most attractive features of btrfs is the ability to create and restore snapshots.  If I were to create a snapshot of my current system, would that help me in any way?

---

### Post by darkod on 2013-02-03
From the original first post you mention moving /boot to a SSD but I don't think you will get any real benefits of the ssd speed unless you actually move the / partition there. The /boot just has few files, it actually works from / of course.

Since most SSDs are still small and depending how much data you have in your Home folder(s), you can use oldfred's suggestion to create /home also on the SSD but use it mainly for the hidden settings files, etc. Not for your big data like videos, photos, downloads...

You can do those with symlinks, or simply use other locations to keep them and remember what is where.

---

### Post by oldfred on 2013-02-03
Some discussion on btrfs. It still is considered experimental.

[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)

---

### Post by oscarivera9 on 2013-02-03
> **darkod said:**
> From the original first post you mention moving /boot to a SSD but I don't think you will get any real benefits of the ssd speed unless you actually move the / partition there. The /boot just has few files, it actually works from / of course.

Since most SSDs are still small and depending how much data you have in your Home folder(s), you can use oldfred's suggestion to create /home also on the SSD but use it mainly for the hidden settings files, etc. Not for your big data like videos, photos, downloads...

You can do those with symlinks, or simply use other locations to keep them and remember what is where.

> **oldfred said:**
> 
Is /home a separate partition on rotating drive? Then a new install but mounting existing /home would be very quick & easy.  If not you can split /home and copy the data to a data partition on rotating drive and the hidden user settings into your SSD.

I prefer to make each drive fully bootable without any other drive. Then when one drive fails I can still boot even if it cannot boot all the data, backup or other linked partitions.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.


It seems like the general consensus is that I will get the most benefit  out the SSD if I have my entire system ( / ) in the SSD.  I will go  ahead and do a fresh install and follow the advice you guys have been  giving me.  I will leave /home in the SSD but link my data to a  mechanical HDD.  Maybe I'll also put /opt in the mechanical drive so  that it doesn't have to be reformatted later when I do an update.  I'll be marking this thread as solved but if any of you guys think it's a bad idea to put /opt in my HDD please feel free to let me know.

Thanks for your help

---

