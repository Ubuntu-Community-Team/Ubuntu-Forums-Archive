---
title: "Un/Installation Questions?"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by riechan on 2009-12-05
Okay, so right now I have Ubuntu (the Jaunty version) and Vista installed in my unit (Vista being my primary), and I'm thinking of upgrading to 7. My question is, do I have to uninstall Ubuntu first before I install 7?

---

### Post by MelDJ on 2009-12-05
see: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by riechan on 2009-12-05
@MelDJ: That sort of didn't answer the question. I was talking about Uninstalling Ubuntu first then formatting the primary HD partition to install Win7. I already know that it's better to install Ubuntu after Windows has been installed to the unit.

---

### Post by presence1960 on 2009-12-05
> **riechan said:**
> @MelDJ: That sort of didn't answer the question. I was talking about Uninstalling Ubuntu first then formatting the primary HD partition to install Win7. I already know that it's better to install Ubuntu after Windows has been installed to the unit.

You do not have to remove Ubuntu to install windows. 

I would back up my data, especially prior to doing any partitioning/OS installation operations. Then you can boot the Ubuntu Live CD or gparted Live CD to format the windows partition to NTFS. Then boot your Windows 7 install DVD and install to that NTFS partition. When install is complete boot into windows a couple times to make sure the install went well.

If windows is OK you will now have to restore GRUB since Windows 7 will have ovewrwritten it with it's own bootloader. If you don't know how to reinstall GRUB post back.

---

### Post by MelDJ on 2009-12-05
did you read the installing windows after ubuntu part? 
[B]and you did not say that you wanted to uninstall ubuntu in your first post
if you uninstall ubuntu, then you can install 7 and install ubuntu back
as said above backup first. or make an iso of your ubuntu with remastersys so you can easily install it back
[/B]

---

### Post by presence1960 on 2009-12-05
> **riechan said:**
> @MelDJ: That sort of didn't answer the question. I was talking about Uninstalling Ubuntu first then formatting the primary HD partition to install Win7. I already know that it's better to install Ubuntu after Windows has been installed to the unit.

Actually it did, just didn't give you a yes or no answer. If you read the link you will see it is telling you how to recover Ubuntu after installing windows. MelDJ just skipped to what I put last in my post

---

### Post by riechan on 2009-12-05
> **MelDJ said:**
> did you read the installing windows after ubuntu part? 
[B]and you did not say that you wanted to uninstall ubuntu in your first post
if you uninstall ubuntu, then you can install 7 and install ubuntu back
as said above backup first. or make an iso of your ubuntu with remastersys so you can easily install it back
[/B]

Yes. I did. Sorry, guess I replied a little too early. Anyways, how about completely uninstalling Ubuntu? Any linkie to it?

---

### Post by presence1960 on 2009-12-05
> **riechan said:**
> Yes. I did. Sorry, guess I replied a little too early. Anyways, how about completely uninstalling Ubuntu? Any linkie to it?

Why would you want to remove Ubuntu to install Windows, then only have to reinstall it again. That is a lot of work. Just installing windows and then getting all your drivers, software, peripherals, etc, etc working is a multi hour job. Unless your Ubuntu install is defective in some way I would leave it be. I would rather spend a few minutes restoring GRUB after installing windows rather than have to install my Ubuntu OS again, which was perfectly good in the first place. Seems very illogical and counterproductive to me.

---

### Post by riechan on 2009-12-05
No. What I mean is what if there comes a time when I need to uninstall Ubuntu. Of course I have to know that too! :D

---

### Post by MelDJ on 2009-12-05
you can install windows straight away and set it to format the whole drive to ntfs. that will remove windows.
I do not know how 7 is installed. but i am assuming its the same as xp

---

### Post by riechan on 2009-12-05
> **MelDJ said:**
> you can install windows straight away and set it to format the whole drive to ntfs. that will remove windows.
I do not know how 7 is installed. but i am assuming its the same as xp

So, will that also format the drive where Ubuntu is installed? Sorry! First time Ubuntu user here. :D

---

### Post by presence1960 on 2009-12-05
> **riechan said:**
> No. What I mean is what if there comes a time when I need to uninstall Ubuntu. Of course I have to know that too! :D

