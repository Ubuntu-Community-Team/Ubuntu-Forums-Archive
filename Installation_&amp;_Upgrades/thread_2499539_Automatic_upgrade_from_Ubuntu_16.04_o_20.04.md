---
title: "Automatic upgrade from Ubuntu 16.04 o 20.04"
date: 2024-07-30
forum: Installation &amp; Upgrades
---

### Post by rpstew on 2024-07-30
I have hardware with a single SSD imaged with six partitions:
[LIST=1]
[*]EFI
[*]/boot
[*]swap
[*]recovery (Ubuntu Server 16.04)
[*]/ (Ubuntu Desktop 16.04)
[*]/home
[/LIST]

I also have another image that is very similar, but with 20.04:

[LIST=1]
[*]EFI
[*]/boot
[*]swap
[*]recovery (Ubuntu Server 20.04)
[*]/ (Ubuntu Desktop 20.04)
[*]/home
[/LIST]

I have been tasked with coming up with an automatic upgrade process from Ubuntu 16.04 to 20.04.  I have a process in place that overwrites the Ubuntu Desktop 16.04 partition (partition 5) with the Ubuntu Desktop 20.04 partition.  This is done from the recovery partition using "partimage -b restore".  Only the 5th partition is overwritten.  After that process the hardware fails to boot with the following error: 
 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=294033&stc=1[/IMG]


