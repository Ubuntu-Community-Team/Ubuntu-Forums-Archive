---
title: "Grub booter Errors"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by Sungbob on 2005-04-01
After I finsh installation of warthog 4.10 ( the full install version) and the computer reboots. The BIOS finshes detecting my hardware and it starts to load the grub booter, the screen goes blank and the computer reboots. I actually see the Line "Grub Booter Loading"  for a split second before the screen goes blank.I have tryed reinstalling Ubuntu several times with the same results. Any help on why this is happening would be nice, currently this is my 4th day of using linux in any shape or form, I also think the LIVE CD is one of the most helpful trouble shooting tools out there. :)

Bob The Linux NEWBIE

---

### Post by feneks on 2005-04-02
Hi Sungbob

[B]There are two reasons I can think of:
[/B]First one is not likely I think: This is a bug of installation.
Second one: The Master Boot Record of your disk has a failure which hasn't a come out yet.
There might be other reasons I don't know.

Windows isn't realy using this first part of harddisks and sets it zero by **fdisk /mbr** typed in at DOS prompt. It's possible to set the GRUB behind the mbr and set the mbr itself to zero. 

**To set mbr zero:**
There are two ways. The save method is to use MS DOS or Windows installation. Get to DOS and type in **fdisk /mbr** That's it.
The other way is to use your beloved Live-CD. Become root or use sudo for following command.
```
dd if=/dev/zero of=/dev/hda bs=512 count=1
```
dd writes a zero to each bit of the first block (length 512bytes) of the Masterdevice of the first IDE-controller. (got it?  :mrgreen: )
This code is from [http://linuxgazette.net/issue63/okopnik.html](http://linuxgazette.net/issue63/okopnik.html) I haven't used it myself but my impression is that linuxgazette is source of good stuff.

**To install GRUB behind the mbr:**
This should be possible using the expert mode of installation. Don't worry as long you just hit [Enter] when you are asked something it will do the same as in normal way. You'll just have to have a keen eye on GRUB. You should be asked if you want to install GRUB to mbr. -say *no* and all should run. 

Hopefully Ubuntu is asking. The last time I did something like this was with Debian Linux (woody) some years ago.

---

### Post by feneks on 2005-04-02
I just read in an other posting of you that you have a dualboot. Things are getting complicated. The problem is if I'm right and you can't use mbr for GRUB, how should Ubuntu be started? WindowsXP has a Bootloader too. It is possible to boot Linux with this one. A search with Google for this topic should help.

I don't think you have a problem with the videocard. Because then you shouldn't have seen anything of GRUB. But I can be wrong.

---

### Post by feneks on 2005-04-05
I did rethink the problem and now I think it might be a videocard problem.

The framebuffer HOWTO at [http://www.faqs.org/docs/Linux-HOWTO/Framebuffer-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Framebuffer-HOWTO.html) tells us many details. When you install Ubuntu you first get to a bootscreen and you can have a look at help-texts by pressing [F1] to [F7] i think. You'll have to type in
```
linux vga=XXX 
```
```
 # vga=XXX sets the framebuffer console to a specific resolution.
 # Here is a table you can use so it can help you decide
 # what resolution you want to use:
 #       colour          depth   | 640x480  800x600  1024x768 1280x1024
 #       256             (8bit)  |  769      771       773      775
 #       32000           (15bit) |  784      787       790      793
 #       65000           (16bit) |  785      788       791      794
 #       16.7 Mill.      (24bit) |  786      789       792      795

```source: [http://linuxbasics.org/Members/SRM/Published/vga_set/view](http://linuxbasics.org/Members/SRM/Published/vga_set/view)

Try a low-end resolution. If it works you can slowly increase the resolution in the file /boot/grub/menu.lst after installation.

---

### Post by Sungbob on 2005-04-12
Dear Feneks,
Thank you so very much for spending the time to help me out.  \\:D/  However since my post on the grub booter error on warty, I have been able to boot up on warty alone after losing my HD partitions and hence losing Windows Xp Pro. However I wanted to try out KDE so I started upgrading to hoary. After upgrade nothing at all worked right so I downloaded hoary install ISO image and reinstalled hoary. Everything worked right, I usually have to use the linux boot CD, in this CD is a program called ranish, I use ranish to change MBR to boot up before grub. This worked to boot correctly. However after some apt-get update/upgrade, I started receiving "GRUB GRUB hard disk error" which i learned has something to do with the geometery of the HD. So after spending some 2 days trying to figure out what went wrong I gave up and reinstalled hoary, but now when i change the MBR with Ranish i just get the same problem as before. It loads stage1 then reboots. :( I am almost ready to scrape the idea of using Linux and going back to windows since I haven't had a day since i installed ubuntu, without having problems :(. I'll try and fight the good fight :)

Sungbob
Still a Linux Newbie  ;-)

---

