---
title: "[SOLVED] GRUB fails to install - has worked in the past?"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by petgraveyard on 2008-02-22
Hello!

The other day I installed Solaris...I hated it and now I'm going back to Ubuntu.  I had Ubuntu on the partition that I reformatted and installed Solaris on.  Today I booted up with my old Linux install CD, did it in safe graphics mode (because my system only works with vesa until I install the nVidia drivers manually later).

The install fails with a "fatal error" when it cannot install GRUB in hda(0).

I tried booting my computer, and it's clear that GRUB totally destroyed my MBR, because booting anything fails.

Now, you see, I had this EXACT problem yesterday on my friend's laptop, so I thought my CD might be messed up or something.  I downloaded Ubuntu, verified the MD5 checksums, burned the ISO, checked the CD for defects, and booted up.  Now the error occurs AGAIN!  So, in short, I know it's not an issue with my CD.

What can I do?  I could try to just wipe out my whole hard drive and make a new partition table, but then I would lose Vista, and Vista is a pain to install!

Does anybody have any advice?

BY THE WAY, I have installed Ubuntu EASILY over 5 times on this computer without ANY problems (that includes with GRUB).  What's going on???

---

### Post by Herman on 2008-02-22
:) How about booting your Ubuntu Live CD and posting here a copy of the output from 'sudo fdisk -lu' to begin with, please, if iyou still have a DOS MBR and not a SUN disc label we may be able to see what's wrong.
```
sudo fdisk -lu
```Regards, Herman :)

---

### Post by petgraveyard on 2008-02-22
> **Herman said:**
> :) How about booting your Ubuntu Live CD and posting here a copy of the output from 'sudo fdisk -lu' to begin with, please, if iyou still have a DOS MBR and not a SUN disc label we may be able to see what's wrong.
```
sudo fdisk -lu
```Regards, Herman :)

Here we go!

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008270a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   488392064   244196001    7  HPFS/NTFS
/dev/sda2   *   488392065   964398014   238002975   bf  Solaris
/dev/sda3       964398015   976768064     6185025   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

Hmm....that's really weird.  I installed Linux already and it reformatted and everything, yet it still says Solaris.  You know what, I hate Solaris more and more.

---

### Post by Herman on 2008-02-22
:) Maybe try using either Gnome Partition Editor in your Ubuntu Live CD if you can get it to work with your video card 'System'-->'Administration'-->'Gnome Partition Editor'. 
Or use [Gnome Partition Editor]("http://gparted.sourceforge.net/") in its own CD. those are free and only a small download and they are excellent software, very useful.
Try deleting your Solaris partition before you begin your install, so it will be less confusing for you. 
:) Also, make sure you don't leave any other devices plugged in while you're installing such as  USB flash memory stick or anything. Unplug things like that first just in case those can cause any kind of mix-up.
:) Then try installing again.

---

### Post by terry-s on 2008-02-22
> **petgraveyard said:**
> Hello!
The other day I installed Solaris...I hated it and now I'm going back to Ubuntu.  I had Ubuntu on the partition that I reformatted and installed Solaris on.  Today I booted up with my old Linux install CD, did it in safe graphics mode (because my system only works with vesa until I install the nVidia drivers manually later).

The install fails with a "fatal error" when it cannot install GRUB in hda(0).

I tried booting my computer, and it's clear that GRUB totally destroyed my MBR, because booting anything fails.

Now, you see, I had this EXACT problem yesterday on my friend's laptop, so I thought my CD might be messed up or something.  I downloaded Ubuntu, verified the MD5 checksums, burned the ISO, checked the CD for defects, and booted up.  Now the error occurs AGAIN!  So, in short, I know it's not an issue with my CD.

What can I do?  I could try to just wipe out my whole hard drive and make a new partition table, but then I would lose Vista, and Vista is a pain to install!

Does anybody have any advice?
BY THE WAY, I have installed Ubuntu EASILY over 5 times on this computer without ANY problems (that includes with GRUB).  What's going on???

Before you do anything drastic with your partitions --- 
you might try making a grub boot 'floppy' diskette or boot CDROM. 
That's the most reliable tool for setting up grub. 

