---
title: "grub_puts error after 9.10 -&gt; 10.04 upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by aumshantih on 2010-04-30
Namaste.

I just did an upgrade of 9.10 amd64 system to 10.04.
I'm pretty sure I messed up the grub2 upgrade.

When I try to start normally, I get an error like this:
> GRUB loading.
Welcome to GRUB!

Entering rescue mode...
Error: the symbol 'grub_puts' not found
grub rescue> _

I currently have 3 HD's on the system, all identical, with two of them in a software RAID.

Now, I *can* boot into 10.04 - by pressing F8 on startup, I can select the second of the three HDs, and it will start up normally.  

When I do start up, everything seems to work fine, but whenever I reboot, I get the same grub error, and have to manually hit F8 and select the second drive.

Any tips to fix this would be great.

Thank you.

---

### Post by fabrizio.benedetti on 2010-05-01
It just happened the same for me; I used to have a grub menu to dual-boot Karmic and XP, after upgrading to 10.04 I'm stuck to the "grub_puts_" / grub rescue screen.

I'm downloading the install ISO and I will try this procedure: 
[FONT=monospace]
[/FONT]run "grub-install --recheck /dev/md0" from a livecd in chroot
([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=563822](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=563822))

If this fails, I will try super-grub-disk... ([http://tinyurl.com/yl8m9p4](http://tinyurl.com/yl8m9p4))

Crossing my fingers... :confused:

  Fabrizio

---

### Post by Jellyffs on 2010-05-02
It might help:

[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

---

### Post by frantid on 2010-05-02
For some reason, the later kernels don't see the drives in the same order as the bios.  (I started seeing this in Karmic after the last kernel update).  So if you have multiple drives and use the bios to set the boot drive, you might run into a problem.

I fixed it by modifying my device.map in /boot/grub.  I set it up to match how my bios sees the drives.

lynx sees it as

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
(hd4)    /dev/sde

but my bios boot disk is /dev/sdb, so grub sees that as hd0.  My device.map had to be:

(hd0)    /dev/sdb
(hd1)    /dev/sda
(hd2)    /dev/sdc
(hd3)    /dev/sdd
(hd4)    /dev/sde

I ran update-grub, it fixed the grub.cfg

---

### Post by guyg on 2010-05-02
Experiencing the same problem following a 9.10 -> 10.04 upgrade. Good thing this is not a machine I use for anything important... Anyway, this is one showstopper too many. Bye bye Ubuntu.

---

### Post by aumshantih on 2010-05-04
> [http://www.webupd8.org/2010/05/fix-s...ound-when.html](http://www.webupd8.org/2010/05/fix-s...ound-when.html)

Thank you, the instructions here worked great!
I made a bootable USB key, and ran through the steps listed and on a reboot it rescanned all my drives and so far things look good.

---

### Post by wavesound on 2010-05-09
I See so this is ecepatable on a new upgrade?

I Now have a hosed system,  Was there no testing off the installation for people with multiple disks?

I cant even boot into my 64studio drive now!

I'm getting convinced some of the Devs work for MS on the side.
This for a user is a total show stopper 

So I'm sat here with grub rescue looking at me, any ideas what this does?

Cheers
Bob

---

### Post by gweinstein on 2010-05-13
Tried both proposed solutions (by frantid and at [http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)).  Both failed.  Any other suggestions?

Here is the output from fdisk -l:


```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        1046     8393962+  82  Linux swap / Solaris
/dev/sda2            1047       19452   147846195   83  Linux

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9662    77609983+  83  Linux
/dev/sdb2            9663       19452    78638175    5  Extended
/dev/sdb5   *        9663       19048    75393013+  83  Linux
/dev/sdb6           19049       19452     3245098+  82  Linux swap / Solaris


```
My boot disk is actually sdb5.

Thanks in advance.

(currently I am booting with super-grub-disk)

---

### Post by alienprdkt on 2010-05-13
Well atleast i have found some solutions for my problem to try and fix my desktop again!

Also if I fix the solution can I move /boot to its own partition just by copy/pasting?

and re-editing /etc/fstab?

(even though fstab has been giving mew problems mounting my drives, had to write a custom script & place it into /etc/rc0.d for startup
and shutdown a umount script and place it in /etc/rc6.d)

can this be done by a copy -r -p and paste?

Am at work right now but will test when I get home. Will also let this thread know if the solution worked or not. Damn I should have backed up grub!

---

### Post by alienprdkt on 2010-05-13
YAY [http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

it worked!

great !!! 

what a relief! now I can sit back and enjoy lynx :)

Well thanks everyone for replying to aumshantih's thread, while I asked the same question had the same problem all I got was over 70 views and ZERO replies.

---

### Post by sallymc on 2010-05-14
I CAN HELP!  Have just had the exact problem, and fixed it.  Go to :

 ['alexandre ***jelly kernel***' french karmic]("http://www.google.com/search?hl=en&ei=Dg3tS8XnEqHYmwPSzq2qDg&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CBEQBSgA&q=%27alexandre+jelly+kernel%27+french+karmic&spell=1")

 on Google.  The first article is : 
**[Fix Symbol 'grub_puts'  Not Found When Migrating From  Ubuntu *Karmic*]("http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html")**

Follow his instructions and you will be delighted.  By the way, you will  need a second working computer in order to access these instuctions,  and a live Ubuntu CD to boot from.
Note that his first instruction :  
sudo fdisk-l

has a space after fdisk, before the dash.

Good luck and keep smiling.  I LOVE UBUNTU.

:smile: Sallymc

---

### Post by pimseb on 2010-05-15
Hello,

I've updated my laptop from Karmic to Lucid. I've downloaded the iso and "burned" it on my USB stick using unetbootin.
I've installed Lucid Lynx but after rebooting I get the grub-puts error.
So I've followed this : [http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)
The problem is that the grub seems to be on my usb drive. I can see the grub when the usb drive is inserted in my laptop (and boot on lynx or windows).
But when I remove the usb stick, I still see this annoying grub_puts errror.
What can I do ?
I think there is a problem with my sda and sdb. But I dont see a device.map in /boot/grub

---

### Post by BartlebyScrivener on 2010-05-16
I got the dreaded grub_puts error after upgrading a dual boot (XP Jaunty) system. I tried this one:

[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

It seems to work for many people on this thread, but I got an error message after the last command. And was then right back at the grub_puts error message.

I found the following Ubuntu documentation much more helpful. You need a LIVE CD to do it. Mine was a Jaunty LIVE CD, but it still worked fine even though I had upgraded to Lucid.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

bs

---

