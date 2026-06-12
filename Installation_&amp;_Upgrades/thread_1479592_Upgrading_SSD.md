---
title: "Upgrading SSD"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Paper Pusher on 2010-05-10
I have an ASUS 900a with a 4GB SSD running Ubuntu NBR 9.10.
It has several accounts and associated data on it.
How do I save the accounts and data as I upgrade the SSD?
I have an 8GB USB drive, an external HHD, and an external DVD burner available.
I suspect that clonezilla will be part of the answer, but I don't know how to put the pieces together.

---

### Post by narendraD on 2010-05-10
I think i have not understood your problem correctly.
Are you thinking of upgrading to a bigger SSD or just upgrading the 9.10 on the SSD to 10.04.
If its the former then yes Clonezilla is the answer, but a fresh install will always be better after you copy all the data and settings. A fresh install may not need clonezilla. 

If the latter, again backup all data and settings, then try and upgrade and hope for the best. 

Because you have means to copy your data and settings, I would recommend a fresh install if that is what you are looking for.

---

### Post by Paper Pusher on 2010-05-11
Thank you for the quick reply.  I apologize for being unclear.

I am replacing the current small 4GB SSD with a larger 32GB one.
I will gladly do a fresh install of Ubuntu NBR.  I simply want to save my current accounts, their settings and their files.  How do I do that?

---

### Post by narendraD on 2010-05-11
While i dont think you can save accounts, you certainly can save the settings and their files. Then you need to recreate the same accounts with the same names and passwords in the new install and copy over the settings and files. The settings are normally saves in the user folder in /home as .files and .folders (hidden) which can be seen CTRL+H in nautilus. Copy all of them along with all user data like photos, videos and music. then reinstall and recreate your users and copy over their respective settings into their respective folders in /home.

Would also advice you to go for a separate /home partition now that you are doing a fresh install. There are enough resources for teaching yopu how to create a separate /home.

---

### Post by Paper Pusher on 2010-05-12
I want to take your advice about the /home partition.  Where do I find out more?

Also, there is no role for clonezilla for me.  Right?

---

### Post by Paper Pusher on 2010-05-12
I cannot find .files nor .folders or any hidden files in /home.
View hidden files is turned on.
:confused:

---

### Post by narendraD on 2010-05-12
> **Paper Pusher said:**
> I cannot find .files nor .folders or any hidden files in /home.
View hidden files is turned on.
:confused:


