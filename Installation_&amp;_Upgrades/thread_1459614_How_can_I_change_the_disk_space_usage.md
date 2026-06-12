---
title: "How can I change the disk space usage?"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by acej1995 on 2010-04-21
Ok, well I went to wubi-installer, and installed Ubuntu, and I love it, I don't want to go back to windows 7, but anyways, I set Ubuntu to my D: Drive, (200GB Space) and I installed Steam (Steampowered.com) to get my games on Ubuntu.  I installed all of my games, but here is a big problem, I can't figure out how to use more than 30GB on Ubuntu, it just doesn't work.  I got GParted, and the D: drive is set to 195 GB (200, but Ubuntu used 5GB).

Image here: [http://tinypic.com/view.php?pic=2wegp08&s=5](http://tinypic.com/view.php?pic=2wegp08&s=5)

What can I do?

---

### Post by oldfred on 2010-04-21
Wubi is a good way for windows users to tryout Ubuntu without having to reformat and add partitions. It is better than just the liveCD as you can save and update without losing the updates when you reboot. But you still boot thru windows and are  using NTFS.

It may be time to consider a true dual boot and install Ubuntu into its own partition(s). If you elect to have a separate /home you can install / (root) into 10-20GB, make swap equal to RAM memory and the rest /home. There is a way to mount your existing root.disk so you can copy all your existing files & hidden settings from your current home in wubi to the new install's /home.

---

### Post by acej1995 on 2010-04-21
Yes, I have 2 different Partitions, C: for windows 7(about 700-800GB Space), and D: (200GB Space) for my Ubuntu.  I used Disk Management on W7 to make seperate Drives.  I have nothing in my D: drive except my ubuntu files from Wubi-installer.

---

### Post by acej1995 on 2010-04-21
Is anyone willing to help out?

---

### Post by ajgreeny on 2010-04-21
If I were you I would uninstall the wubi version of ubuntu and then install it properly on to the separate partition.

Don't get confused about drives and partitions, windows calls everything a drive (C: D: etc etc) but it sounds as if you have a single drive, but now you have two partitions.

When you use the installer from the live disk desktop, you will need to chose manual partitioning when you get to that stage.

1.   Make a new extended partition on sda2 of the whole partition size, 200GB (probably sda2, but your D: drive in windows terminology)

2.   Make three logical partitions within that extended partition, 10GB with mountpoint root (/) formatted to ext4; a swap of about 2 or 3 GB formatted as linux swap, depending on your amount of ram, for which you do not need to set a mountpoint; and all the rest formatted as ext4 with mountpoint /home.

You may even prefer to do the partitioning in advance of the installation using gparted which is on the live CD.  In that case youwill again choose manual partitioning in your installation, but the partitions will already be there and you just will need to set the formatting and mountpoints.

---

### Post by acej1995 on 2010-04-21
I just tried that, and I keep getting an error, It's, O/I, or I/O - Unable to boot from disk

---

### Post by oldfred on 2010-04-22
Do you have a good bootable liveCD? The CD should not contain the .iso file but the extration of all the files so the CD is bootable. Some windows software has to be told explicitly to copy an ISO as an install and not just copy it.

---

### Post by acej1995 on 2010-04-22
Yea, the extraction of all the files, I burned them all from PowerISO

---

### Post by garvinrick4 on 2010-04-22
This is just getting way to difficult to do a simple install.
Put your install Ubuntu Cd in tray and restart and choose just to try Ubuntu not to install.
Open up a Terminal. Applications/Accessories to Terminal. Type in Code.

sudo fdisk -l  (that is a small L)

Copy and paste the results to this Thread and we can see how to install quickly.

If you already made a new partition it will show up. Linux uses sda1,sda2, sda3 and so on.
It is Like Windows C,D,E,F  and so on and on. But they mean the same.

When you install Ubuntu it has its own partioning software included in installation but no big deal we can use your new one if all looks good.

---

### Post by acej1995 on 2010-04-22
I get the same error, It wont let me run anything on the disk.

---

### Post by oldfred on 2010-04-22
Do you have any known working bootable CDs (even windows:)) to see if your CD works?

---

### Post by acej1995 on 2010-04-22
I have windows XP cd, but it goes straigt to a BSOD once its done unpacking all of the thing and hits the "Loading up Windows", then a BSOD, but yea I've installed stuff with CD's, like just now I installed Battlefield 2.

---

### Post by garvinrick4 on 2010-04-22
Go to this Link and download this Ubuntu file of version 9.10

Then BURN this to a CD at the slowest speed and then put the new cd in the tray and reboot. Pick just to try not to install. You will then be in a LiveCD and can run your Code: sudo fdisk -l like stated previously and post here.

Downloading a copy of 9.10 will take about 10 minutes and burning disk about 5 minutes. Booting it up about 2 minutes. 
So just a 17 minute procedure to get a good disk and this will be your install and live Cd disk that you keep around all the time.
 Just like Windows install disks or Macintosh disks that come from the factory. You are the Linux factory!!

---

### Post by garvinrick4 on 2010-04-23
> **acej1995 said:**
> I get the same error, It wont let me run anything on the disk.
Burn a new disk at a real slow speed. Should not have trouble booting off of a CD unless Cd is corrupt.

---

