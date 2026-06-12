---
title: "Need help partitioning hard drive"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by purifiedwater on 2008-03-17
I am trying to partition my 40gb hard drive.  I can not figure out how to resize the existing C drive.  When I use gparted my HD is locked and wont allow me to resize it.  If I unmount my HD it still will not allow me to resize it.  Thank You

---

### Post by Pumalite on 2008-03-17
XP or Vista?

---

### Post by purifiedwater on 2008-03-17
I have XP, but I ran gparted both as a boot CD and in Ubuntu off the live CD.  I am trying to partition in order to install Ubuntu.

---

### Post by Pumalite on 2008-03-17
Boot Gparted Live CD. Right click on XP. Choose resize from the menu.

---

### Post by purifiedwater on 2008-03-17
I booted with the Gparted CD.  On the HD there is three partitions already on it.  Labeled as hda1-3.  Two(hda1 and 2) are small ones which contain windows and Dell files.  The third (hda2) is the C:/ which around 34-35gbs.  It isn't labeled as XP, so i'm not sure if this is the one you mean but it is the one I want to resize.  On the left next to it is an orange triangle with an exclamation point in it.  It also doesn't show how much space is taken up on it, it just says 34-35 total.  When I click resize for it, the window comes up with the bar to drag left and right.  It won't allow me to drag it either way and if I try to enter the size in numbers it won't allow me click the resize button.

---

### Post by purifiedwater on 2008-03-17
I meant hda 1 and 3 have the Dell and Windows files.

---

### Post by Pumalite on 2008-03-17
Post a screenshot from Gparted Live CD. Use the camera icon.

---

### Post by purifiedwater on 2008-03-17
I have the screen shots but don't know how to retrieve them in HP.

---

### Post by Pumalite on 2008-03-17
Boot your Live CD then and post:
sudo fdisk -lu

---

### Post by purifiedwater on 2008-03-17
I took these using Gparted in Ubuntu.  It appears the same as the gparted boot Cd.  My bad the partitions are labeled sda not hda.
The first shot is when the disk is not mounted.
The second shot is when the disk is.
I'm sorry but I don't know what yu mean by,  "sudo fdisk -lu"

---

### Post by purifiedwater on 2008-03-17
The second screen shot

---

### Post by jken146 on 2008-03-17
> **purifiedwater said:**
> I'm sorry but I don't know what yu mean by,  "sudo fdisk -lu"

Open a terminal (Applications -> Accessories -> Terminal) then type ```
sudo fdisk -lu
``` and copy-paste the output in a post.

---

### Post by purifiedwater on 2008-03-17
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      128519       64228+  de  Dell Utility
/dev/sda2   *      128520    71039429    35455455    7  HPFS/NTFS
/dev/sda3        71039430    78124094     3542332+  db  CP/M / CTOS / ...

Is this what you meant?

---

### Post by Pumalite on 2008-03-18
Boot Gparted Live CD. Right click on sda2, choose resize from the menu and 'shrink' to the left
Backup everything first. Takes some time.

---

### Post by purifiedwater on 2008-03-19
I ran chkdsk and now it's partitioned.  But I can't install it when I do the Install and do manual I can't select the new partition or the original C either.

---

### Post by Herman on 2008-03-19
You have a 'recovery' or re-install partition or something like that in partition number1, Windows in partition2, and a data partition as partition number3, by the looks of things.
So you have already used up three out or your four possible primary partitions. You can only make one more primary partition, or you can make an extended partition which you can subdivide up into as many logical partitions as you want.

Ubuntu needs at least two partitions to install in, a large partition for / (root), (the main operating system files), and a small partition for a swap area, (like a page file). It can't do that if you created a number4 primary partition because the primary partition can't be further subdivided.

I'm just guessing that might be what's wrong, I'm not sure.

If I'm right, try deleting the new number4 partition and make it again but this time make sure you make an 'extended' type of partition.
Then you will be able to create more partitions (logical) inside that okay and you should have no more problems.