They are in /home/username where username is the name of the user. 
Look at [http://ubuntuforums.org/showthread.php?t=1480523](http://ubuntuforums.org/showthread.php?t=1480523) for formating

---

### Post by Paper Pusher on 2010-05-12
Thanks for the link.

It looks like the following approach may have merit:
[LIST=1]
[*]Download a copy of Ubuntu 10.4 NBR and burn it to a CD-R on my dektop.
[*]Create a USB Start Up Disk using the CD-R on a thumb drive on my Ubuntu 9.10 desktop.
[*]Write a script that uses the adduser command to add the users I need.  Store the script on thumb drive #2.
[*]Copy all home folders (/home/*) on my 4GB SSD netbook to thumb drive #2.
[*]Edit the file .profile in each user's home directory to start the standard /usr/bin/oocalc .ods spreadsheet on login.  I did this interactively for each user using System>Preferences>Startup Applications, but for some reason it doesn't show in their .profile.
[*]Change the boot sequence of my netbook to look on the USB port first.
[*]Install the new larger 32GB SSD in the netbook.
[*]Use the USB start up disk to install Ubuntu 10.4 NBR with the /home partition you suggested.
[*]Restore the original boot sequence.
[*]Download and install a local OpenOffice.org. UNBR 9.10 came with one. I hear that UNBR 10.4 does not.
[*]Install thumb drive #2 and run the adduser script.
[*]Copy the original home folders back. 
[/LIST]

Whew!  I hope this is right.  Is it?

---

### Post by igf1 on 2010-05-13
Ok, I just did this the other day. There are three things that you should do.

1. upgrade to to the upstream .33 Kernel for Trim support.
2. remove journaling (if your using EXT4) 

for these two steps, edit fstab and put this at the end of the drive. noatime,discard

the first (noatime) is to disable journaling, the second enables TRIM in the .33 kernel. 

Now for the fun stuff :) Aligning your drive.... I booted from another disk, copied everything from the root to the space on that drive (yeah just copied everything from /) and then did the fdisk thing to align the drive on 64/128k 

this is the difference each step made in the drives performance. 

(the format was funky so I touched up the output for reading)
---------------------------
richard@richard-desktop:~$ sudo hdparm -tT /dev/sda
[sudo] password for richard: 

~Before disabling journaling: /dev/sda
 Timing cached reads:1848 MB in  2.00 seconds = 924.80 MB/sec
 Timing buffered disk reads:309 MB in 3 seconds = 103 MB/sec

~After disabling journaling: /dev/sda
 Timing cached reads:2618 MB in  2.00 seconds = 1308.80 MB/sec
 Timing buffered disk reads:464 MB in  3 seconds = 154.41 MB/sec

~After Aligning: /dev/sda
 Timing cached reads:5516 MB in  2.00 seconds = 2759.32 MB/sec
 Timing buffered disk reads:486 MB in  3 seconds = 161.58 MB/sec


As you can see, Aligning is rather important, disabling journaling is up to you, I actually did it ONLY because I know Im about to format and start over with 64bit ubuntu as soon as the RAM arrives. 

This is where I got the info for aligning: [http://bryan.larsen.st/2009/3/23/using-a-vertex-ssd-with-ubuntu-jaunty](http://bryan.larsen.st/2009/3/23/using-a-vertex-ssd-with-ubuntu-jaunty)


update kernel
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb)

add this to fstab
ext4   noatime,discard,errors=remount-ro 0       1


you need to align partitions on at least 128k boundaries for maximum efficiency. 
use 224 (32*7) heads and 56 (8*7) sectors/track.  This results in 12544 (or 256*49) sectors/cylinder, so that each cylinder is 49*128k.  You can do this by doing starting fdisk with the following options when first partitioning the SSD:
# fdisk -H 224 -S 56 /dev/sdb

[http://www.linuxfoundation.org/news-media/blogs/browse/2009/02/aligning-filesystems-ssd%E2%80%99s-erase-block-size](http://www.linuxfoundation.org/news-media/blogs/browse/2009/02/aligning-filesystems-ssd%E2%80%99s-erase-block-size)


disk bench
[http://sourceforge.net/projects/diskgui/files/](http://sourceforge.net/projects/diskgui/files/)

( before aligning )
high: 216.11 mbs
low: 163.37
avg: 204.55

( after )
high: 245.40 mbs
low: 192.75
avg: 214.92


-- Richard Corsale

---

### Post by Paper Pusher on 2010-05-13
Thanks for all the good ideas. 
My head is spinning!
Yes, I want to use the .33 kernel.
Yes, I want to use TRIM support.
Yes, I want to use EXT4.
Yes, I want to turn off journalling. Journalling causes extra writes which reduces the lifespan of my new SSD.
Yes, I like your performance numbers, but how do I put the pieces together? How will this fit into my “twelve step plan”?

---

### Post by igf1 on 2010-05-14
> **Paper Pusher said:**
> Thanks for all the good ideas. 
My head is spinning!
Yes, I want to use the .33 kernel.
Yes, I want to use TRIM support.
Yes, I want to use EXT4.
Yes, I want to turn off journalling. Journalling causes extra writes which reduces the lifespan of my new SSD.
Yes, I like your performance numbers, but how do I put the pieces together? How will this fit into my “twelve step plan”?


Well, the first step is admitting you have a problem :) 

Seriously though I would do this in order, 
1. install ubi10.04 clean on the target drive. 
2. update kernel to .33
3. modify fstab with the flags I posted and reboot
4. now, boot to another harddrive with ubi on it and see that 
the target drive is ok, at this point mount the target and simply copy the files over from the SSD install to the drive your sitting on. 

5. unmount the drive and run fdisk ```
fdisk -H 224 -S 56 /dev/sda
```  (assuming that your SSD Drive is /sda)

6. now, in the fdisk shell enter the following:
'n, p, 1, 1, 5082' create a partition
'x, b, 1, 256' to move the start of the partition into alignment

then w (to write the partition) and exit.

7. for a 32 gig drive enter: ```
mke2fs -t ext4 -E stripe-width=32,resize=50G /dev/sda1 
```

8. now you have a perfectly optimized 32 gig drive! you just have to get the UUID of the new drive and set the bootable flag. do this with Gparted ( ```
sudo apt-get install gparted

``` ) it's now under system->administration. Start that and you can see your new drive (theres a list of the drives in a dropdown if it's not sda). 

9. In gparted Right click it and select information. copy it's UUID and note the first sector is set to 256. You might have lost a few meg of space but it's worth it.

10. now right click the drive again and select "manage flags". This brings up the menu and you want to set the boot flag. 

11. goto your directory where you had the backup and edit the fstab changing the UUID of the drive to the new one. then do the same in the  /boot/grub/grub.conf. just do a search and replace of the old with the new UUID

12. It's been a long day, go get a beer or ten! I wish all 12 step programs ended this way :)

In Closing...
when you reboot run the after benchmarks and you can see that your drive will scream by the before benchmarks if you took them. I cant even see the loading of ubuntu on my system. It's basically instant on. Though the post login wait is really lame (Mark, seriously?? That's just cheesy)

---