If your computer can boot from 'floppy'-diskette, that would be the easiest 
route to try.  (But if it can only boot from CDROM, you'd need a machine 
that can write a CDROM while it's running your linux -- and if your only linux 
is on the live CDROM, hmm, that may be a problem :( until  you can find a 
machine with 2 cd drives, one bootable and another writable).

The ubuntu live-CD contains the files needed for making a grub boot disk.  
They are located in your ubuntu live-cd tree at

      /usr/lib/grub/i386-pc/stage*

and if you choose the floppy route, the boot disk is made by giving the following commands
after putting a floppy into the drive (and existing data on the floppy will be lost by 
doing these write commands, not surprisingly):-

cd /usr/lib/grub/i386-pc
ls           

[and the listing after 'ls' should confirm that the stage files are in your current directory:  
If all is ok, then: ]

sudo dd  if=stage1  of=/dev/fd0  bs=512  count=1
sudo dd  if=stage2  of=/dev/fd0  bs=512  seek=1

(The machine should report 1 record transferred after the first command,
and about 215 record transferred after the second.  That's your grub boot floppy made.)

(These instructions are from 
[ http://www.gnu.org/software/grub/manual/grub.html]( http://www.gnu.org/software/grub/manual/grub.html)
-- see section 3.1 for making a grub boot floppy, and if you need the grub boot CD-ROM, 
-- see section 3.4 for making a grub boot CD-ROM. )

To install a bootable grub on the hd of your machine, now close down the live linux CD, 
remove the CD disk, and boot up the machine using your grub boot disk.

You should then see a > command prompt.

There are several instructions for installing bootable grub on the hard disk, 
in section 3.2 ('Installing grub natively'), and  I suggest you go through the 
whole procedure of doing (first) some 'find' operations, like this:--

>  find  /boot/grub/menu.lst    (and then _also_)
>  find  /boot/grub/stage1

Check through the lists of partitions returned in response to these commands.  

In your case, the machine should probably tell you something like (hd0,1) both times. 

btw,  "(hd0,1)" equates to hda2 in linux-speak, and to sda2 in ubuntu-speak: 
grub starts counts from 0, and 'disk a' is 'disk 0' to grub.  

If it tells you more than one partition id, then you have to decide on your 
background information which is the right one to be nominated as root partition 
for ubuntu.

If you get nothing, or only one positive return out of the two 'find' commands, 
then you don't seem to have a properly installed grub boot directory yet, so 
trying to put grub on the boot record probably may not help at this stage.

If you do get a positive return, you could then try installing grub with

> root (hd0,1)   [or whatever the correct partition id was, from the find commands] 

[and then]

> setup (hd0)   [_provided_ you want your grub to be the main and first bootloader
on your machine, which it seems you probably do -- otherwise see grub manual, sec.3.2.]

The grub disk will probably report failure to find a few stage 1.5 grub files or something, 
but as long as it ends up also telling you success with the installation, you should 
be ok, and should now have a bootable computer.  It will initially let you boot 
whatever OSs are properly specified in your root-partition's /boot/grub/menu.lst file.  

If it turns out that the menu.lst file is not correctly configured, you can still edit the 
boot parameters from the grub boot-up screen, to try and find an amendment that works,
and then when you are in, you can incorporate the change into /boot/grub/menu.lst,
with your usual text editor.

Good luck!
Terry

---

### Post by petgraveyard on 2008-02-22
> **terry-s said:**
> Before you do anything drastic with your partitions --- 
you might try making a grub boot 'floppy' diskette or boot CDROM. 
That's the most reliable tool for setting up grub. 

If your computer can boot from 'floppy'-diskette, that would be the easiest 
route to try.  (But if it can only boot from CDROM, you'd need a machine 
that can write a CDROM while it's running your linux -- and if your only linux 
is on the live CDROM, hmm, that may be a problem :( until  you can find a 
machine with 2 cd drives, one bootable and another writable).

The ubuntu live-CD contains the files needed for making a grub boot disk.  
They are located in your ubuntu live-cd tree at

      /usr/lib/grub/i386-pc/stage*

and if you choose the floppy route, the boot disk is made by giving the following commands
after putting a floppy into the drive (and existing data on the floppy will be lost by 
doing these write commands, not surprisingly):-

cd /usr/lib/grub/i386-pc
ls           

[and the listing after 'ls' should confirm that the stage files are in your current directory:  
If all is ok, then: ]

sudo dd  if=stage1  of=/dev/fd0  bs=512  count=1
sudo dd  if=stage2  of=/dev/fd0  bs=512  seek=1

(The machine should report 1 record transferred after the first command,
and about 215 record transferred after the second.  That's your grub boot floppy made.)

(These instructions are from 
[ http://www.gnu.org/software/grub/manual/grub.html]( http://www.gnu.org/software/grub/manual/grub.html)
-- see section 3.1 for making a grub boot floppy, and if you need the grub boot CD-ROM, 
-- see section 3.4 for making a grub boot CD-ROM. )

To install a bootable grub on the hd of your machine, now close down the live linux CD, 
remove the CD disk, and boot up the machine using your grub boot disk.

You should then see a > command prompt.

There are several instructions for installing bootable grub on the hard disk, 
in section 3.2 ('Installing grub natively'), and  I suggest you go through the 
whole procedure of doing (first) some 'find' operations, like this:--

>  find  /boot/grub/menu.lst    (and then _also_)
>  find  /boot/grub/stage1

Check through the lists of partitions returned in response to these commands.  

In your case, the machine should probably tell you something like (hd0,1) both times. 

btw,  "(hd0,1)" equates to hda2 in linux-speak, and to sda2 in ubuntu-speak: 
grub starts counts from 0, and 'disk a' is 'disk 0' to grub.  

If it tells you more than one partition id, then you have to decide on your 
background information which is the right one to be nominated as root partition 
for ubuntu.

If you get nothing, or only one positive return out of the two 'find' commands, 
then you don't seem to have a properly installed grub boot directory yet, so 
trying to put grub on the boot record probably may not help at this stage.

If you do get a positive return, you could then try installing grub with

> root (hd0,1)   [or whatever the correct partition id was, from the find commands] 

[and then]

> setup (hd0)   [_provided_ you want your grub to be the main and first bootloader
on your machine, which it seems you probably do -- otherwise see grub manual, sec.3.2.]

The grub disk will probably report failure to find a few stage 1.5 grub files or something, 
but as long as it ends up also telling you success with the installation, you should 
be ok, and should now have a bootable computer.  It will initially let you boot 
whatever OSs are properly specified in your root-partition's /boot/grub/menu.lst file.  

If it turns out that the menu.lst file is not correctly configured, you can still edit the 
boot parameters from the grub boot-up screen, to try and find an amendment that works,
and then when you are in, you can incorporate the change into /boot/grub/menu.lst,
with your usual text editor.

Good luck!
Terry

I kind of did a little research of my own and got past making my own GRUB boot disk like you said by using Super Grub (I had to record this CD using another machine that had a dual optical drive setup like you mentioned).  Super Grub did absolutely nothing for me, but I used it to replace whatever weird grub installation was on the MBR with some weird Windows bootloader (the point was to get something that I knew Ubuntu could replace because it has done so before).  This bootloader didn't work to boot my Windows, in fact, it didn't do anything - which was perfect, my mobo wasn't giving me a message in red anymore.

Following Herman's instructions, I tried to use gParted on my LiveCD back when I could actually use the LiveCD - but it didn't work!  I plugged in my old PC with a two optical drive (ROM, burner) setup and burned myself a gParted LiveCD, then I used that to delete the two old partitions (Solaris & Solaris swap).

I then booted with the alternate CD (since for some reason the graphical I had been using just magically stopped working!) and I installed Ubuntu with that - it worked, GRUB and all!

It seems those Solaris partitions were really tripping up the Ubuntu install, either that or the weird, corrupt MBR.  The point is, everything is working now!

Thank you very much, both of you, for your help!

---

### Post by Herman on 2008-02-23
:cool: Cool! Thanks for letting us know you got it fixed.
Regards, Herman :)

---

