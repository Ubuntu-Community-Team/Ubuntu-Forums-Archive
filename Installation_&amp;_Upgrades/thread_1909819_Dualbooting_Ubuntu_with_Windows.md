---
title: "Dualbooting Ubuntu with Windows"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by AZBoy28 on 2012-01-16
Hey.

I'm wanting to Dualboot Ubuntu (10.04, 10.10 or 11.10) with Windows 7.

So  far hasn't been good, I have got into Live USB mode (on both 10.04 and  11.10) and have started the installation process, however when it gets  to where it asks how I want it to be installed (pictured below) thats  where the problem starts.


[IMG]http://cloud.addictivetips.com/wp-content/uploads/2011/06/Windows-7.jpg[/IMG]

[IMG]http://http//cloud.addictivetips.com/wp-content/uploads/2011/06/Windows-7.jpg[/IMG]
 

The  problem is, that I don't get the option to 'Install Ubuntu alongide  them' (first option) which I need to dualbooth with Windows. I only get  'Erase disk and install Ubuntu' and 'Something Else'

PLEASE HELP!!!

---

### Post by carl4926 on 2012-01-16
We need to see the result of this from a terminal in the Ubuntu Live session
```
sudo fdisk -l
```

Many windows installations come in such a way that you cannot install without some major adjustment.

---

### Post by AZBoy28 on 2012-01-16
Thanks for your reply, I'm personally not that good with the Terminal, I'm still new to Ubuntu. 

What is the problem with my Ubuntu Installation?

---

### Post by Wug on 2012-01-16
I don't see your picture.

However you may be able to get it working with the 'something else' option.

I HIGHLY SUGGEST you consult someone you know who already uses linux and has set up partitions before.

If you're quite sure you can do this without help, you will need to do the following:

0) backup everything you cant afford to lose

1) read all of the steps before doing anything, so you know what you will be doing and can put it on hold and ask if something appears different.  If at any time something seems weird about it, post.  you might be able to get a browser running from within the installation environment, which will help you post screenshots and stuff.

2) disconnect USB devices like external hard drives, they will make things more confusing

3) run the installer, proceed to point of confusion

4) select "something else"

5) determine which disk you are trying to install on (if you only have one hard disk it will be the only one)

6) resize the existing partitions to make space for a new one (if there is not already space).  You can make it as small as 2GB, but I recommend something larger.

7) create a new ext4 partition in the empty space you created in step 6

8) under the options for the new ext4 partition, select / as the mount point

9) the installer will prompt you to confirm before making any changes, and will perform them all at once.  Once it asks you to confirm, go back and double check.  Ensure that you still recognize the old windows partition.  Do a sanity check to make sure you're not accidentally doing something really stupid.

10) confirm the changes and continue with the installation.

---

### Post by AZBoy28 on 2012-01-16
Thanks, I have put the picture back on ;)

I will try it, if I don't have any other choice!

---

### Post by carl4926 on 2012-01-16
Better going this route
[http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10_go_advanced_partit.png](http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10_go_advanced_partit.png)

---

### Post by mastablasta on 2012-01-16
> **AZBoy28 said:**
> 
 
 
The problem is, that I don't get the option to 'Install Ubuntu alongide them' (first option) which I need to dualbooth with Windows. I only get 'Erase disk and install Ubuntu' and 'Something Else'
 
PLEASE HELP!!!
 
you need to have an empty disk space for the option to show. empty partition that is not formated to any file system.
 
additionally you must not have too many primary partitions already on the disk (you can have extended). i think limit is 4.

---

### Post by AZBoy28 on 2012-01-16
Thanks for your replys :)

I'll create myself a new partition. How exactly do I make one? (do I use the Ubuntu Installer or do I have to download a program etc..)

---

### Post by carl4926 on 2012-01-16
You need to run the Live CD
Open a terminal
Post result of

```
sudo fdisk -l
```

---

### Post by AZBoy28 on 2012-01-16
> **carl4926 said:**
> Better going this route
[http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10_go_advanced_partit.png](http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10_go_advanced_partit.png)

 Thats exactly what shows up on my installer! I will use that route =)

---

### Post by carl4926 on 2012-01-16
> **AZBoy28 said:**
> Thats exactly what shows up on my installer! I will use that route =)

You have been warned about the possible existence of 4 primary partitions

Please post the fdisk info asked for

---

### Post by AZBoy28 on 2012-01-16
Okay, I'll do that tomorrow!

---

### Post by mastablasta on 2012-01-16
> **AZBoy28 said:**
> Thanks for your replys :)
 
I'll create myself a new partition. How exactly do I make one? (do I use the Ubuntu Installer or do I have to download a program etc..)
 
 
windows has a disk manager in accessories!? not really sure where is is in Win7.
 
