---
title: "GRUB Error 21"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by Nemisis_101 on 2008-06-07
Hello,

I have just finished an installation of Ubuntu, everything went ok and there were no errors during install.

The situation -

I have a HP Pavilion 750 with Windows XP on the internal hard drive, i purchased an external hard drive to install Ubuntu onto, hoping to be able to duel boot them. Now after Ubuntu saying "Installation complete, restart now", and after re-starting. This has happened. 

The screen i see right now -

```

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21

_

```

Windows is not booting either when the external hard drive is not plugged in, or when it is plugged in. If it matters; the install option I selected was to install to all free space on my external hard drive.

What should i do to fix this?

Thanks,

---

### Post by Pumalite on 2008-06-07
Use Super Grub to fix your Windows MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Reinstall.
During the installation, in step 7 or 8; go to 'Advanced Tab' and change (hd0) for /dev???
Where ??? is your external drive. Find out with:
sudo fdisk -lu

---

### Post by Nemisis_101 on 2008-06-07
Sorry, i am new to Linux etc.

So i burn this iso to a bootable CD and whack it in the system, the select !WIN! which should let me into windows, what about getting into Ubuntu? how would i actually repair the fault? 

Cheers and aplogies for being new,

---

### Post by Pumalite on 2008-06-07
You can do both; repair the MBR and/or boot Windows. Ubuntu, you have to reinstall.

---

### Post by Nemisis_101 on 2008-06-07
Do i burn all of these - [http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/](http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/) to a CD? or which one?

Thanks,

---

### Post by meierfra. on 2008-06-07
> Ubuntu, you have to reinstall.


This might be the easiest solution, but try this first:

Use Subgrub  to fix the MBR of the Internal drive.

Also use Supergrub to install Grub to the MBR of the external drive.

Then boot from you external drive and see whether you boot into ubuntu.(or at least get to the grub menu)

---

### Post by meierfra. on 2008-06-07
Get the newest one 

super_grub_disk_0.9725.iso

---

### Post by Pumalite on 2008-06-07
Delete.

---

### Post by Nemisis_101 on 2008-06-07
Thanks, but can you explain that in layman's terms (sorry), so I burn to super_grub_disk_0.9725.iso to CD then whack it in, navigate the confusing non-G UI, whats the command option to repair the MBR on my internal (most important) then repair the external?

Cheers,

---

### Post by issih on 2008-06-07
Ubuntu as a whole doesn't need reinstalling, grub does.

Whats actually happening is that ubuntu, by default, installs the boot-loader (grub) onto the primary (i.e. internal) drive's master boot record (mbr).

This boot-loader is set up to have options to boot windows from its original location, and also an option to boot ubuntu from wherever you installed it.

The problem is occurring when you remove the external disk, but the boot loader doesn't know this, and tries to find the ubuntu install, which is no longer present because you removed the disk. Grub therefore fails, with error 21 and you can't boot into anything.

At this point, using a supergrub cd to replace grub with the original windows boot loader will give you your system back in a working manner (i.e. windows will boot).

To get ubuntu working you need to do something else, probably the most sensible thing is to install grub into the mbr of the external drive rather than the internal one.

If you then set the boot order in bios so that the external drive is tried first (or indeed if you just modify the boot order dynamically at boot time) so that the system boots from the external drive, grub should have no problems locating ubuntu or the windows installations.

For someone new to linux, it is almost certainly easiest to just redo the ubuntu installation and as has been said drop into the advanced dialog at the last step and select where to install grub. It can be done without reinstalling by doing this:

