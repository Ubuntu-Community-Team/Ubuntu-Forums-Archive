---
title: "grub problem during install. please help!"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by ignus on 2006-11-15
im having problems getting 6.10 to install on my machine. everything goes fine 'till the end of the install when grub tries to do its thing. the problem i am having is with grubs strange naming scheme. i currently have 5 hdds in the pc 2 x ide (just for storage) i think they are /dev/hdc,hdd and 3 x sata /dev/sda,sdd and my main (read: original) disk /dev/sdc which is where the mbr is. when you install ubuntu and choose to partition your disks the installer asks you to choose a disk to stick the grub mbr. default is hd0 i think. i have tried the install several times with several different things in here. i thought sd0 or sd2 would work but apparently not. grub sh*ts itself if i try to install the mbr manually after the installer is finished. 

i tried asking in #ubuntu on freenode but got no replies. if anyone could help i would really appreciate it. appologies for the long post. if there is any info i left out or something i didnt explain correctly please let me know.

---

### Post by bscbrit on 2006-11-15
When you partitioned your disks to install Ubuntu, what did the partition manager identify /dev/sdc as?

If you have a Live CD, you can always boot it up and use the partition manager in that to try to identify the correct description for the drive holding the MBR.

There is probably an easier way but I'm just visiting the forum after several months' absence - The gears are a bit slow at the moment!

---

### Post by bulldog on 2006-11-15
GRUB is counting disks as hd0,hd1,hd2 and so on.
No sda or what ever,that's for fstab.

Now you have to find out which number is your sdc :D 

I think your IDE is hd0 and hd1,so sda is hd2,sdd is hd3 than should be sdc hd?:D 

Just give it a try.

If you have Uuntu installed already you can install GRUB from the live cd on your Ubuntu disk or any other disk for that matter.
Let me know.

---

### Post by ignus on 2006-11-15
ah! that makes sense. so grub probably considers sdc to be hd2 or hd3 or something like that.. i think its time to fire up the live cd again and see if the installer wants to play nice!! 

thanks a million for the help. ill let you know how it get on :D

---

### Post by ignus on 2006-11-15
ok now this is where it gets interesting. ubuntu installed flawlessly. turns out grub decided to call my disk (/dev/sdc) hd4.  
so when i reboot after the install im presented "attempting to boot from CD... skipped" followed by the GRand Unified Bootloader and this is good. i hit return on Ubuntu and get "Error 22: partition does not exist" or something to that effect. so i try  Ubuntu Recovery and get the same thing. finally i try the windows option which ubuntu has helpfully added to the grub menu. i get "Non System Disk: press any key..." hit a key and "disk boot failure: insert system disk and hit a key"

now this is where it gets interesting. after the windows bootleader has shat itself my machine goes straight back to "attempting to boot from CD... skipped" followed by the very same grub menu only this time windows and ubuntu will both work fine. it does this EVERY time. windows/ubuntu fail to load, windows bootloader errors, back to grub again, everything works fine.... wtf?

does anyone have any idea why grub might sh*t itself on the first time? and then work second time 'round without a reboot?

i think it might be something to do with my many attempts to install. there may be more than one grub/mbr on a seperate disk.
is there any way to blank the mbr on the other disks in my system? or possibly find out where grub is booting from first?

if anyone has any ideas please let me know!!  :)

---

### Post by confused57 on 2006-11-15
You might want to boot up the live cd, open a terminal(Applications---Accessories---Terminal), and post the output of:
```
sudo fdisk -l
```
The -l is a small "L".

Here is an excellent link for mounting partitions, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You might want to mount the Ubuntu partition, and determine what your /boot/grub/device.map shows...this should show how grub recognizes the order of your hard drives.

You can use the live cd to install grub to a specific hard drive mbr:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If you can get grub installed to the Ubuntu drive mbr, and you're able to select booting to that drive 1st in bios...then you "should" be able to add an entry to grub to boot your Windows drive, once you determine how it's designated in your device.map.

I'm just giving you some possibilities...you'll need someone with more experience using multiple hard drives that can help you further.

---

### Post by bulldog on 2006-11-15
Hate to say it but I do .............told you so.lol
Reinstall Grub at your Ubuntu hdd with the live cd
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next commands. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell
```
quit
```
That is it. Grub will be installed to the mbr.[/code]

**Watch it!! when the command 'find' gives you hd4,0  as an answer than the last part setup should be hd4 too**

Make this disk your first boot device.

---

