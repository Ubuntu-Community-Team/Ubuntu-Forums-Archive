---
title: "How to divide partitions"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by JohnJSal on 2008-05-03
Hello everyone. It's been a while since I installed Ubuntu and I wanted to do it again, but about halfway through the installation I wasn't remember as much as I thought I was about how to partition the HDD. I want to get it right the first time, so I stopped and decided to ask here first.

Here's what I'd like:

NTFS partition for Windows (10GB) - this is already there, just needs to be sized down

Ext3 partition for Ubuntu (48GB)
FAT32 partition for sharing (1GB)
swap partition (1GB)

So I see *how* to create these, but I was confuse about what, if anything, to put in the "mount" category. For the Windows partition, should that be "/windows" or should it just be blank?

For the Ubuntu partition, should it be "/"? What about the others?

I also didn't know what to put when it asked to put the partition at the beginning or end of the drive for the last three partitions, or what mounting to give them as well.

Are there any guides that cover this in enough detail so I won't make a wrong choice? Or if someone feels like explaining it, I'd appreciate that as well.

Thanks!

---

### Post by Pumalite on 2008-05-03
Post:
sudo fdisk -l

---

### Post by JohnJSal on 2008-05-03
> **Pumalite said:**
> Post:
sudo fdisk -l

Huh? I don't have Linux installed yet.

---

### Post by Pumalite on 2008-05-03
You can do it from your Live CD.

---

### Post by JohnJSal on 2008-05-03
> **Pumalite said:**
> You can do it from your Live CD.

Well what exactly is that? Does that tell me *everything* I need to know about all the options?

---

### Post by Pumalite on 2008-05-03
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by Rallg on 2008-05-03
My laptop came with Windows Vista. I now have Vista, Ubuntu amd64, Ubuntu i386, linux-swap, FAT32 for sharing, and a couple of manufacturer-supplied partitions that are not to be touched. Ignoring the "not to be touched" partitions, the remainder was 100Gb, originally all for Vista. Here is what I did:

Before repartitioning, I advise you to de-fragment your Windows partition. You might be able to get away with just letting the defragmenter run for an hour, rather than all the way.

You don't have to do it this way, but I firmly recommend that you shrink the Windows partition from within Vista (if you have Vista). The capability to shrink (not expand) is built into even the basic home edition. You do it in Vista via the Administration control panel, storage. Vista will calculate the amount of available free space for shrinking, which is actually less than the total amount of free space (the better you defragmented, the more you can shrink). Of course, do not shrink too much, since you'll still need some space to work within Windows.

If you don't have Vista, or if you simply don't want to use its built-in shrinker, then you can use GParted from the Ubuntu live CD. Actually, I prefer to use a separate CD for this purpose (System Rescue CD) because it is not also an installer, so I cannot confuse creating partitions with using them.

I firmly recommend that you first create all necessary partitions when NOT part of the install process. That reduces the chance of error if you click the wrong button, in my experience.

How much space to allot will depend on your usage. My Ubuntu amd64 partition has a complete compiling environment and all the major applications. I gave it 12Gb. My Ubuntu i386 partition is very stripped-down, primarily used by guests for surfing the Internet. I gave it only 4.7Gb. My RAM is 2GB, so I allowed the maximum 4Gb for linux-swap (you can use less than 2x your RAM, but I believe the minimum is 256Mb swap). If you have more than one Linux installation, you only need one swap.

For my shared FAT32, I gave it a few Gb.

Understand that I don't do heavy multimedia. If you are working with large files, you may need more. If not, you can get by with less.

So, let's go back to partitioning. In Vista, after defragmenting, I shrunk my Vista partition by an amount equal to the sum of my planned two Ubuntus, swap, and shared. If you are shrinking Windows via Gparted, first you will shrink the Windows partition by an appropriate amount equal to the sum of space needed.

Once the space has been carved from Windows, in GParted I select the unused space, and define it as an extended partition. For now, it can be formatted as ext3 or whatever you like (it will be re-formatted later).

After creating the extended partition, I shrink it within GParted, and create a new logical partition to be used for whatever. Then I shrink the extended partition again, creating aanother logical partition. In the end, my extended partition was carbed into FAT32, ext3 for Ubuntu amd64, linux-swap, and ext3 for Ubuntu i386.

You may find that between partitions there are a few unallocated Mb, due to alignment with cylinders. Do not attempt to squeeze them out.

DO NOT move the starting point of your Windows partition! In some cases, Windows uses its parition starting point as one of several factors determining if your software is "valid."

DO NOT use GParted to give any partition a "label." That is a technical factor that will mung your system if you do it. You don't need it.

Got partitions? Then boot the Ubuntu installer. Under no circumstances play with the Windows partition. Instead, when you get to the list of available partitions, select the one you want for Ubuntu. Click it, and choose Edit. Choose "use as /" which is your Ubuntu root, and re-format it (suggested ext3). If the installer did not automatically select your linux-swap partition for use as swap, do it yourself (but I believe this is automatic). Do not play with any other partitions.

Some users have a separate partition for "/home" when multiple Linux installations are present. This is not mandatory whether or not you have multiple Linux. If you on't know what I am talking about, just forget it.

So, now you have selected your root and swap. That's it. In the installer, go the to next step where it summarizes actions. Notice that there is an "Advanced" button. This is where you can instruct Ubuntu to put the Grub installer somewhere other than the default location. If you accept the default, the installer will mark your drive's master boot record (MBR) so that it is directed to Grub on (hd0,0). This is not appropriate for everyone, but telling all the possibilities is another story. Just keep in mind that if you later remove Ubuntu, then you wil either have to live with the leftover Grub, or restore the MBR using Windows' own installer or recovery software (methods for XP and Vista differ).

You do not need to fool with your FAT32 partition in the Ubuntu installer. Definitely do not fool with the Windows partition, or any other. If you have multiple Linux, each one will use its own root (/) when it installs. If you are re-installing Linux over a prior installation on the same partition, be sure to re-format it so that prior files are erased.

Once you have Ubuntu up and running, you can determine which parititons (volumes) are allowed to auto-mount at startup, by using the terminal command
sudo gedit /etc/fstab
and commenting out anything you do not want to mount. Note that Ubuntu (and other contemporary Linux) use UUID as mount identifiers. A partition's UUID changes whenever you re-format it.

IMPORTANT: During installation, Ubuntu will count your hard deive's partitions as /dev/sda1, /dev/sda2, etc. But Grub counts them as (hd0,0), (hd0,1), etc. Notice the 1-offset. Also notice that your extended partiton, taken as a group, may have a device identifier. Have pen and paper to write things down as you work, lest you mis-install your boot loader or install Ubuntu to the wrong partition.

---