here maybe this can help: [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
 
 
Make sure you defrag the disk 2 times (second time will be fast) and also run a checkdisk before partitioning. that way you minimise the chance of something going wrong and data loss. defrag will make sure data is clustered together so that free disk space is really free.

---

### Post by AZBoy28 on 2012-01-17
> **carl4926 said:**
> We need to see the result of this from a terminal in the Ubuntu Live session
```
sudo fdisk -l
```Many windows installations come in such a way that you cannot install without some major adjustment.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd7e2d7e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       37569   300228608    7  HPFS/NTFS
/dev/sda3           37569       38914    10805248   17  Hidden HPFS/NTFS

Disk /dev/sdb: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004b2ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         245     1967931    6  FAT16
ubuntu@ubuntu:~$ 

```

---

### Post by AZBoy28 on 2012-01-17
Hope this helps =)

---

### Post by carl4926 on 2012-01-17
OK
Great

You can install. But here is what I recommend.
First backup any important files in windows
Next defragment it
Determine how much free space you have in windows (That's sda2 in your output, just FYI)
Download Parted Magic and boot from it
Use the Partition editor to highlight sda2 and resize it
Drag the slider to take up **only half of the Free space** in sda2
Apply it
When done, highlight the free space you just created and select New > Extended partition type
Highlight the extended space and do New > swap 2GB (Or equal to your RAM)
Highlight the Extended and do New ext4 20GB
Highlight the Extended and do New ext4 and let it use all the remaining free space
Apply
[COLOR=DarkRed](N.B. If the last ext4 above is smaller than the the first 20GB, you should just create one ext4 after swap and let it use all the free space)[/COLOR]

Now boot Ubuntu and go this route
[http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10_go_advanced_partit.png](http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10_go_advanced_partit.png)
In the advanced partitioner double click the 20GB ext4 and use as ext4 and mount as /
Double clcik the second ext4 and use as ext4 and mount as /home
[COLOR=DarkRed](If you only have one ext4 it's mount is /)[/COLOR]
swap will sort itself
Then proceed with the rest of the install setup

---

### Post by carl4926 on 2012-01-17
This will give you an idea, but it's NOT an exact representation of what I describe
[http://dl.dropbox.com/u/10573557/Partitioning%20example%20win7-linux.mpeg](http://dl.dropbox.com/u/10573557/Partitioning%20example%20win7-linux.mpeg)

Parted Magic
[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

---

### Post by carl4926 on 2012-01-17
Here, I did a video a little closer to what you need.
Sorry it's in a SUSE machine
[http://dl.dropbox.com/u/10573557/win_lin_partitions.m4v](http://dl.dropbox.com/u/10573557/win_lin_partitions.m4v)

---

### Post by AZBoy28 on 2012-01-17
Thanks for your reply =)

So do I use GParted or Parted Magic?


[B] 
[/B]

---

### Post by carl4926 on 2012-01-17
> **AZBoy28 said:**
> Thanks for your reply =)

So do I use GParted or Parted Magic?



Either
I always use Parted Magic, but it uses gparted as the partition editor

gparted is in the ubuntu live cd, so if you have that....

---

### Post by AZBoy28 on 2012-01-17
Awesome =)

I have just finished downloading Parted Magic. I'll try GParted first :)

Thanks for your help =)

---

### Post by nipunshakya on 2012-01-17
Hi. sorry i didn't read all of the above stuff. But somewhere i felt like u needed help with the partitions. 
I run a dual-boot too and someone in this forum once suggested me the following site :
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

Hope it helps.

Regards,WinuxUser

---

### Post by Mark Phelps on 2012-01-17
Do NOT use the slider to resize sda2!  Win7 is very finicky about it's OS partition and doesn't do well when that is tampered with by "outside" utilities -- such as GParted.  You're risking filesystem corruption shrinking it this way.  And, if it does get corrupted, you won't be able to boot back into Win7 to fix it.

Instead, use the Win7 Disk Management utility to do the shrinking.  You find that by entering Disk Management in the start area and clicking the entry above that mentions formatting drives.  That utility will limit the shrinkage -- but it does so to prevent damage to the filesystem.

---

### Post by AZBoy28 on 2012-01-18
> **Mark Phelps said:**
> Do NOT use the slider to resize sda2!  Win7 is very finicky about it's OS partition and doesn't do well when that is tampered with by "outside" utilities -- such as GParted.  You're risking filesystem corruption shrinking it this way.  And, if it does get corrupted, you won't be able to boot back into Win7 to fix it.

Instead, use the Win7 Disk Management utility to do the shrinking.  You find that by entering Disk Management in the start area and clicking the entry above that mentions formatting drives.  That utility will limit the shrinkage -- but it does so to prevent damage to the filesystem.

Hey,

Thanks for the warning, I did what you said, all went well, until the message 

'The volume you have selected to shrink maybe corrupted, use Chkdsk to fix the corruption problem, and then try to shrink again.'

Whats wrong?

---

### Post by carl4926 on 2012-01-18
I have done literally hundreds of win/linux installs and never yet had a problem using GParted

Windows will spit dummy forever and a day

In windows open a admin terminal

```
chkdsk /f
```

---

### Post by nipunshakya on 2012-01-18
> **AZBoy28 said:**
> Hey,

Thanks for the warning, I did what you said, all went well, until the message 

'The volume you have selected to shrink maybe corrupted, use Chkdsk to fix the corruption problem, and then try to shrink again.'

Whats wrong?

Hi again. If you won't feel dizzy, i suggest you format your **linux partitions** and then go for a clean install. I guess you have already backed up your data. So, its better you format your first two drives(they aren't labeled, which means u made them for linux ! :D ). At this point, i suggest a clean format and clean install to the partitions allocated for linux(**only linux**) using the Disk Management tool in windows 7. 

After you format, you can then make a reboot. Reboot ensures that your new partitions are placed well and functional for windows 7 too. 
Then after a next reboot, you can boot from LiveCD and then carry on with your installations at the newly partitioned spaces. Goodluck.

Regards,WinuxUser

---

### Post by Mark Phelps on 2012-01-18
> **AZBoy28 said:**
> 'The volume you have selected to shrink maybe corrupted, use Chkdsk to fix the corruption problem, and then try to shrink again.'

Whats wrong?

Windows seems to think the partition is corrupted.  Did you reboot into Windows AFTER shrinking the partition?  You need to do that to allow it to make any filesystem adjustments.

You can try using the Boot-Repair tool to fix the Win7 boot -- but you will have to burn a CD of it and boot from that:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