Use Ubuntu Live CD or gparted Live CD to delete all Ubuntu partitions. You can then format them to NTFS or if you want to redo everything with just windows after removing Ubuntu's partitions make one big NTFS partition using all the disk's space as NTFS then install windows. Or you can delete all partitions and leave the entire hard disk as unallocated space then install windows.

---

### Post by riechan on 2009-12-05
> **presence1960 said:**
> Use Ubuntu Live CD or gparted Live CD to delete all Ubuntu partitions. You can then format them to NTFS or if you want to redo everything with just windows after removing Ubuntu's partitions make one big NTFS partition using all the disk's space as NTFS then install windows. Or you can delete all partitions and leave the entire hard disk as unallocated space then install windows.

Thanks for this info. Thread resolved. :D

---

### Post by presence1960 on 2009-12-05
> **riechan said:**
> Thanks for this info. Thread resolved. :D

No problem. Mark thread as solved using thread tools on right top of thread window please.

---

### Post by riechan on 2009-12-09
Sorry. Thread not yet resolved. I have a problem on these steps:


[LIST=1]
[*]Tell GRUB where your Ubuntu partition is by entering 
[/LIST]

root (hdA,B)Where 'A' is the hard-drive number, starting at 0, and 'B' is the partition number, starting at 0. For example, if Ubuntu was installed on the second partition of the first hard-drive, the command should be 
root (hd0,1)
[LIST=1]
[*]Tell GRUB which drive to put the boot sector on 
[/LIST]

setup (hd0)(replacing 0, as above, if a drive other than the first is used as the boot device) 

How do I know what number my hard drive is? I have two primary partitions (C:, E:) and the one that is being used by Ubuntu on a single hard drive.

---

### Post by presence1960 on 2009-12-09
> **riechan said:**
> Sorry. Thread not yet resolved. I have a problem on these steps:


[LIST=1]
[*]Tell GRUB where your Ubuntu partition is by entering 
[/LIST]

root (hdA,B)Where 'A' is the hard-drive number, starting at 0, and 'B' is the partition number, starting at 0. For example, if Ubuntu was installed on the second partition of the first hard-drive, the command should be 
root (hd0,1)
[LIST=1]
[*]Tell GRUB which drive to put the boot sector on 
[/LIST]

setup (hd0)(replacing 0, as above, if a drive other than the first is used as the boot device) 

How do I know what number my hard drive is? I have two primary partitions (C:, E:) and the one that is being used by Ubuntu on a single hard drive.

forget C: & D: type terminology- that is how windows reports partitions/disks. Linux does not report them that way. In Linux disks are sda, sdb, sdc, etc. & partitions are sda1, sda2, sda3, etc. You can find out your partition table by running in terminal ```
sudo fdisk -l
``` That is a lowercase L in -l

What exactly are you trying to do? Your thread was about deleting Ubuntu. Fill us in on what you are trying to do and why. Then do this so we can better help you:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by darkod on 2009-12-09
> **riechan said:**
> Sorry. Thread not yet resolved. I have a problem on these steps:


[LIST=1]
[*]Tell GRUB where your Ubuntu partition is by entering
[/LIST]

root (hdA,B)Where 'A' is the hard-drive number, starting at 0, and 'B' is the partition number, starting at 0. For example, if Ubuntu was installed on the second partition of the first hard-drive, the command should be 
root (hd0,1)
[LIST=1]
[*]Tell GRUB which drive to put the boot sector on
[/LIST]

setup (hd0)(replacing 0, as above, if a drive other than the first is used as the boot device) 

How do I know what number my hard drive is? I have two primary partitions (C:, E:) and the one that is being used by Ubuntu on a single hard drive.

Boot with the cd and select Try Ubuntu. At the desktop open terminal and do:

To avoid confusion check your grub version with:
sudo grub-install -v

0.97 is for grub1 (or grub legacy), 1.97 is for grub2. Depending which one you have the install process is different. What you quoted is used for grub1.

To check your disks partitions:
sudo fdisk -l

On the ubuntu disk you would usually have one large ext3/ext4 partition and one smaller swap partition. Your large partition is your root partition.

If you are still confused post the results here and we'll help you figure it out.

---

