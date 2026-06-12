---
title: "Ubunto doesn't start from a slave drive (was master at the time of the installation)!"
date: 2005-02-06
forum: Installation &amp; Upgrades
---

### Post by Mikael on 2005-02-06
Hi folks!

I decided to go Linux the other day, because I want to learn something new (tired of Windows). So, I heard pretty much nothing but positive things about Ubuntu and decided to give it a try. I've had slight experience with Mandrake and Red Hat before.

Now to the problem: I had a spare 20GB drive and I decided to put Ubuntu on that one and then just switch which drive to boot from thru BIOS. I removed my Windows drive temporarily and put the 20GB alone in the computer, jumpered as master off course. I then proceeded to install Ubuntu and everything went smooth as cream. I then decided to add my Windows drive to the mix. So, I put the 20GB Ubuntu drive as slave drive and the Windows drive as master.

With the Windows drive put back in I tried to boot. BIOS was set to boot from HDD-0 and Windows fired up fine. Great! So, what if I told the BIOS that I wanted to boot from HDD-1 (Ubuntu drive) instead? Well, here's the result:

[http://upl.silentwhisper.net/uplfolders/upload1/KernelPanic.jpg](http://upl.silentwhisper.net/uplfolders/upload1/KernelPanic.jpg)

Great, my first Kernel Panic... 8-[ 

So, was I wrong in thinking that I could just move drives from master to slave (HDD-0 to HDD-1) without affecting the operating system on the disk? I'd be very grateful for some help with this.

EDIT: Would i be right in assuming that Ubuntu looks for files on hda1, while in fact hda1 turned into hda2 (or would that be hdb1...?) the moment I put the disk as a slave to my Windows drive? If so, where can I change this? I have a Ubuntu Live-CD if that helps matters...

---

### Post by AlBundy on 2005-02-06
Your Grub Menu's source (You can find it in /boot/grub/menu.lst) like this if you install Ubuntu to primary master: 

title		Ubuntu, kernel 2.6.8.1-4-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-4-386
savedefault
boot


You must to write to this, if you use this for primary slave (And your primary master's haven't got extended partition)

title		Ubuntu, kernel 2.6.8.1-4-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.8.1-4-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-4-386
savedefault
boot

---

### Post by Mikael on 2005-02-06
[QUOTE=AlBundy]Your Grub Menu's source (You can find it in /boot/grub/menu.lst) like this if you install Ubuntu to primary master: 

title		Ubuntu, kernel 2.6.8.1-4-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-4-386
savedefault
boot


You must to write to this, if you use this for primary slave (And your primary master's haven't got extended partition)

title		Ubuntu, kernel 2.6.8.1-4-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.8.1-4-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-4-386
savedefault
boot[/QUOTE]
Thanks! I found my way to that file and it looked like this:


title		Ubuntu, kernel 2.6.8.1-4-386 
root		(hd0,**0**)
kernel		/boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-4-386
savedefault
boot


Notice the zero in bold, where you said it would be a one. Anyway, I edited the file to look like this:


title		Ubuntu, kernel 2.6.8.1-4-386 
root		(hd**1**,0)
kernel		/boot/vmlinuz-2.6.8.1-4-386 root=/dev/hd**b**1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-4-386
savedefault
boot

The two bold things were the only ones changed. Now I tried to boot from HDD-1 again, but it didn't work... Check out the error:

[http://upl.silentwhisper.net/uplfolders/upload9/BadStuff.jpg](http://upl.silentwhisper.net/uplfolders/upload9/BadStuff.jpg)

So, what now? I know that Ubuntu identifies the other disk (the second disk on the IDE channel, containing Ubuntu) as hdb (or as Grub would call it, hd1). So, wouldn't everything be fine if I changed (hd0,0) to (hd1,0) and /dev/hda1 to /dev/hdb1? I guess not... In other words: More help is needed.

EDIT: Okay, I've done a lot of reading and trying now. I'm pretty convinced that the changes I did to menu.lst are correct. Grub sees a partition, but can't recognize it. So, I tried to change from "Auto" to "LBA", "CHS" and "Large" in BIOS, but none of the options made Ubuntu boot.

So, I'm back were I started, with no idea on how to make this work. Ubuntu still fires up fine if I change the file menu.lst back to its original form and run the 20GB drive as primary master instead. Why does it have to be so damn hard to get a working Linux install... :cry:

EDIT2: Ohh, and the drive is run in CHS mode when it is set to "Auto" in BIOS. Ubuntu boots up fine when the drive is in CHS mode, as long as it is the primary master.

---

### Post by thestarman on 2005-02-07
[QUOTE=Mikael]So, what now? ... In other words: More help is needed.
.......
So, I'm back were I started, with no idea on how to make this work. Ubunto still fires up fine if I change the file menu.lst back to its original form and run the 20GB drive as primary master instead. Why does it have to be so damn hard to get a working Linux install... :cry:[/QUOTE]

   First, it wouldn't have been all that difficult if you had left your Windows drive in the machine as Primary, and then installed to the Slave/Secondary drive Ubuntu.  It would have installed GRUB to your Primary drive's first track, but that's how you gain the ease of dual booting... by using a boot manager! OK moving on....

   You were getting closer...  well, at least when you saw the "Kernel Panic" and then knew that Ubuntu tried to boot up!  THE PROBLEM THEN was:  You must also change the file:  **/etc/fstab**  (a plain text configuration file that tells Ubuntu where all its filesystems that are to be mouned during boot up are located).
    To do so, as 'root', open the file in any text editor ('**vi**', '**pico**' -- this is nice for newbies, or enter:
**gedit /etc/fstab** in the **Root Terminal**, and wait for the GUI app. to start up).

    From what I've seen above, I think you'll know what to change, but here's an example from my own install *which is located in the Extended Partition of a Second Drive*:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb9       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb7       /boot           ext2    defaults        0       2
/dev/hdb8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto  0       0
```
    Anyone should be able to see from this, that Linux OSs do not like to be moved around very much ;-) , but if you do enough studying and keep notes on this, it is certainly possible to accomplish.

   If this still doesn't help, let me know what happened....  Daniel:
[http://thestarman.dan123.com/FF.html](http://thestarman.dan123.com/FF.html) .

---

### Post by Mikael on 2005-02-07
Thanks for the answer **thestarman**!

I was actually able to boot Ubontu from the 20GB primary slave drive, just before I read this! Here's what I changed in Grub's menu.lst file:

title Ubuntu, kernel 2.6.8.1-4-386
root (hd**0**,0)
kernel /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.8.1-4-386
savedefault
boot

I changed the 1 to a 0. So, now the root refers to the first drive (which should be the primary master WindowsXP disk), but the third line still has a reference to hdb1 (which should be the primary slave Ubuntu disk). This doesn't make much sense to me, but I'm sure someone can explain this.

Now, Ubuntu booted fine, but there was a problem with accessing hda1 (Windows partition). I thought it wasn't mounted at startup, so I mounted it myself, but got the message that it was already mounted as "/". So, Ubuntu thinks that hda1 is the Ubuntu partition and it also thinks that hdb1 is the Ubuntu partition! Things are getting crazy here... 8-[ 

Anyway, here's another screenie from Grubs command line during boot up:

[http://upl.silentwhisper.net/uplfolders/upload8/Grub.jpg](http://upl.silentwhisper.net/uplfolders/upload8/Grub.jpg)

hd0 is identified as the Ubuntu disk and hd1 as the Windows disk (even though it can't seem to identify NTFS...). It's exactly the opposite of what it should be. I've already spent hours and hours trying to find a solution to this so, please, if anyone knows anything, share it!

EDIT: Wait a minute... I might have solved this problem now! I'll be back i a couple of minutes!

---

### Post by Mikael on 2005-02-07
Okay, I figured out how to mount hda1 and hda5 so that I can reach my Windows stuff from Ubuntu. Took some tampering with the fstab file, but eventually worked out fine.

Now there's only one problem left: How do I make Grub boot to WindowsXP? The physical setup is this:

Primary Master: WindowsXP disc with two NTFS partitions
Primary Slave: Ubuntu

If I'm not totally off here, this would suggest that the Windows drive would be called hd0 or hda and the Ubuntu drive would be called hd1. That's, however, not the case here. This is the same picture posted in my previous post:

[http://upl.silentwhisper.net/uplfolders/upload8/Grub.jpg](http://upl.silentwhisper.net/uplfolders/upload8/Grub.jpg)

The Windows drive is hd1, even though it's physically the primary master! The fact that the partitions aren't recognised makes it impossible to boot from it. Why is this happening and what do you think I can do about it?


**EDIT:** Everything works now! As you can see from the above image it seems as if Grub has misunderstood my harddrive config. So I thought "Why not just play along?". Said and done. Instead of:

title WindowsXP
root (hd0,0)
makeactive
chainloader +1 

like it should read when Windows is on the first partition of the primary master, I wrote these lines to Grub's menu.lst:

title WindowsXP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

AND IT WORKS! It was 8 hours work, but it was worth it! Ohh, the sheer pleasure of achieving the "impossible"! 8) Now I've done what I set out to do, namely dual boot Linux with WinXP while preventing any modification to the Windows drive.

Now there's just one important question left to answer:

Why, ohh why, doesn't Grub understand that the Windows drive (primary master) is supposed to be indentified as hd0!?

Somebody has got to have an answer to that...

---

