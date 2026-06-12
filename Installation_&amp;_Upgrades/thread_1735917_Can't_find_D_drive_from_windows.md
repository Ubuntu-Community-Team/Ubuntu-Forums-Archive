---
title: "Can't find D: drive from windows"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by alexander-the-great on 2011-04-21
Hello,
I installed ubuntu 10.04 on my desktop not too long ago alongside windows 7 which i had before.
In other words I'm dual booting windows 7 and ubuntu.

Whenever I was on windows before i installed ubuntu, I had a C: drive and a D: drive visible (They were both my hard drive). The problem is, ever since I installed ubuntu, I can no longer see the D: drive when I am using windows 7. I can see my and access my C: drive from windows, but its almost full. My D: drive was empty and I want to be able to access it from windows because it has a lot of free space I could use. I want to be able to access both the C: drive and the D: drive from My Computer.

Does anyone know how to fix this?

---

### Post by Dutch70 on 2011-04-21
please post the output of...
```
sudo fdisk -l
```
That's a lower case L

Actually, it would also help if you post a screenshot of your partitions in Gparted. 
Use the paper clip in the toolbar to attach the pic.

---

### Post by alexander-the-great on 2011-04-22
[FONT=monospace]Here is the output of what you asked for:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83929bbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1959    15728640   27  Unknown
/dev/sda2   *        1959        1972      102400    7  HPFS/NTFS
/dev/sda3            1972       15271   106824704    7  HPFS/NTFS
/dev/sda4           15271       38914   189913088   83  Linux



And here is the screenshot of gparted:

[[IMG]http://img535.imageshack.us/img535/4204/gpartedscrnsht.jpg[/IMG]]("http://img535.imageshack.us/i/gpartedscrnsht.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")
[/FONT]

---

### Post by Dutch70 on 2011-04-22
Well, I see you didn't simply use the paper clip in the toolbar to attach the pic. :shock:

Your D-drive is still on your hard disk. It is usually your recovery which would be sda1 according to your scrot, so I have no idea why it's not showing in windows. Looks like a windows issue cause it's showing up in Ubuntu.

---

### Post by coffeecat on 2011-04-22
It would appear that your "D:" drive was reformatted and used for the Ubuntu root partition when you installed Ubuntu. Your partitions as showing in Gparted are:

sda1 - This look like a manufacturer's recovery partition.
sda2 - This is your Windows 7 "System" or boot partition.
sda3 - Your Windows C: partition.
sda4 - Your Ubuntu root partition.

A few comments.

You've formatted the Ubuntu root partition with the ext2 filesystem. This is an old non-journalled filesystem - not a good idea for your root partition. Was there any reason why you did not choose the journalled ext3 or ext4 filesystems?

You have no Linux swap partition.

You have four primary partitions. This is the maximum allowed with the mbr partition table scheme, and allows you no flexibility. You would be better to replace sda4 with an extended partition in which you could create a number of logical partitions. For example an ext3/4 Ubuntu root partition, a swap partition, a separate home partition if you want one, and a NTFS partition which Windows would recognise as D:. You have 180GB+ - probably plenty.

---

### Post by coffeecat on 2011-04-22
> **Dutch70 said:**
> Your D-drive is still on your hard disk. It is usually your recovery which would be sda1 on according to your screenshot, so I have no idea why it's not showing in windows. Looks like a windows issue cause it's showing up in Ubuntu.

I believe not. With a size of 15GB of which 10.6 is used, a label of "Recovery" and the diag flag set makes this a recovery partition, not a data D: partition.

---

### Post by Dutch70 on 2011-04-22
I believe you're right Coffeecat. Typically D: drive is Recovery, but apparently not on his system.

---

### Post by alexander-the-great on 2011-04-22
It looks like you guys know how to fix this, but can u guys simplify it for me because I'm a noob.

I just want to have both a C: drive and a D: drive visible and accessible from windows 7 again. How do i do this? do i use gparted while on linux? if so, how?

---

### Post by alexander-the-great on 2011-04-22
I think /dev/sda4 ext2 used to be my D: drive because its 180gb and has a lot of free space. I wanna be able to access it again from windows

---

### Post by Dutch70 on 2011-04-22
Install fs-driver into windows.

[[COLOR="RoyalBlue"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

AFAIK, this only works with ext2/ext3 file systems. You just happen to have ext2, but may want to consider reformatting and reinstalling to ext3 as Coffeecat mentioned above. It's a little trouble now, but well worth it in the long run.

---

### Post by alexander-the-great on 2011-04-22
So i downloaded and installed ext2 volume manager like u said. I ran it and attached a screenshot for you. I can't find the D: drive anywhere. Is there a way to make the D: drive accessible from My Computer again?

---

### Post by coffeecat on 2011-04-22
I haven't used a Linux filesystem driver in Windows for a long time. To be honest, I don't think it's the best option. It's not a good idea to be accessing a Windows C: partition from Ubuntu, or an Ubuntu root partition from Windows. It's just too easy to accidentally delete some essential system files. My preferred option would be to have a separate data partition formatted NTFS. This would be seen as D: by Windows and easily mounted from the Places menu in Ubuntu. But to do this you would need to remove the current Ubuntu root partition (sda4) and replace it with an extended partition. In outline you would need to:

1 - Backup any files you need from your current Ubuntu install.

2 - Boot up the live CD, open Gparted and delete the sda4 partition.

3 - From Gparted, create an extended partition in the 180GB+ vacated by sda4.

4 - Create logical partitions as follows:

  - ext4 partition for Ubuntu root - say 20GB
  - swap partition for Ubuntu - say 1-2 GB
  - NTFS partition in the remainder of the space.

5 - Start the installer and choose the manual/advanced option to install to the two Linux partitions.

Windows would see the logical NTFS partition as well as if it were a primary partition and designate it D: or E: or whatever drive letter comes next. Please note that "D:" type "drive" designations are a Windows convention and make no sense in Linux.

If you need any help with any of that, post back and we can give you more details.

---

### Post by Dutch70 on 2011-04-22
+1 to Coffeecats suggestion.

I have one disk set up with windows & Ubuntu and I access my /home from windows with fs-driver. (I did this 3 yrs ago) I've never had any problems with it, but since I learned more about Linux, I set up my new hdd the way he mentioned. Well, until I decided I didn't need to access it from windows anymore...lol.

That being said. It looks to me like what you call your D: drive is right there (EXT2-181GB) It's just not labeled D:. That's just a name you can change to whatever windows drive letter you want.

Edit: You would access it from "Computer" or My Computer. I don't know where you're at with your pic, I'm not familiar with windows7.

---

### Post by 64bit or bust on 2011-04-22
Before you dig to deep, boot to windows and check to see if drive is hidden in the registry.

The key(s) to look for are described on this page [http://www.ghacks.net/2007/12/16/hide-drives-in-windows-explorer/](http://www.ghacks.net/2007/12/16/hide-drives-in-windows-explorer/)

---

### Post by Dutch70 on 2011-04-22
Wait, what is ext2 volume manager? What I said was fs-driver. It's a file system driver, not a volume manager. Although I can see what you call your D: drive in the pic you posted.

---

### Post by alexander-the-great on 2011-04-22
Since ubuntu is installed on ext2 which is 180gb (I guess this is my D: drive) is it possible to partition this in half so i keep 90gb for ubuntu and then make the other 90gb my D: drive visible and accessible from windows? is that possible? If so, how and what software do i use?

---

### Post by alexander-the-great on 2011-04-22
Dutch 70 !!!!!!! The link you sent me with ext2fsd worked!!! thanks

---

### Post by alexander-the-great on 2011-04-23
One question, I notice that when i reboot windows, the D: drive doesnt reappear in My Computer, so i have to start the ext2fsd program everytime i reboot to make it visible. Is there a way to make ext2fsd show the D: drive automatically without me running the program manually?

---

### Post by Dutch70 on 2011-04-23
AFAIK... you're guess is as good as anyone's. Let us know how it works.

Works well with ext2, I can say that :)

---

### Post by augustuen on 2011-04-23
> **alexander-the-great said:**
> One question, I notice that when i reboot windows, the D: drive doesnt reappear in My Computer, so i have to start the ext2fsd program everytime i reboot to make it visible. Is there a way to make ext2fsd show the D: drive automatically without me running the program manually?
 
I don't really have an experience with partitioning after installation, since I never really need to, but I think you can format from Ubuntu, and if not you should be able to do it from the Live CD. Just remember not to format it, but instead shrink the drive, since if you format it, all your information is gone.

---

### Post by Dutch70 on 2011-04-24
> **alexander-the-great said:**
> Since ubuntu is installed on ext2 which is 180gb (I guess this is my D: drive) is it possible to partition this in half so i keep 90gb for ubuntu and then make the other 90gb my D: drive visible and accessible from windows? is that possible? If so, how and what software do i use?

You can use Gparted to shrink that partition & create a new partition with the unallocated space, you'll need to format the new prtn to NTFS.

---

### Post by coffeecat on 2011-04-24
> **Dutch70 said:**
> You can use Gparted to shrink that partition & create a new partition with the unallocated space, you'll need to format the new prtn to NTFS.

Unfortunately not, since the OP has the maximum 4 four primary partitions. If they shrink sda4, which is the ext2 partition, they will simply get unusable space. Which is why I earlier suggested deleting sda4 and creating an extended partition in which the OP can create as many logical partitions as they wish, for Ubuntu and for a new NTFS D: partition.

---

### Post by Dutch70 on 2011-04-24
> **coffeecat said:**
> Unfortunately not, since the OP has the maximum 4 four primary partitions. If they shrink sda4, which is the ext2 partition, they will simply get unusable space. Which is why I earlier suggested deleting sda4 and creating an extended partition in which the OP can create as many logical partitions as they wish, for Ubuntu and for a new NTFS D: partition.

Thank you, I had forgotten about that. Guess I should review the thread before I post. :P

---