[https://help.ubuntu.com/community/GrubHowto#head-4c7a8640a439568ee312c9f262cc1099634f25ef](https://help.ubuntu.com/community/GrubHowto#head-4c7a8640a439568ee312c9f262cc1099634f25ef)

Following the instructions listed under command line ought to sort you out if you really don't want to reinstall.

Good luck, and i hope you followed that

---

### Post by Nemisis_101 on 2008-06-07
So repairing the mbr has to be done through Ubuntu? i thought the super grub could fix it?

---

### Post by Pumalite on 2008-06-07
Both.

---

### Post by meierfra. on 2008-06-07
Supergrub can do it. Choose 

> 
Super Grub Disk (WITH HELP)   

and then   look for the option

> WIN => MBR & !WIN!   

---

### Post by Nemisis_101 on 2008-06-07
No we are cooking with gas! thanks very much to both of you!

Ok, current status - windows boots from start up.

So how do i set the grub for the external hard drive to load Ubuntu, presumbly there is a similar option in super grub? preferably without re-installing as for my PC installation takes hours.

Cheers,

---

### Post by meierfra. on 2008-06-07
Sorry for the delay. I'm not familar enough with SuperGrub to tell you exactly  how to use it to install Grub to the MBR of the external drive. So I'll give you instruction for the Ubuntu LiveCD instead.


Boot from the Ubuntu LiveCD, open a terminal (Applications->Accesories->Terminal). Type

```
sudo grub
```

and at the "grub>"  prompt

```
find /boot/grub/stage2
```

The output will be of the form

(hd0,0)  

but the numbers could be different.

At the "grub>" prompt:

```
root (hd0,0)   (use the output of find /boot/grub/stage2)

setup (hd0)          (use the first number from the output)
 
quit
```


Reboot. But set you bios to boot from the external drive.

---

### Post by meierfra. on 2008-06-07
This is how it works with SuperGrub. Make the following selections:

Super Grub Disk (No Help)
English Super Grub Disk
Advanced
Gnu/Linux (Advanced)
Fix Boot of Gnu/Linux (Grub)
Manually Restore Grub in Hard Disk (MBR)
Manually Restore Grub in Hard Disk (MBR)
Choose your External Drive   (If you  pick the wrong one, you should notice it at the next step and you can  go back to correct it)
Choose your Ubuntu Partition 
Choose your External Drive  (same one as above)
Press "c" and  then type reboot.

---

### Post by Nemisis_101 on 2008-06-08
It does not give the option to select my external hard drive(sdb) (when selecting the hard drive where Super Grub should fix mbr) it only shows - 
or i am being confused by the layout, ie this is the screen below -

```

Partition of GRUB
NATURAL  LINUX-IDE     LINUX-SCSI    GRUB      HURD
1          hda            sda        (hd0)      hd0

```

What do i select? i sure don't want to overwrite my windows drive, on install my external was sdb.

When i boot from the LiveCD it goes to the main boot menu screen with the options to "Try Ubuntu without changes to your computer"
or "Install Ubuntu" etc. what do i select?
Thanks,

---

### Post by issih on 2008-06-08
To do it via the live cd just select the option to "try ubuntu without changes to your computer". Eventually (it will take a few minutes) that will boot the system into a version of ubuntu running entirely from the cd.

Once that is up and running, go to:

Applications->Accessories->Terminal

And then in the terminal window do the following:

1. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
2. Type "grub". (N.B. the prompt in the command line will now say grub)
3. Type "find /boot/grub/stage1". You'll get a response similar to
   "(hd1,0)". The first number identifies the hardisk with ubuntu 
   installed on it, the second the partition on that disk in which
   ubuntu is installed
4. Type "root (hd1,0)", or whatever your harddisk + partition numbers are
   for Ubuntu.
5. Type "setup (hd1)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot and remove the bootable CD.

---

### Post by Nemisis_101 on 2008-06-08
Ok i did what you said and it now boots windows, what about Ubuntu?

Thanks,

---

### Post by Nemisis_101 on 2008-06-08
Could Ubuntu not be booting because its not set in the BIOS?

I went to the boot order, but i don't see an obvious name meaning an external hard drive, i only have the following options -

```

Floppy
LS120
Hard Disk
CDROM
ZIP100
LAN
Disabled

```

Alternatively there is an option called "Hard Disk Boot Priority" then an option for my internal hard drive and a "Bootable Add-on Cards".

What should i do?

Thanks,

---

### Post by meierfra. on 2008-06-08
Edit: Read my next message first

It seems like your bios are not able to boot from a USB drive. I suggest to look at you bios for a while longer and see whether there are any settings  you can change.

If this does not work, you need to create a dedicated grub partition or boot partition on the internal drive.

---

### Post by meierfra. on 2008-06-08
> Ok i did what you said and it now boots windows, what about Ubuntu?

Does the grub menu appear than you boot from the external drive?

If yes, what error messages to you get when you select Ubuntu?

---

### Post by Nemisis_101 on 2008-06-08
Hmmm, i suspected that. I will see what super grub has to say about booting it. If it cant then I will re-size my existing Windows XP partition on my internal Hard Drive and install it there (sigh). If for some reason I don't like Ubuntu how would i give that partition back to Windows XP (effectively merging it into one again)?

Also, how do i format my external Hard Drive back to NTFS so Windows XP can see it?

[EDIT] Just tried super grub and it cant find /boot/grub/menu.1st to boot it. Looks like its off to the internal Hard Drive. [/EDIT]

Thanks for all your help fellas,

---

### Post by meierfra. on 2008-06-08
It seems our messages crossed in cyber space. If the grub menu appears at boot up, you shouldn't need  a separate grub partition.

---

### Post by Nemisis_101 on 2008-06-08
Sorry, im not sure what you mean? Whats the best way to install Ubuntu now? What do I select on the install wizard; resize existing partition?

Cheers,

---

### Post by meierfra. on 2008-06-08
Never mind my previous two messages. 


You have two  possibilites:

1)  Keep Ubuntu on the external drive (no re-installation  neccessary). Create  a small partition (about 200 MB) on the internal drive  to hold the boot information for ubuntu.  Fur further help, please  boot from the Ubuntu Live CD, open a terminal and post the output of "sudo fdisk -l".