I ran the boot-info tool and got the following:  [https://paste.ubuntu.com/p/gMHZ8Nnm7H/](https://paste.ubuntu.com/p/gMHZ8Nnm7H/)
I notice several issues in those logs:
[LIST]
[*]line 67: Normal Mode shows 16.04, but should show 20.04
[*]line 109: grub-pc added (not sure if this is an actual issue or not)
[*]line 117: fstab-has-bad-efi
[*]line 125: fstab-has-bad-boot
[*]line 165: UUID changed of partition 5 (this is expected)
[/LIST]
I'm not sure how to address these issue.  Please advise.

---

### Post by TheFu on 2024-07-30
Going from 16.04 --> 18.04 --> 20.04 is the approved method.  BTW, standard support for most flavors of 20.04 end next April, so I'd strongly suggest you push management to 22.04, as a minimal upgrade.

I've not had much success doing 2 LTS upgrades.  1 seems to mostly work, however.  After 2, there is a bunch of cruft left over since many subsystems change between different LTS releases.

BTW, standard support for 16.04 ended in 2021, so unless you have an ESM agreement (now called "Pro"), the repos you need aren't available.

If it were me, I'd just backup the data for each install  and do a fresh install to avoid the issues and cruft.  All sorts of things that weren't done in the older releases are handled in the newer ones.

Also, you really should be certain that the target OS version works for each of the different groups.  Canonical has "improved" a few things to the point that they don't work anymore, especially in a business environment with centralized storage and account management.  Some of the suggested workarounds are worse than just using a different base OS, at least for us.

Oh ... and the way Ubuntu boots has changed a bunch between 16.04 and 20.04, so there is that issue you need to solve.  Most people just do a fresh install to get the needed updates for boot stuff.

---

### Post by yancek on 2024-07-30
You are aware that 16.04 has not been supported for over 3 years, right?  Support for 20.04 will end in less than 9 months.

If you look at line 193 in boot repair, you will see that this is the EFI parition sda1=search.fs_uuid 18570a9f-c96f-4e70-9cce-453a1cef1774 root hd0,gpt4.  This is the entry in the grub.cfg file on your EFI partition which as you can see, is pointing to sda4.  The UUID shown in the image you posted is for sda5.

Some other things other than using outdated systems are the fact that you have a menu.lst file showing on your 16.04 partition (sda4) which has not been used in a default Ubuntu for almost 15 years.

What is sda2?  Is that a separate /boot partition?  There is a grub.cfg file there??  You also have a grub.cfg file on sda4 in addition to the one on sda1 (EFI).  Did you install 20.04 with a separate boot partition and not do that with 16.04?  That's what it appears to be.

If you want to move the boot to the 20.04 system you moved from sda5 to sda4 you need to change the grub.cfg entry on sda1 to point to the sda5 UUID.  If however, you have Ubuntu 20.04 installed on sda5 with a separate /boot partition (sda2) this won't help.  Looks like a real mess.  You might try backing up your data and installing a newer version of Ubuntu.

Do you get the error you posted in the image when you have moved 20.04 from sda5 to sda4 and just rebooted.  You can't expect it to work if you only move the OS partition (sda5) to another without modifying the files on the EFI partition (sda1) and possible sda2 if that is actually a boot partition.  Good Luck!

---

### Post by rpstew on 2024-07-30
I am aware of 16.04 no longer being supported and that 20.04 will soon stop being supported.  I am working on a new custom image for 24.04. 

The original designer/developer of the system no longer works with us.  As far as I can tell, the boot partition (2nd partition) is not being used.  When I create our custom images I boot into the recovery partition (4th partition - Ubuntu Server) which has its own /boot directory.  From that partition I run the commands to create the grub menu:
$ grub-install /dev/sda
$ update-grub

By default, partition 5 is booted into which is Ubuntu Desktop.  Partition 4 (Ubuntu Server) can also be booted into by pressing <ESC> during booting process and choosing a grub menu entry.  Booting into partition 5 is what is failing now after overwriting that partition.  Partition 4 still boots successfully.

I also ran the boot-info tool on our working 16.04 and 20.04 devices for comparison:
* 16.04: [https://paste.ubuntu.com/p/4sXzpgvKrY/](https://paste.ubuntu.com/p/4sXzpgvKrY/)
* 20.04: [https://paste.ubuntu.com/p/D3ZBdh8dDG/](https://paste.ubuntu.com/p/D3ZBdh8dDG/)

I only overwrote partition 5 on the 16.04 device with partition 5 from the 20.04 device.  After that you get the failure to boot into the default partition 5.  I'm assuming I have the partition UUIDs messed up some how.

---

### Post by yancek on 2024-07-31
Your boot repair output clearly shows that /dev/sda2 is a separate boot partition but it is not possible to tell if it is used.
The boot repair run from 16.04 shows this entry in the EFI grub.cfg file:

```
search.fs_uuid 18570a9f-c96f-4e70-9cce-453a1cef1774 root hd0,gpt4 
```

That is pointing to the grub.cfg file on sda4, the 16.04 grub.cfg file.  If you scroll down to the blkid output in that boot repair, you clearly see that is the correct UUID for partition 4 so that means that the EFI partition boots to the grub.cfg on sda4 (16.04) but we don't see that grub.cfg file so don't know which OS it boots to.  20.04 could be the default.

Are you using images from 2 different drives?

The second boot repair which you ran from 20.04 shows the below entry for the EFI file on line 193 which clearly shows a different UUID:

> search.fs_uuid 8fb26d47-14fe-41dd-8cf6-62a406e887aa root hd0,gpt4  

If you look at the boot repair from 20.04 you can see the blkid for that entry is: 

> sda4 ext3     8fb26d47-14fe-41dd-8cf6-62a406e887aa  

Compare the UUIDs in the 2 boot repair outputs.  They are all different.  
Have you tried simply copying sda5 to sda4 overwriting 16.04 and then changing the UUID in the EFI/ubuntu/grub.cfg file to the UUID that 20.04 had?  Before doing that, you would need to run the blkid command to get the correct UUID for the partition to boot.

This is done from the recovery partition using "partimage -b restore".  Only the 5th partition is overwritten.  You have an EFI system, that won't work.  You need to change the EFI partition, particularly the grub.cfg file there so that it points to the correct partition by UUI, the partition on which the Grub bootloader exists.

---

### Post by rpstew on 2024-08-02
The kernel and initramfs files are stored in the boot partition (/dev/sda2).  I copied in the new kernel and initramfs files (20.04) into that partition.  The grub menu is created from partition 4 which has its own /boot directory.  There is a script in the /etc/grub.d directory in partition 4 that is used to create the grub menu.  That script calls the "linux-boot-prober" command, but it is returning nothing for partition 5:
#  linux-boot-prober /dev/sda5
#
That is the currently issue I am facing.  I'm not sure what linux-boot-prober is doing under the hood, but I'm sure I need to modify something to get it to work with the modified partition (partition 5).

Again this is a dual boot disk which can be booted into both partition 4 and partition 5.

---

### Post by rpstew on 2024-08-06
I fixed the linux-boot-prober issue.  Debug messages show up in the /var/log/syslog file when executing that command.  The linux-boot-prober checks /etc/fstab on the passed in partition.  After cloning the /dev/sda5 Ubuntu 20.04 partition over the /dev/sda5 Ubuntu 16.04 partition I had to update the UUID pointed to in /etc/fstab on /dev/sda5 partition to point to the proper UUID for the boot partition (/dev/sda2).  The UUID for /dev/sda2 is obviously different between the Ubuntu 16.04 drive and Ubuntu 20.04 drive.

I still have work to do to get the Ubuntu 20.04 to work, but I am past the booting issue.

---

### Post by rpstew on 2024-08-12
The linux-boot-prober was returning nothing before I fixed the UUID issue.  That command is now returning kernel information, but not the new kernel (20.04), just the old kernel (16.04).

---

### Post by rpstew on 2024-08-13
I was able to get the new kernel to show up with the linux-boot-prober command.  That command in addition to using the /etc/fstab for the input partition also parses the /boot/grub/grub.cfg file for kernels so I had to copy the /boot/grub/grub.cfg file from the Ubuntu 20.04 image.  Everything seems to be working now.

---

