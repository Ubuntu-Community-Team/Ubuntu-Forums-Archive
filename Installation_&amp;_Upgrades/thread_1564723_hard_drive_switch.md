---
title: "hard drive switch"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by pokethesmot on 2010-08-30
i have a 200gb hard drive and im upgrading to a 1tb hard drive and i want all my stuff like settings and files on my new hard drive whats the best and easiest way to transfer all my stuff from the old hard drive to the new one

---

### Post by Herman on 2010-08-31
:D If I were in your position I would plug the new disc in beside the old one and boot a USB or Live CD Ubuntu.
Then I would use a dd command to copy the entire 200 GB disc to the 1000 GB disk and use GParted to resize it as desired.

Here's a link, [Learn The DD Command Revised]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") - Linux Questions.org - by awesome machine.

Something like the following should do the trick,
```
dd if=/dev/sdb of=/dev/sda bs=4096 conv=notrunc,noerror
```Where: your old disc is /dev/sdb and your new disc is /dev/sda, you must test this with 'sudo fdisk -lu' first or by taking a look with GParted.
Warning: Be careful not to reverse the dd command because it will do exactly as you tell it and if you get the command wrong you might lose any data you don't have a backup copy of.
If you're not sure what you're doing with the dd command then it would be better not to use it without help. If you read the page I linked you to and you understand it you will probably be okay.
There are other ways, but you did ask for the best and easiest. 
The dd command would be the fastest too.
If you had asked for the safest and most user friendly I would have recommended something else like clonezilla or maybe partimage.

---

### Post by pokethesmot on 2010-08-31
> **Herman said:**
> :D If I were in your position I would plug the new disc in beside the old one and boot a USB or Live CD Ubuntu.
Then I would use a dd command to copy the entire 200 GB disc to the 1000 GB disk and use GParted to resize it as desired.

Here's a link, [Learn The DD Command Revised]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") - Linux Questions.org - by awesome machine.

Something like the following should do the trick,
```
dd if=/dev/sdb of=/dev/sda bs=4096 conv=notrunc,noerror
```Where: your old disc is /dev/sdb and your new disc is /dev/sda, you must test this with 'sudo fdisk -lu' first or by taking a look with GParted.
Warning: Be careful not to reverse the dd command because it will do exactly as you tell it and if you get the command wrong you might co be
If you're not sure what you're doing with the dd command then it would be better not to use it without help. If you read the page I linked you to and you understand it you will probably be okay.
There are other ways, but you did ask for the best and easiest. 
The dd command would be the fastest too.
If you had asked for the safest and most user friendly I would have recommended something else like clonezilla or maybe partimage.

user friendly sounds good lol whats clonezilla

---

### Post by sikander3786 on 2010-08-31
> **pokethesmot said:**
> user friendly sounds good lol whats clonezilla

A cloning and backup software just like Norton Ghost.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by pokethesmot on 2010-09-16
i tried clonezilla and it said that there was an error and i tried ur code u listed and it said permission denied

---

### Post by pokethesmot on 2010-09-16
bump

---

### Post by pokethesmot on 2010-09-16
some one pleas help me

---

### Post by gordintoronto on 2010-09-16
I have taken a different approach. I got an adapter to use the old drive as an external drive. I installed from scratch on the new drive, then copied my data files over.

I exported my Evolution data and imported it on the new drive, and likewise with Firefox bookmarks.

---

### Post by pokethesmot on 2010-09-17
> **gordintoronto said:**
> I have taken a different approach. I got an adapter to use the old drive as an external drive. I installed from scratch on the new drive, then copied my data files over.

I exported my Evolution data and imported it on the new drive, and likewise with Firefox bookmarks.


does this mean u got to keep all ur add ons and settings

---

### Post by SlugSlug on 2010-09-17
> **pokethesmot said:**
> i tried clonezilla and it said that there was an error and i tried ur code u listed and it said permission denied


start it with sudo

---

### Post by pokethesmot on 2010-09-17
> **SlugSlug said:**
> start it with sudo


i got it all to work now i am having a problem resizing the partition i made a new thread about it im about to just say forget it and lose all my data and do a fresh install cuz there was no reason for me to get a 1tb if i still gotta use 200gb lol

---

### Post by Herman on 2010-09-17
:D Okay, so you used the dd command to make a perfect copy of one hard disk to your other hard disk. (So far so good).
That included the first sector of the hard disk, including the MBR, and the MBR contains the partition table. The partition table records the location and size of the partitions in your hard disk. Now you need to update your partition table in your 1000 GB HDD to tell it it's 1000 GB and not just 200 GB.

If you use the fdisk -lu command, you will see that your new 1000 GB hard disk and your old 200 GB hard disks have identical partitions, but fdisk will still report to you the correctly size of each hard disk drive.
```
sudo fdisk -lu
```

To upgrade the partition table in your new 1000 GB hard disk, I would use TestDisk, (sudo apt-get install testdisk), and have it write a new partition table after detecting your partitions. :D

---

### Post by Herman on 2010-09-17
You may use the following command to install TestDisk,
```
sudo apt-get install testdisk
```
Before using TestDisk, (or most programs that can write to the MBR), please alsway check your partition and hard disk numbers with fdisk,
```
sudo fdisk -lu
```
```
sudo testdisk /dev/sda
```
Where: /dev/sda is your 1000 GB hard disk to be worked on, as determined by the fdisk command output mentioned previously.

I just wrote a MBR from a 64 GB drive to a 320 GB drive and restored it again a couple of times to make sure I'm giving you the correct instructions, here's the procedure in case you're not familiar with TestDisk,
a) Select 'proceed'
b) continue
c) Intel
d) Analyse
e) Quick Search
f) Y or N for 'Yes' or 'No' when asked if the partititon was created under Vista.
g) TestDisk should now display a list of partitions for you to check
h) Press Enter
i) If happy, select [write] for TestDisk to write you a new MBR
j) Y to confirm
k) Quit, and then Quit again to exit TestDisk.

That's it, your 1000 GB HDD's MBR should be correct now. :D

---

### Post by gordintoronto on 2010-09-17
> **pokethesmot said:**
> does this mean u got to keep all ur add ons and settings

No, I was installing from scratch. I timed it so it was two years after my initial installation, so it was time for a new install.

---

### Post by Herman on 2010-09-17
Sorry if my ways and methods are getting a little old fashioned.
Since this post was started, I found out that most people are now using a program called 'Clonezilla' for this kind of work, and not the dd command.
I have used Clonezilla once but it was a while back and I don't remember now what it's like. Clonezilla is probably a safer and more user friendly way to do the same thing.

---