2)  Install Ubuntu on the internal drive. (Yes, "resize existing partition" is the way to go.)

---

### Post by Nemisis_101 on 2008-06-08
Ok i will try and post the fdisk output, i tried to install onto a new partition (i used the slider to create a 20GB partition for Ubuntu) it then said it had an error when it was creating a partition, XP fixed the drive with a chkdsk on boot up. I figured a defragment of the hard drive might help (doing that right now). What tool can I use to make a 200MB partition?

Thanks,

---

### Post by meierfra. on 2008-06-08
> I figured a defragment of the hard drive might help (doing that right now)

Good idea.  I suggest  to defrag two or three times.


> What tool can I use to make a 200MB partition?

gparted   on the Ubuntu Live CD should work just fine (System->Administration->Partition Editor)

Or you can get the [gparted LiveCD]("http://gparted.sourceforge.net/") or [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php")

---

### Post by Nemisis_101 on 2008-06-08
Ok, i have defragmented the Hard Drive 4 times.

sudo fdisk -l =

```

Disk /dev/sda/ 60.0 GB, 600601555904
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a98a89

  Device Boot       Start       End      Blocks    Id   System
/dev/sda1 *             1       7300    58637218+    7  HPFS/NTFS

Disk /dev/sdb/ 60.0 GB, 60011642880
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80341265

  Device Boot       Start       End      Blocks    Id   System
/dev/sdb1              1       7108    57094978+   83   Linux
/dev/sdb2           7109       7298     1510110     5   Extended
/dev/sdb5           7109       7298     1510078+   82   Linux swap / Solaris


```

Thanks, I think I will attempt an install onto the Internal again, but can you expand on the 200MB partition part again?

Thanks,

---

### Post by meierfra. on 2008-06-08
> but can you expand on the 200MB partition part 

Boot from the Ubuntu Live CD.


Step 1  Create a 200MB partion on the internal drive

Use Gparted to shrink your XP partition by 200MB at the end. 
Use the unallocated space to create a 200MB partiton, format ext3.

(You might have to reboot after this for the  LiveCD to recognize the new partition)


Step 2) Copy the boot folder to the internal drive.

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb1 /ubuntu
sudo mkdir /newboot
sudo mount -t ext3 /dev/sda2 /newboot
sudo cp -prv  /ubuntu/boot/* /newboot/
```

Step 3) Mount your boot folder

```
gksudo gedit /ubuntu/etc/fstab
```

Add this line to the file:

/dev/sda2 /boot     ext3    relatime        0       2

Save the file.


Step 4  Edit menu.lst


```
gksudo  gedit /ubuntu/boot/grub/menu.lst
```


Change "#groot (hd1,0)" to "#groot (hd0,1)"

Change "root (hd1,0)" to "root (hd0,1)" (three times, for ubuntu, ubuntu recovery, memtest)

Change /boot/vmlinuz.... to /vmlinuz... (twice)
Change /boot/initrd.... to /initrd...  (twice)
Change /boot/memtest... to /memtest... 

Save the file.



Step 5   Install Grub to the MBR of the internal drive.

```
sudo grub
```
and at the grub prompt:

```
root (hd0,1)
setup (hd0)
quit
```

That's it.

---

### Post by Nemisis_101 on 2008-06-08
[EDIT] I didnt know gparted was part of Ubuntu, forget this. Thanks and i will report back. [/EDIT]

---

### Post by meierfra. on 2008-06-08
Skip Step 4.

---

### Post by Nemisis_101 on 2008-06-08
Do i make the 200MB partition - "Create as : Primary Partition" or "Extended Partition"?

Thanks,

---

### Post by meierfra. on 2008-06-08
Sorry for the wrong Step 4.  I realized that step 4 was wrong immediately after I posted it. But just then, we had a 1 second power outage, which was enough to knock out my wireless connection. So it took me a little bit to get back online.

---

### Post by Nemisis_101 on 2008-06-08
Ok thanks, but should it be a Primary Partition or Extended Partition? (for the 200MB partition).

My dumb, its a Primary partition because there is no filesystem 
option for a extended partition.

Thanks,

---

### Post by meierfra. on 2008-06-08
> Its a Primary partition 

That's right. Just to confuse you even more:  Step 4 actually was correct.  We had a tornado warning, moved in the basement, power was out for a second, internet was gone  and in the mids of all of that I got confused between a "dedicated grub partition" and a "separate boot partition".

So I will put Step 4 back in. Just give me minute.

---

### Post by Nemisis_101 on 2008-06-08
Now that's dedication! Thanks!

I get an error -

When executing - ```
sudo mount -t ext3 /dev/sdb1 /newboot
``` 

Error - ```
mount: mount point /newboot does not exist
```

Also, where is the file - 


Please help,

Thanks,

---

### Post by Nemisis_101 on 2008-06-08
Agh! I made a mistake when i was doing the first block of command prompts, i did the mounting the wrong way round, i did it again and i think it corrected itself. 

Eeeek,

---

### Post by meierfra. on 2008-06-08
>  sudo: please use single character options

sound like you left out the "cp"   in "sudo cp -prv  /ubuntu/boot/* /newboot/"

I recommend  "copy and paste" rather than retyping.


Edit: seems you figured it out by yourself

---

### Post by Nemisis_101 on 2008-06-08
Sorry, where is the menu.1st file? The command prompt does not open it and i dont see it on the hard drive, which drive should it be on?

Thanks,

---

### Post by meierfra. on 2008-06-08
menu.lst  (the "l" is a lowercase "L")

---

### Post by Nemisis_101 on 2008-06-08
Gotcha, lower case.

This doesent do anything - 

> Step 4 Edit menu.lst

```
gksudo /ubuntu/boot/grub/menu.lst
```
Change "#groot (hd1,0)" to "#groot (hd0,1)"

Change "root (hd1,0)" to "root (hd0,1)" (three times, for ubuntu, ubuntu recovery, memtest)

Change /boot/vmlinuz.... to /vmliuz... (twice)
Change /boot/initrd.... to /initrd... (twice)
Change /boot/memtest... to /memtest... 

Save the file.

When I add "gedit" to the prompt it loads up a file but there is none of the "#groot" stuff you asked me to change.

Do i change - ```
/boot/vmlinuz(long string of stuff) root=(longstring of stuff) ro single
```

to just - ```
/boot/vmlinuz
```

What have I dont wrong?

Thanks again,

---

### Post by meierfra. on 2008-06-08
Thats strange.  In case that you rebooted after

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb1 /ubuntu

```

you will have to repeat those  two  commands.

If that did not help:

 What is output of the following two commands:

```

ls /ubuntu/boot
ls /ubuntu/boot/grub
```

---

### Post by meierfra. on 2008-06-08
>  to  /boot/vmlinuz


No to

> /vmlinuz(long string of stuff) root=(longstring of stuff) ro single

---

### Post by Nemisis_101 on 2008-06-08
It says /ubuntu already exists and is mounted

output -

```

ls /ubuntu/boot

abi-2.6.24-16-generic           initrd.img-2.6.24-16-generic.bak
config.2.6.24-16-generic        memtest86+.bin
grub                            System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic    vmlinuz-2.6.24-16-generic 

```

```

ls ubuntu/boot/grub

default installed-version minix_stage1_5        xfs_stage1_5 
device.map   jfs_stage1_5                  reiserfs_stage1_5 
e2fs_stage1_5  menu.lst         stage1
fat_stage1_5  menu.lst~          stage2

```

Thanks,

---

### Post by meierfra. on 2008-06-08
My bad.

```
gksudo  gedit /ubuntu/boot/grub/menu.lst
```

---

### Post by Nemisis_101 on 2008-06-08
You my friend are a genius, on re-boot i have a grub screen letting me choose my operating system, but it cant find the Ubuntu disk, Windows XP seems to work. But im off to bed and will review the menu.lst file tomorrow, if you can see any noticeable errors please let me know. 

PS - I had already changed the prompt to gedit.

Thanks again!!!!!!!! :guitar:

---

### Post by meierfra. on 2008-06-08
> When I add "gedit" to the prompt it loads up a file but there is none of the "#groot" stuff you asked me to change.


Sorry, I think you edited a post without me noticing.

the "#groot"  is in the middle of all the stuff with a ## in front.


If you still can't find it, post your menu.lst

---

### Post by meierfra. on 2008-06-08
> on re-boot i have a grub screen letting me choose my operating system

That's good. 

>  but it cant find the Ubuntu disk,  

I'll think about what might have gone wrong.

---

### Post by meierfra. on 2008-06-08
deleted

---

### Post by meierfra. on 2008-06-08
I figured out what went wrong.  Just a  stupid mistake on my side. I told you to edit the "menu.lst"  on the Ubuntu partition.  But that one is not being used.  This will fix it:

Boot from the LiveCD

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb1 /ubuntu
sudo mkdir /newboot
sudo mount -t ext3 /dev/sda2 /newboot
sudo cp  /ubuntu/boot/grub/menu.lst /newboot/grub/menu.lst

```


You should also do some cleaning:
```

sudo mkdir /ubuntu/oldboot
sudo mv   /ubuntu/boot/* /ubuntu/oldboot/

```

Reboot and hopefully  you will be able to boot into Ubuntu.

---

### Post by meierfra. on 2008-06-09
Once you succesfully  booted into Ubuntu, there  are a couple of  more things to do:


Step 6 Edit update-grub   **(Edit:  It turns out that this step is uneccessary. Thanks to Herman for pointing this out to me.  Herman also has a section on  "/boot"-partitions on his [web page]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition"))**

```
gksudo gedit /usr/sbin/update-grub
```

Change

kernel_dir=/boot

to

kernel_dir=

(In my update-grub, this was line 1234 (at 84% of the file) 

Save the file.

This step makes sure that  the  "/boot"'s you removed from menu.lst will not reappear after the next kernel update.


Step 7 Cleaning Up

Deleted the folder /oldboot and all its contents.

---

### Post by Nemisis_101 on 2008-06-09
Thanks, it all works great now; there is a menu to choose an operating system and both Windows XP and Ubuntu load perfectly. Slight problem is that I cant delete the "oldboot" directory - it says I don't have permission - but, I guess that doesnt matter to much.

Thanks again,

:guitar: :guitar:

---

### Post by meierfra. on 2008-06-09
> it says I don't have permission

```
gksudo nautilus
```

opens the File browser with root permission.

> 
it all works great now

Good, I was a little worried that  our hard work wouldn't  pay off.

---

### Post by Nemisis_101 on 2008-06-09
That worked perfectly. I will definitely keep that super grub disk handy from now on. I have conveniently labeled the CD box - "God Tool".

Thanks again,

---

