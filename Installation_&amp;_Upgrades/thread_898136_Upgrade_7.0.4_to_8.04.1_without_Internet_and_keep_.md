---
title: "Upgrade 7.0.4 to 8.04.1 without Internet and keep partitions"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by DAFoxFL on 2008-08-22
I started with a Compaq desktop with Win XP pro installed. Last year I downloaded the Feisty ISO and installed. The disk partitioning went as it should along with installing GRUB. So, I have a nice dual boot XP/Ubuntu machine. The only problem I was never able to solve is that I can't get Ubuntu to connect to my wireless access point because the WAP uses WPA encryption and there evidently is no support for that in Feisty. So, I've messed around a bit in Ubuntu but mostly boot to Windows so I can get on the net.

Fast forward to today. I burned the ISO for 8.04.1 and booted to the live CD. Guess what? Ubuntu found my WAP and gave me the choice to use WPA encryption! I got connected and was able to surf. So, I thought it would be easy to upgrade my old Ubuntu to the latest.

Wait - IS it easy? I haven't been able to figure out how, even after spending half the day reading posts here on the forum. I've also burned the "alternative" CD.

Here's my problem: the installation process gets to the disk partitioning part and then I don't know what to do. I don't want to nuke my Windows partition and I really don't know what the install program is going to do when I hit next. There is nothing I need to keep in any of the Ubuntu partitions.

So, I need a step-by step explanation of how to upgrade Ubuntu using the same partitions set up by the original installation without bothering the Windows partition.

TIA, Dave

---

### Post by jackcy on 2008-08-25
Hi there, from what I have found out until now it is only possible to upgrade from 6.06 or 7.10 to 8.04. This is because 6.06 was the last long term release and 7.10 is the preceding release.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Using a cdrom there would be the work around to upgrade to 7.10 using the cd and then upgrading to 8.04.1 with your actual downloaded version.
You should be able to run a 
gksu "sh /cdrom/cdromupgrade"
or
kdesu "sh /cdrom/cdromupgrade"
for both of the versions.
I tried a direct upgrade from 7.04 to 8.04 but that did not work for me.

Hope it helped.

---

### Post by DAFoxFL on 2008-08-26
So, where can I download the iso for 7.10 to make the CD?

Or, better yet, how can I do a fresh install of 8.04.1 without messing up the existing dual-boot partitions? That really was my original question above:

> [B]"Here's my problem: the installation process gets to the disk partitioning part and then I don't know what to do. I don't want to nuke my Windows partition and I really don't know what the install program is going to do when I hit next. There is nothing I need to keep in any of the Ubuntu partitions.

So, I need a step-by step explanation of how to upgrade Ubuntu using the same partitions set up by the original installation without bothering the Windows partition."[/B]


> **jackcy said:**
> Hi there, from what I have found out until now it is only possible to upgrade from 6.06 or 7.10 to 8.04. This is because 6.06 was the last long term release and 7.10 is the preceding release.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Using a cdrom there would be the work around to upgrade to 7.10 using the cd and then upgrading to 8.04.1 with your actual downloaded version.
You should be able to run a 
gksu "sh /cdrom/cdromupgrade"
or
kdesu "sh /cdrom/cdromupgrade"
for both of the versions.
I tried a direct upgrade from 7.04 to 8.04 but that did not work for me.

Hope it helped.

---

### Post by mkvnmtr on 2008-08-26
You can install 8.04.1 into the same partitions that your current 7.04 is in. If you have gparted installed you can look at your partitions and learn how big each one is. In other words which is your linux partition and which is your swap. Then boot to the live disk. Start the install. When you get to the install choose manual install. You will see all your partitions just like in gparted. It is the same program on the live disk. Click on your linux partition. When it ask you to put in amount point or name the partition put "/" without the quote marks. Then click the box to format the linux partition. Don't format the other partitions. It would not let me do it wrong. It kept sending me back until I had it right. You are only going to fool with your linux partition and the swap partition. You are not going to change anything else. Click proceed and the format will start. Then again and the installation will start. Anything you want to save will have to be backed up. If you have your home in another partition back it up but don't change anything about it. Thats it.

---

### Post by Sef on 2008-08-27
> Here's my problem: the installation process gets to the disk partitioning part and then I don't know what to do. I don't want to nuke my Windows partition and I really don't know what the install program is going to do when I hit next. There is nothing I need to keep in any of the Ubuntu partitions.

So, I need a step-by step explanation of how to upgrade Ubuntu using the same partitions set up by the original installation without bothering the Windows partition

With the Live CD:

System > Applications > Terminal

Copy and paste or type in this code:

```
sudo fdisk -l
``` Small L

Copy and paste the results here.

If we know what partition your ubuntu root sits on, then things will go better.

---

### Post by DAFoxFL on 2008-08-27
Ok, here is the result of sudo fdisk -l :

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1147     9213246    7  HPFS/NTFS
/dev/sda2            1148        1657     4096575   83  Linux
/dev/sda3            1658        1784     1020127+  82  Linux swap / Solaris
/dev/sda4            1785        2434     5221125    b  W95 FAT32

Disk /dev/sdb: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2431    19526976    c  W95 FAT32 (LBA)

So, given the info from mkvnmtr above, I should format and install to sda2 ?

Dave

---