If that's not it and I guessed wrong, can you provide an up to date screencap of your new situation from GParted please? 

Regards, Herman :)

---

### Post by purifiedwater on 2008-03-20
Thanks a lot man that was the problem and I got it installed.  I have a problem though of not being able to see what's on my C drive because it say there is no mount point... or something similar to that.  Also I have an external drive, how do i get Ubuntu to recognize the files on it.

---

### Post by Herman on 2008-03-20
> I have a problem though of not being able to see what's on my C drive because it say there is no mount point... or something similar to that. Okay, Ubuntu will almost always detect all the other file systems you have in the computer prior to installation and make a mount point for each one automatically.
Ubuntu will normally also have a line for them in the /etc/fstab file which causes Ubuntu to mount your other file systems automatically on each boot-up.
I don't know why that doesn't happen every time, but I noticed that too, sometimes Ubuntu mounts everything and other times it doesn't.
I suspect, (but I'm not sure), that Ubuntu doesn't mount the other file systems if it detects that they need a file system check. (Maybe they're 'dirty' and need cleaning up). Again, I'm not sure, but it wouldn't hurt anything and might do a lot of good if you would take a little time and run CHKDSK in Windows.[NTFS and FAT32 file system repair and maintenance]("http://users.bigpond.net.au/hermanzone/p10.htm#NTFS_File_Fystem_Repair_and_Maintenance").

A 'mount point' is just a folder (the name for a 'folder' in Linux is a 'directory'), and you can make an empty folder (directory) to use for a mount point anywhere you want. I have one in my home directory that has my data disk mounted in it, (it kind of reminds me of going down into the basement if my computer was a house). :)
Anyway, the traditional place to make mount points in Linux is in the /mnt directory.
In Ubuntu, we're a little different to standard Linux systems, we have a /mnt directory that we can use for that, but even better, we have a /media directory.
Most Ubuntu users make their mount points in thier /media directory and that means we will be automatically given an icon on our Desktop for easy access to the file system that we mounted. (Instead of having to navigate to the /media directory every time).
We need to be the super user (or 'root' user), to be allowed to make a new directory in /media, so we need to use the word 'sudo' before the command.
Here is a command to make a mount point,
```
sudo mkdir /media/WindowsXP
```Now for the next step, we need to know the partition number for Windows XP, so we take a look at your GParted screencap, or most people would use the 'sudo fdisk -lu' command, Either one will be okay.
```
sudo fdisk -lu
```From your earlier screencap of GParted, it should be /dev/sda2, so I'll use that.
Okay, here's the command to mount your Windows partition,
```
sudo mount /dev/sda2 /media/windows -t ntfs -o nls=utf8,umask=0222
```That will mount your drive C for the duration of one session or boot -up. 

If you want it to automatically be mounted on every boot-up, you need an entry in your /etc/fstab file.
First, make a backup copy of your /etc/fstab file for safety,
> sudo cp /etc/fstab /etc/fstab.backupThen you need the file system UUID number for the file system you want to mount automatically. You can use this command to get the UUID number,
```
ls /dev/disc/by-uuid/ -alh
```That will give you a list of your partitions and their UUID numbers.
Copy that to a text fiel, or leave that terminal open and open another terminal in another desktop if you want.

By the way, I hope you don't type all these commands our by hand, it would be a lot easier if you just copy and paste them.

Now, we'll make an entry in /etc/fstab,
```
gksudo gedit /etc/fstab
```That opens the file with administrative privledges.

Then, here's what you do,

Example file BEFORE
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>       <type>           <options>                <dump>  <pass>

   proc          /proc               proc             defaults                  0       0

# /dev/sda5      
UUID=61e29deb-c5c3-4401-8557-81482aedc839  /   ext3    defaults,errors=remount-ro 0       1

# /dev/sda3
UUID=124D-170D   /media/hda1         vfat    defaults,utf8,umask=007,gid=46       0       2

# /dev/hda5
UUID=a08d44f6-d681-4901-a7cc-345fc9fa9eb6 none  swap     sw                       0       0

/dev/cdrom      /media/cdrom0     udf,iso9660         user,noauto                 0       0

/dev/fd0        /media/floppy0      auto             rw,user,noauto               0       0
```Example /etc/fstab file AFTER
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>       <type>           <options>                <dump>  <pass>

   proc          /proc               proc             defaults                  0       0

# /dev/sda5       
UUID=61e29deb-c5c3-4401-8557-81482aedc839  /   ext3    defaults,errors=remount-ro 0       1

# /dev/sda3
UUID=124D-170D   /media/hda1         vfat    defaults,utf8,umask=007,gid=46       0       2

[COLOR=Sienna][B]#[COLOR=Sienna][FONT=Bitstream Vera Sans Mono]/dev/sda2     
[/FONT][/COLOR][FONT=Bitstream Vera Sans Mono]UUID=[/FONT][FONT=Bitstream Vera Sans Mono][COLOR=#33ccff]**285F98566380864A**[/COLOR][/FONT][COLOR=Sienna][FONT=Bitstream Vera Sans Mono]/media/WindowsXP   ntfs  nls=utf8,umask=0222      0         2[/FONT][/COLOR]
[/B][/COLOR]
# /dev/sda5
UUID=a08d44f6-d681-4901-a7cc-345fc9fa9eb6 none  swap     sw                       0       0

/dev/cdrom      /media/cdrom0     udf,iso9660         user,noauto                 0       0

/dev/fd0        /media/floppy0      auto             rw,user,noauto               0       0
``` NOTE: Please replace the file system UUID number with your own file system UUID number, copy and paste it from your output from the 'ls /dev/disc/by-uuid/ -alh' command.

That should do it.

As for  your USB external drive, it should automatically be mounted in a minute or so every time you plug it in, but sometimes that doesn't seem to work, or it doesn't work in all computers. I don't know why not, possibly something to do with the BIOS or the motherboard.
You might try having the USB external plugged in and rebooting, that's what I need to do with my Acer laptop, for some reason.
If that;s inconvenient, or doesn;t work either, I just do it the same way as already explained above for manually mounting a file system.

Regards, Herman  :)

