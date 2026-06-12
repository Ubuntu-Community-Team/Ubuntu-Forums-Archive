---
title: "[SOLVED] Not booting, maybe drive order"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by kextyn on 2008-06-17
I just installed Ubuntu Server 8.04 AMD64 and it will not load the GRUB at all.  I suspect it might have something to do with the order of the disks not remaining constant.  My boot drive can show up as sda, sde, or sdh.  I think I may be able to get it to show up the same everytime if I don't change anything in the BIOS but after installation I want to disconnect the optical drive.  I will also be putting a couple more drives in after I get it to boot up.

So what can I do to have the drive mapping remain constant for GRUB?  I have seen a couple other threads about this same topic but no definitive answer yet.

---

### Post by wpshooter on 2008-06-17
If you are saying that you are planning on "permanently" doing away with your optical drive, I think you are making a mistake !!!

---

### Post by Pumalite on 2008-06-17
Can you boot a Live CD?

---

### Post by kextyn on 2008-06-17
Why is it a mistake to run without an optical drive?  I was doing it for over a year previously with Feisty...or was it Edgy, I can't remember.  The problem is I don't have the space for an optical drive.  I have 12 5.25" bays which are full of hard drive bays (4 drive bay takes up 3 5.25" bays).  I could keep the optical drive connected and sitting at the bottom of the case but I'd prefer not to.  I just hook it up when I need it (which is when I install Ubuntu, almost never any other time.)

I can boot to the LiveCD which is how I figured out my drive order kept swapping.  When I installed Ubuntu my boot drive (IDE) was recognized as sda.  device.map also shows hd(0) as sda.  But each time I booted to the LiveCD it was either sde or sdh.

Maybe I'll just have to hook up 10 drives plus the optical and always have that number of drives (they won't stay the same because 2 of them will be changed pretty soon.)  I'll have to do some testing to make sure that the mapping remins constant as long as I don't change anything.

---

### Post by wpshooter on 2008-06-17
IMO, if you have 10 drives in your system, you need to either get several larger drives to replace these or get some different type of system.  I sure would not want to hear the noise that a system with 10 drives in it might make (if the drives were properly cooled) !!!

---

### Post by kextyn on 2008-06-17
> **wpshooter said:**
> IMO, if you have 10 drives in your system, you need to either get several larger drives to replace these or get some different type of system.  I sure would not want to hear the noise that a system with 10 drives in it might make (if the drives were properly cooled) !!!

lol

8 500GB drives...can't afford to upgrade those right now.  They are cooled with 120mm fans which are fairly quiet (I have a 90 and 80mm fan in the same case which I leave off because they're much worse than the 6 120's that are running.)  It's a steel case and the hard drive bays are mounted on rubber grommets.  It's actually pretty quiet compared to my other systems.  But I have it in the laundry room anyway.

---

### Post by Pumalite on 2008-06-17
Did you disconnect any of the drives while you installed Ubuntu Server 8.04?

---

### Post by kextyn on 2008-06-17
> **Pumalite said:**
> Did you disconnect any of the drives while you installed Ubuntu Server 8.04?

No, I left everything plugged in except for 2 drives which have not been plugged in since I put in the disc the first time.

---