### Post by DAFoxFL on 2008-09-07
I seem to be at a dead end.

 - I've downloaded the Windows 16 bit live CD iso from three different locations.
 - I've checked each one with the Windows version of md5sum and they all test OK.
 - I used ImageBurn software to burn the image to CD.
 - When I boot to the CD, sometimes it will load completely and sometimes it hangs. Seems like if I have unplugged the computer for an hour or so and then booted, it comes up OK. If I just reboot, it hangs at a blank tan screen.
 - When I boot to the CD and choose Check CD it always finds an error in one file (no other information).
 - When I boot the CD and run the memory check, it finds bad memory but Windows does not.

 - The times I get it to boot from live CD and give me a usable desktop with internet connection, I am unable to delete the swap partition because it is in use (probably by the live CD).
 - When I click on the install desktop icon, I get an error message (I need to write that down probably).

 - When I boot the live CD and get to the intro menu and choose Install, it hangs at the blank tan screen.

Any ideas?

---

### Post by Sef on 2008-09-07
If you are updating from a cd, then you need to use the [alternate cd]("http://ubuntu.com/getubuntu/download").  Click the box below the green arrow next to start download.

Do you have a dvd RW +/-?  If so, then download the [dvd version]("http://cdimage.ubuntu.com/dvd/current/") of ubuntu.

---

### Post by DAFoxFL on 2008-09-13
OK, I booted from the 8.04.1 alternate CD. Everything goes fine until I get to partitioning part. It says:

"Currently configured partitions and mount points:
SCSI1 (0,0,0) (sda) 20.0 GB ATA ST3200114
   #1 primary 9.4 GB B   ntfs
   #2 primary 4.2 GB     ext3
   #3 primary 1.0 GB   F swap   swap
   #4 primary 5.3 GB     fat32"

I select "Finish partitioning and write changes"
It says "No root file system is defined. Please correct this from partitioning."

So, I chose #2 of SCSI1 "This partition will be formatted with the ext3 journaling file system." I said "Yes, format it." then "Done setting up this partition."

It again came back with "No root file system is defined. Please correct this from partitioning."

I'm stuck. What am I supposed to do here to simply overwrite the existing 7.0.4 with 8.04.1 ?

---

### Post by DAFoxFL on 2008-10-07
I'm still stuck here. Any ideas, anyone?

---

### Post by amac777 on 2008-10-07
As people told you above, you need to set a mount point of "/" (without the quotes) for #2 primary 4.2 GB ext3. That way, the install cd will know that SDA2 is where the root directory of Ubuntu should be installed.

The steps are something like this:

1. backup anything you want to keep for your old Ubuntu (you said you didn't want to keep anything but I'm just making sure)

2. Boot from the new Ubuntu CD, start the installation, select "manual partitioning" when you get to the partitioning step.

3. Select SDA2 (#2 primary 4.2 GB ext3) and set a mount point of "/" (without the quotes), and check the format box so it gets formated

4. (?) Select SDA3 (#3 primary 1.0 GB F swap swap) as the swap partition if necessary. I am not sure if the install CD will do this automatically or not. If you get an error message that no swap partition is selected, then select SDA3 as the swap and that will fix it.

5. Continue installation and your old Ubuntu version will be overwritten with the new version.

---

### Post by haydnc on 2008-10-07
Hi DAFoxFL, it looks like you've probably got your /home in the same partition as your existing installation (that being sda2).

With that in mind - so that you don't lose everything you've got stored from your Ubuntu login I'd advise copying everything in your /home directory to a DVD or something before you upgrade. That includes all the hidden files (the ones that have names starting with a '.').

If you copy all that data off first you can copy it back again after you install 8.04.1 and you won't lose anything.

Once that data is copied off you run the installer just as you have been and when you get to the partitioning bit you'll probably need to select manual partitioning with the following settings:

/dev/sda1 - mount as /mnt/windows; do **not** format
/dev/sda2 - mount as / ; set this partition to be formatted as this is where 8.04.1 will be going
/dev/sda3 - mount as swap; no formatting should be needed
/dev/sda4 - mount as /mnt/windata; do **not** format, also you might want to chose a mountpoint that is a bit more relevant to whatever you've got on that partition currently

/dev/sdb1 - mount as /mnt/windata2; do **not** format, also as with sda4 you might want to chose a mountpoint that is a bit more relevant to whatever you've got on that partition currently

---

### Post by DAFoxFL on 2008-10-10
You folks are telling me things that don't match up with what I'm seeing on the screen. First, there are no check boxes, only DOS-looking screens that I navigate through using arrow keys and tab and enter.

So, I get to the Partition section of the install and I choose Manual. The next screen shows a list of my partitions. I select partition #2.

The next screen says "You are editing partition #2 ..."
Partition Settings: do not use
Bootable Flag: off
Resize Partition
Copy data from another partition
Erase data on this partition
Delete this partition
Done

If I go into the partition settings, I get a new screen titled "How to use this partition" with the following options:
Ext3 journaling file system
Ext2 file system
ReiserFS journaling file system
JFS journaling file system
XFS jounaling file system
FAT16 file system
FAT32 file system
Swap area
Physical volume for encryption
Physical volume for RAID
Physical volume for LVM
Do not use this partition.

So what do I choose? Do I just set the Bootable Flag to ON on the first screen? Do I have to "Erase data on this partition" also?

I don't care about the existing Ubuntu installation, I've only explored, never really used so there is nothing I want to save. I just want to get 8.04.1 installed over it.

Thanks,
Dave

---