---

### Post by purifiedwater on 2008-03-26
Thanks.  Sorry to take such a long time to get reply.  You were right again, the drive was dirty and it automatically mounted after reboot.
I know it's random but do you know of a way to download a 3D file file viewer, like in Jurassic park.

Thanks a lot again.

---

### Post by Herman on 2008-03-26
I don't know much about 3D file viewing, there are a lot of programs available for free to Ubuntu users, at least 30,000 packages. There are programs there for almost anything you can think of, but would be quite a feat to be able to remember them all. As it happens, unfortunatley 3D isn't something I have bothered looking into yet.

There are some great videos you can download from [Ubuntu Screencasts]("http://screencasts.ubuntu.com/") that explain quite a lot about how to install and how to do things in Ubuntu.
One of them is '[Installing Applications]("http://screencasts.ubuntu.com/MoS2007/12_Installing_Applications")'. 
If you download that and watch it, it will take you through enabling repositories and show you how to search for free software.
I highly recommend Ubuntu Screencasts, I have downloaded and watched mosty of them and they're well worth the time taken. I learned quite a few tips and tricks from them myself, and I've been using Ubuntu for a while.

'Applications'-->'Add/Remove' is a good place to look around for the most popular programs.
'System'-->'Administration'-->'Synaptic Package Manager' shows you the full list. It can take all day to scroll through them all, so thankfully there's a very good search bar.
Of course, another good place to begin is right here in Ubuntu Web Forums too, where you might search for '3D file viewer', or something like that and find out what others are using.

Regards, Herman :)

---