### Post by Pumalite on 2008-06-17
Try reinstalling your Grub then:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by kextyn on 2008-06-17
> **Pumalite said:**
> Try reinstalling your Grub then:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Tried that exact solution.  But when I restarted it I had the same problem.  So I put the LiveCD back in and found that the boot drive had changed from sde to sdh.  Even if I change it to the correct hd(#) the device map will not dynamically update it the next time it changes to sda or sde will it?

I didn't have much time to mess with reinstalling GRUB this morning.  I'll mess with it some more when I get home.

---

### Post by meierfra. on 2008-06-19
> I found that the boot drive had changed from sde to sdh. 

As long as you are using UUID's in fstab and menu.lst this should not matter.

>  the device map will not dynamically update

The computer does not use the device.map. So this is irrelevant.

> 
 ....it will not load the GRUB at all. ..
 
Yes, this will happen if you change the boot order in the bios, or add/remove hard drives.  But only the location of the Ubuntu drive matters. So if you install grub to the MBR of the Ubuntu drive and make sure that the Ubuntu drive is always first in the boot order, then you should not have any problems.
(you will have to edit "menu.lst" accordingly. The first number in "#groot (hd?,?)" and in "root (hd?,?)" needs to be changed to a "0".)

---

### Post by mscir on 2008-06-19
I have a similar problem. I have amd machine with one SATA drive with XP on it, and a 2nd IDE drive where I installed 8.04. I tried doing an install letting it load the boot loader to hd0 but when I rebooted xp loaded like normal. I burned a new CD and repeated the install but selected the XP SATA drive. Now I see the bootloader but I can't load either OS, I'm writing this after loading the OS from the CD. Here's what I see:

8.04 2.6.24-16 Error 17 can't mount selected partition
8.04 2.6.24-16 (recovery mode) Error 17 can't mount selected partition
XP Pro Error 13 incorrect or unsupported executable format

Can I repair this from the CD?

---

### Post by meierfra. on 2008-06-19
mscir:  You don't even need the Live CD. Do this

At the grub menu at boot up, select Ubuntu. Press "e" instead of "enter". At the new screen press "e"  again. You get a line which looks like

root (hd0,?)

Change  it to

root (hd1,?).

So change  first number to a "1" but don't change anything else.
Press ``enter'' and then ``b'' to boot.

This should boot you into Ubuntu. Once you successfully booted into Ubuntu
you need to make these changes permanent. Open a terminal  (Applications->Accessories->Terminal) and type

```

cd /boot/grub
sudo cp menu.lst menu.lst.bu
gksudo gedit menu.lst
```

Look for the line

#groot (hd0,?)

Again change the  first number to a ""1"

Look for the windows item:

title  Window XP
root (h1,?)
map (hd0) (hd1)
map (hd1) (hd0)
........

change it to 

title  Window XP
root (h0,?)
.....

(so change the first number to 0 and remove the  two map lines)

Save the file. In the terminal type

```
sudo update-grub
```


Reboot and hope for the best.

---

### Post by kextyn on 2008-06-19
> **Pumalite said:**
> Try reinstalling your Grub then:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I tried this again (not reinstalling, just the instructions in the link) and it worked.  I had to change it to (hd4,0).  But I had to reconfigure some stuff in my computer.  I took out one drive and put another in it's place.  Of course when I tried to start up again it wouldn't load Grub.  So I went through the instructions again (this time it's (hd0,0) and it still didn't work.  Every time I boot up the drive remains at (hd0,0) /dev/sda but it still isn't working.

I just tried again with the LiveCD and it showed up as /dev/sde (even after showing up as sda 3 times in a row with no changes done.)  After changing it back to (hd4,0) in Grub it's still not working.

Ok this time when I booted to the LiveCD and did the "find /boot/grub/stage1" it said it couldn't find it.  The drive is now listed as sdi. Turns out sdi wasn't listed in device.map.  So I added it.

After rebooting it's back to (hd0,0) so I setup Grub again using that.  Of course it's still not working.  What would cause the hard drives to change order so often with nothing being changed?

---

### Post by meierfra. on 2008-06-19
> Of course it's still not working.

Please, provide more details. Does the grub menu appear?
Any error messages?

Did you edit menu.lst according to my last post?  Are you using UUID's in /boot/grub/menu.lst and /etc/fstab?

As long as Ubuntu is on the boot drive and you are using UUUID's in 
menu.lst and fstab, the boot order should not matter.  So maybe something else is wrong.

---

### Post by kextyn on 2008-06-19
> **meierfra. said:**
> Please, provide more details. Does the grub menu appear?
Any error messages?

Did you edit menu.lst according to my last post?  Are you using UUID's in /boot/grub/menu.lst and /etc/fstab?

As long as Ubuntu is on the boot drive and you are using UUUID's in 
menu.lst and fstab, the boot order should not matter.  So maybe something else is wrong.

Grub does not load at all, it just sits there with a blinking cursor.

I know at least the boot drive is listed with the UUID in fstab (the array is listed as /dev/md0 and there's only one other drive that isn't in there at all yet).  I forgot to look in menu.lst though...that might be the issue.  But I figured if it's not even loading the Grub menu then menu.lst isn't the problem.

---

### Post by meierfra. on 2008-06-19
> (the array is listed as /dev/md0 and there's only one other drive that isn't in there at all yet).  

You should have mention that you have a raid. Sorry, I know nothing about raid.

---

### Post by kextyn on 2008-06-19
> **meierfra. said:**
> You should have mention that you have a raid. Sorry, I know nothing about raid.

The RAID shouldn't matter.  It's not a boot drive.  It would just be picked up as an unknown partition because it's software RAID.

The problem lies in the swapping of the drive order.  The boot drive shows up in one of 3 spots (sda, sde, sdi) and I'm guessing sometimes it's because the two SATA controllers are swapping order.

---

### Post by meierfra. on 2008-06-19
Is ubuntu on the boot drive? Or to be more precise: Are  "stage2" and "menu.lst" on the boot drive?

> 
Grub does not load at all, it just sits there with a blinking cursor.

Does it say "grub" or anything else?

I'm trying to figure out whether grub ever got installed to the MBR of the boot drive.

And you are  right, if the grub menu does not appear, it does not matter what's written in  "menu.lst".  Also fstab does not matter.

---

### Post by kextyn on 2008-06-19
I'm fairly certain everything that is needed is on the boot drive.  It was working (see my first post from today) untill I unplugged a hard drive and replaced it.  It was working fine for several reboots untill I changed the hard drive.

I have 9 hard drives installed listed as sda-sdi.  7 of them are part of the software RAID so they're essentially unknown partitions.  All 7 of those plus one more which is a fresh format (NTFS) are on SATA.  My boot drive which was formatted using the "guided - use entire disk" option is the IDE primary master.  I have also kept the CD-ROM connected throughout this process (I'm pretty sure I said earlier I was going to remove it, it's staying for now.)

When it should be loading Grub it doesn't say anything.  If I boot to an Ubuntu CD and choose "Boot from first hard disk" it also just shows a blinking cursor.

---

### Post by meierfra. on 2008-06-19
> I unplugged a hard drive and replaced it. I

Maybe the replaced drive became the boot drive?


> did the "find /boot/grub/stage1" it said it couldn't find i

Did you to "sudo grub" or only "grub"?  Try mounting the  ubuntu partition from the LiveCD.

But it looks more and more like something is wrong with your bios or sata controller.

---

### Post by kextyn on 2008-06-19
Always sudo grub.  Unfortanately I don't think there will be any more BIOS updates for this board (A8N-SLI Deluxe) so I can't really do much about the BIOS.

---

### Post by Pumalite on 2008-06-19
How about mounting the Ubuntu partition on the Live CD and postings a screenshot of /boot.

---

### Post by meierfra. on 2008-06-19
You  haven't really answered this question drive:

Does the hard drive, which CURRENTLY is first in the boot order in the bios, contain the Ubuntu partition?

And is this the same  drive you were able to boot from earlier today?

---

### Post by kextyn on 2008-06-19
> **meierfra. said:**
> You  haven't really answered this question drive:

Does the hard drive, which CURRENTLY is first in the boot order in the bios, contain the Ubuntu partition?

And is this the same  drive you were able to boot from earlier today?

Yes, and yes.

---

### Post by kextyn on 2008-06-19
ls -l /boot/
```
-rw-r--r-- 1 root root  420224 2008-04-10 15:15 abi-2.6.24-16-server
-rw-r--r-- 1 root root  420224 2008-06-04 17:46 abi-2.6.24-19-server
-rw-r--r-- 1 root root   74191 2008-04-10 15:15 config-2.6.24-16-server
-rw-r--r-- 1 root root   74169 2008-06-04 17:46 config-2.6.24-19-server
drwxr-xr-x 2 root root    4096 2008-06-17 20:27 grub
-rw-r--r-- 1 root root 7801606 2008-06-17 20:22 initrd.img-2.6.24-16-server
-rw-r--r-- 1 root root 7209842 2008-06-17 02:49 initrd.img-2.6.24-16-server.bak
-rw-r--r-- 1 root root 7801097 2008-06-17 20:27 initrd.img-2.6.24-19-server
-rw-r--r-- 1 root root 7801379 2008-06-17 20:27 initrd.img-2.6.24-19-server.bak
-rw-r--r-- 1 root root  103204 2007-09-28 11:03 memtest86+.bin
-rw-r--r-- 1 root root 1162081 2008-04-10 15:15 System.map-2.6.24-16-server
-rw-r--r-- 1 root root 1162275 2008-06-04 17:46 System.map-2.6.24-19-server
-rw-r--r-- 1 root root 1928120 2008-04-10 15:15 vmlinuz-2.6.24-16-server
-rw-r--r-- 1 root root 1928216 2008-06-04 17:46 vmlinuz-2.6.24-19-server
```

ls -l /boot/grub/
```
-rw-r--r-- 1 root root    197 2008-06-17 02:54 default
-rw-r--r-- 1 root root    137 2008-06-19 14:54 device.map
-rw-r--r-- 1 root root   8056 2008-06-17 02:54 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-06-17 02:54 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-06-17 02:54 installed-version
-rw-r--r-- 1 root root   8608 2008-06-17 02:54 jfs_stage1_5
-rw-r--r-- 1 root root   4681 2008-06-17 20:27 menu.lst
-rw-r--r-- 1 root root   4259 2008-06-17 20:27 menu.lst~
-rw-r--r-- 1 root root   7324 2008-06-17 02:54 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-06-17 02:54 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-06-17 02:54 stage1
-rw-r--r-- 1 root root 108356 2008-06-17 02:54 stage2
-rw-r--r-- 1 root root   9276 2008-06-17 02:54 xfs_stage1_5
```

fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a9683

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008a179

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005b55e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        9327    74919096   83  Linux
/dev/sde2            9328        9729     3229065    5  Extended
/dev/sde5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eaae1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3e8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b2a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdi: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078814

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1       60801   488384001   fd  Linux raid autodetect

```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=10f6c702-814a-4db4-b5cf-56eca1452cf5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=bbbcd034-d367-4808-b1a1-7beda1f187f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/md0	/raid	ext3	defaults	0	0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

Uncommented sections of menu.lst
```
default		0

timeout		3

hiddenmenu

title		Ubuntu 8.04, kernel 2.6.24-19-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=10f6c702-814a-4db4-b5cf-56eca1452cf5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=10f6c702-814a-4db4-b5cf-56eca1452cf5 ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04, kernel 2.6.24-16-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-server root=UUID=10f6c702-814a-4db4-b5cf-56eca1452cf5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-server
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-server root=UUID=10f6c702-814a-4db4-b5cf-56eca1452cf5 ro single
initrd		/boot/initrd.img-2.6.24-16-server

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by meierfra. on 2008-06-19
(Edit: I  had not see your last post when I posted this)

> Yes, and yes

O.K. I just wanted to be sure. I really would think you would get some kind of Grub errror messages under these circumstances.

Try to access the boot and grub folder from the LiveCD. Since "find /boot/grub/stage1" failed, there might be something wrong with your Ubuntu partition (although that is unlikely since it was just fine earlier today) (edit:  You did this already)

Also get SuperGrub (see my signature) and see whether it detects Ubuntu and/or is able to boot it.

Are where any kind of settings in the bios  you could change?
Are all you drives plugged in correctly? Maybe remove all drives but the Ubuntu drives and see whether Ubuntu  boots again.

Could you post the output of "sudo fdisk -l" and your "menu.lst",
just so that I get a better picture of the whole situation  (edit: you did this already)

Sorry, I currently have  no idea what the problem could be and how to fix it.

---

### Post by meierfra. on 2008-06-19
Change "timeout 3" to "#timeout 3"

and "hiddenmenu" to "#hiddenmenu"

in menu.lst

That won't   really help, but I  want to see whether we can get the grub menu to appear during boot up.

---

### Post by meierfra. on 2008-06-19
Everything looks fine. So I'm  convinced  by now that the problem is caused by your bios, bios settings, Sata controllers and/or   the way your drives are plugged in.

---

### Post by kextyn on 2008-06-19
As far as BIOS settings...

My hard drive boot order is 80GB (boot), SATA1-4, bootable add in cards (which I'm assuming the second SATA controller falls under.)

Changing the menu.lst had no effect.

I unplugged all the drives but the boot drive and it worked fine.  It was #1 on the boot order list in the BIOS and detected as (hd0,0) by Grub.  I should have made it more clear that Grub only failed to find /boot/grub/stage1 when the boot drive was detected as /dev/sdi (no when it was sda or sde.)

After plugging all the drives back in I made sure the boot drive was still #1 in the BIOS and it stopped working again.

---

### Post by meierfra. on 2008-06-19
> My hard drive boot order is 80GB (boot), SATA1-4, bootable add in cards (which I'm assuming the second SATA controller falls under.)
> I unplugged all the drives but the boot drive and it worked fine
> After plugging all the drives back in I made sure the boot drive was still #1 in the BIOS and it stopped working again.

Sorry,  I'm at the end of my wisdom and knowledge.  Hopefully, somebody who knows something about bios and Sata controllers   can provided  better advice.

---

### Post by kextyn on 2008-06-19
I'm trying SuperGrub now.  If I try to do either of the "GRUB => MBR & !LINUX!" options it stalls similar to booting normally.  It just shows the "selectfile /grub/stage1 /boot/grub/stage1" message and a blinking cursor.

It will boot off the menu.lst if I choose " !LINUX! (1) AUTO."

---

### Post by kextyn on 2008-06-19
I solved it.  I should have looked into this before because I've had issues with it in the past.

On the Asus A8N-SLI Deluxe there are 2 SATA controllers (Nvidia, and Silicon Image).  The IDE is also controlled by the Nvidia controller.  I believe if you have all 8 SATA ports filled there is some problem with any additional (IDE) drives being seen outside of the BIOS.  So if I unplugged one or two SATA drives from the Nvidia controller Ubuntu boots just fine.  The workaround is to enable NVRAID for at least one of the drives.

When I had this problem before I had a storage drive on IDE and the boot drive was SATA.  I had NVRAID enabled on the IDE drive to get it to work correctly.  I turned this off when I installed Server this time.  I initially had problems booting off the drive while it had NVRAID enabled so I comnpletely disabled NVRAID and all was well until I filled up all the SATA ports.  I ended up turning on NVRAID for all 4 of the SATA drives hooked up to the Nvidia controller (without actually putting them into an array...they're already part of a software array) and it worked just fine.

---

### Post by Pumalite on 2008-06-19
No wonder.

---

### Post by meierfra. on 2008-06-19
> is some problem with any additional (IDE) drives being seen outside of the BIOS

Thanks for letting us know.  At least now I feel  better about the fact that I kept asking you whether your are booting from the Ubuntu drive.  Seemingly you were not :)

---

### Post by kextyn on 2008-06-19
> **meierfra. said:**
> Thanks for letting us know.  At least now I feel  better about the fact that I kept asking you whether your are booting from the Ubuntu drive.  Seemingly you were not :)

But it was the first drive!!

:)

---

### Post by meierfra. on 2008-06-19
> But it was the first drive!!
O.K. You win.

---

### Post by kextyn on 2008-06-19
> **meierfra. said:**
> O.K. You win.

I'll be waiting for my prize.

---

### Post by meierfra. on 2008-06-19
:popcorn:

---

### Post by VMC on 2008-06-19
Kextyn, if this is solved, you can go to Thread Tools up top and mark it so. thanks

---

### Post by Pumalite on 2008-06-19
:guitar:

---

### Post by mscir on 2008-06-22
> **meierfra. said:**
> mscir:  You don't even need the Live CD. Do this

At the grub menu at boot up, select Ubuntu. Press "e" instead of "enter". At the new screen press "e"  again. You get a line which looks like root (hd0,?) Change  it to root (hd1,?).
So change  first number to a "1" but don't change anything else.
Press ``enter'' and then ``b'' to boot.
This should boot you into Ubuntu. Once you successfully booted into Ubuntu you need to make these changes permanent. Open a terminal  (Applications->Accessories->Terminal) and type
```

cd /boot/grub
sudo cp menu.lst menu.lst.bu
gksudo gedit menu.lst
```

Look for the line
#groot (hd0,?)

Again change the  first number to a ""1"
Look for the windows item:
title  Window XP
root (h1,?)
map (hd0) (hd1)
map (hd1) (hd0)
........

change it to 

title  Window XP
root (h0,?)
.....
(so change the first number to 0 and remove the  two map lines)
Save the file. In the terminal type
```
sudo update-grub
```
Reboot and hope for the best.

Thanks for the post, I booted from the XP Cd, use recovery console to repair the files so I could access XP. I'm disappointed because I installed Ubuntu once before and it went perfectly... select the drive where you want grub to be installed and no problem. I don't know if having one SATA and one IDE is causing a problem but I think I'm going to try to find someone else who's done a similar hardware setup installation before attempting it again. 
Mike

---

### Post by meierfra. on 2008-06-22
> I don't know if having one SATA and one IDE is causing a problem but I think  

Yes, a mixture of sata and ide  drives  often causes the kind of problem you are having.   In fact it happens to me all the time. 

Did you try my instruction?    (To keep the instruction simple, I had made some reasonable guesses, but maybe I guessed wrong and the numbers need to be adjusted)

There is a second way to fix your problem, without erasing the MBR on the windows drive (but this assumes that you can set your  bios  to boot from your Ubuntu drive):

Boot from the Live CD. Open a terminal and type

```
sudo grub
```

and at the "grub>" prompt

```
find /boot/grub/stage2
```

The output will be of the form (hd2,3) . But the numbers will be different.
Still at the grub prompt:

```

root (hd2,3)    (use the output from   "find /boot/grub/stage2")
setup (hd2)     (use the first number from the output)
quit 

```

Then reboot from the Ubuntu drive.  (This should get you at least to the grub menu. If you can't boot into Ubuntu from the grub menu, you will also have to edit menu.lst. Just come back here and ask for help)

If this did not work post the output of
```
 sudo fdisk -l
```



You can avoid the Sata/IDE problem by unplugging the Windows drive, while installing Ubuntu.

---

### Post by mscir on 2008-06-29
> **meierfra. said:**
> YYou can avoid the Sata/IDE problem by unplugging the Windows drive, while installing Ubuntu.

My machine has an F8 option to choose which drive to boot from, after repairing the XP boot I was using F8 to choose Ubuntu/XP -  until I wiped out the Ubuntu bootloader "cleaning up" the disc, so I took your advice and unplugged the SATA drive, fixed the bootloader, now everything works great. Thank You!

---

