---
title: "Need help with partitioning scheme for dual boot"
date: 2019-11-27
forum: Installation &amp; Upgrades
---

### Post by redsnek on 2019-11-27
Hi everyone,

Though I am not entirely new to Linux or Ubuntu I feel pretty lost when it comes to creating a working partitioning scheme for my dual boot system. Especially since I worry about messing up my Windows 10 install. So I would be thankful for any help you can give me.

What I already have is Windows 10 installed on one NVMe drive, and a NTFS partition for sharing files between OS's taking up half the space of a new 500GB SSD (dev/sda). I want to install Ubuntu Budgie on the other half of sda, and I need to create partitions manually since the installer doesn't want to do what I want it to do automatically.

So, the plan is to just create / on the unallocated space, since I do not feel that I need a separate /home and so on. But the big question is, what do I do with the EFI partition, and where do I install the boot manager? The installer gives me the option whether to install the boot manager to the NVMe where Windows is already installed or to the new SSD. If I install to the NVMe drive, do I need an EFI partition on /dev/sda? Can I do this without messing with my Windows install? Or do I install the boot manager to /dev/sda and create a EFI partition? Does the EFI partition have anything to do with the boot loader? So many questions :)

I hope I have described my problem in an understandable way. Thanks in advance for any answers.


/redsnek

---

### Post by yancek on 2019-11-27
Best place to start to understand your situation is at the Ubuntu site below which explains in detail dual booting with windows 10 with EFI.  I would suggest reading through it carefully before beginning.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I would suggest that when you begin the install, you verify that the drive you want to install Ubuntu to is actually sda.  You can do that with GParted which is on the Ubuntu install media (DVD/USB).

>  the installer doesn't want to do what I want it to do automatically.

Most installers are not telepathic so it won't know what you "want it to do" and do it automatically.  This is a major reason for the manual options with installers which in Ubuntu is called 'Something Else'.  This is also the best option to use with a dual boot UEFI install.

The default with Ubuntu on an EFI system is to install the Grub EFI files to the EFI partition on the first drive.  In your case this will likely be the windows drive if windows 10 is a default EFI install.  This will not overwrite your windows EFI files but will create a separaate ubuntu directory on the EFI partition and place the Ubuntu EFI boot files there.   If you want a separate EFI partition on the drive on which you install Ubuntu, you will need to create it yourself before beginning the install and in all likelihood, dis-connect the windows drive so the Grub EFI boot files are not written to that drives EFI partition.  The EFI partition is essential for windows to boot from a GPT drive and as indicated above could contain your Ubuntu boot files.  I think reading through the link above should answer most of your questions, if not post back.

---

### Post by Dennis N on 2019-11-27
To install Ubuntu on the SATA SSD, you need an partition formatted ext4 on the SATA SSD for Ubuntu root partition. I use 25 gB as the partition size. No need for another EFI system partition on the SATA drive, since the Ubuntu grub boot loader can be installed on the same EFI partition on the NVMe drive used by Windows - it does not interfere with Windows, since they have separate folders for their boot files there.

---

### Post by oldfred on 2019-11-27
With UEFI Ubiquity ignores all the options on where to install boot loader. As posted above, it just uses first ESP, usually the Windows on. And that often is ok.

I do like to have an ESP on every drive and a way to boot from that drive in an emergency (I still have flash drives also for emergency boot.). 
So with every new drive I add an ESP as first partition, it actually only has to be within the first 2GB, but UEFI suggests it be first. Windows often makes it second or even third, but only smaller partitions in front of it.
My ESP on second drive, then is more of a place to backup the ESP on first drive.

The only way I have found with Ubiquity as installer is to force unmount & remount "correct" ESP in the middle of the install. Grub will install correctly to any drive. Other distributions will let you select where to install grub and those work. Old bugs, and having choice is vital if installing to a removable drive. 

       Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

---

### Post by redsnek on 2019-11-28
> **yancek said:**
> Most installers are not telepathic so it won't know what you "want it to do" and do it automatically.

So why don't use the telepathic ones ;)

Anyway, everything worked out fine thanks to you guys. I told the installer to install Grub to the NVMe drive with Windows installed to it, and used the available space on /dev/sda to install the root partition.


Thanks a bunch!

redsnek

---

