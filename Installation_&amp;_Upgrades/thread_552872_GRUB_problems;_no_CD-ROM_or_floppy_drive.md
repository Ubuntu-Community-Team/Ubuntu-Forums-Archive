---
title: "GRUB problems; no CD-ROM or floppy drive"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by hobybuntu on 2007-09-17
Hi everyone.  I have a big problem with my Dell Inspiron 8200 that I was hoping to get some help with.  Long story short, my GRUB is messed up; I get error 15 when I boot the computer and GRUB tries to start.  To make matters worse, my laptop's CD-ROM seems to be broken; it worked well enough to let me run the live cd a few weeks ago, but now it refuses to recognize my burnt CDs (it thinks they are blank CDs--this behavior occurs in both Windows and Ubuntu).  I also no longer have the floppy drive bay that came with the laptop.

Does anyone know of any ideas for how I can get my computer back?  If I could even access GRUB, I could edit the menu items to get myself into Ubuntu and then fix it from there.  But unfortunately, that doesn't seem to be possible.  I really don't want to wipe my Ubuntu partition, and I definitely CAN'T wipe the Windows one (wife would kill me).  Any ideas?

Thanks a lot!  I hope someone can help!

---

### Post by Herman on 2007-09-17
Hello hobybuntu,
I would try cleaning the lens in the CD drive with a cotton bud and some methylated spirits first, and see if that helps if you haven't tried that already.

You might be able to use [Super Grub Disk]("http://geocities.com/supergrubdisk/") for USB for booting with if you have no floppy or CD-ROM drive, but only if your computer's BIOS supports booting from USB.
To check, try tapping your F8 or F12 or some other key (look in your owners manual maybe) for a BIOS boot menu. Here is a link to explain exactly what I mean, with illustrations too, [  How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).
If your BIOS has a similar function then you are in luck!
Download a [Super Grub Disk]("http://geocities.com/supergrubdisk/") for USB and use that to boot your computer! :)

Here are a few extra links that might help you, [Hardware Guys .com Super Grub Disk thread]("http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=21;t=5489"),

[How to Make your Super Grub USB Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk").

[     Grub error 15]("http://users.bigpond.net.au/hermanzone/p15.htm#15").

Super Grub Disk should boot Ubuntu and Windows for you. :)

Regards, Herman  :)

---

### Post by hobybuntu on 2007-09-17
Herman,

Thanks a ton!  As soon as I read your post (and realized what a cotton bud is--we call them Q-tips in the US) I grabbed a cotton bud tried to clean the lens of my CD-ROM.  I didn't even have methylated spirirts, but I figured I might as well give it a try; it worked!  I'm booting from the Ubuntu live disk right now.

Now to just read up on exactly how to fix my GRUB install from the live CD.  Awesome!

Thanks again, Herman.  I really appreciate it.

---

### Post by Herman on 2007-09-17
:) Hee- hee, alright! :)
Sometimes the simplest little things cause the biggest problems eh?   Isn't it amazing how a little spec of dust in the wrong place can bring all this technology to its knees?  :) 

I wasn't sure what to call a Qtip, so everyone would know what I meant. Yes, a cotton bud is the same thing as a Qtip.
What do you call methylated spririts in the US?  I seem to remember when I lived in Canada that we used a different name for that, but I'm not sure. 

Here's a link about how to mount your hard disk installed Ubuntu system in your LiveCD Ubuntu and access certain vital files that sometimes need to be operated on in this manner, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000]. :)

Regards, Herman :)

[/COLOR][/COLOR]

---

### Post by hobybuntu on 2007-09-18
Yeah, I can't believe that it fixed so easily.  Just brushed the lens with the Q-tip and everything worked like a charm.  Hilarious.

To be honest, I had no idea what we call methylated spirits here in the US.  I looked on Wikipedia.  Turns out we call it denatured alcohol.  I've never used the stuff, personally, although it sounds like it must be useful.

After booting into the live CD, I had another adventure fixing GRUB.  Having read a lot of forum posts about the problem, I first tried this method from the terminal:

$ su grub
$ find /boot/grub/stage1
$ root (hdx,x) [whatever the respone from "find /boot/grub/stage1" is]
$ setup (hd0)

Unfortunately, I was told it couldn't find the file.  Then I tried to chroot my Ubuntu drive, but was met with an error on that too (it's been two days since I did this, so I forget what the error was, unfortunately).  I then read that sometimes it helps to mount the disk in a folder given the same name as the device (i.e. my disk is /dev/sdb so I mount it at /mnt/sdb).  I tried this, and was able to chroot.  Then I tried "grub-install /dev/sdb" and got another error (again, can't remember what it was).  Finally, after more searching and reading forum posts, I was able to successfully reinstall GRUB through the following method:

$ sudo su
$ mnt /dev/sdb /mnt/sdb
$ chroot /dev/sdb
$ grub-install --recheck /dev/sdb

Not sure if this information will happen to fall in the hands of anyone else in a similar situation to mine, but if so, I hope it helps.

Thanks again for the help, Herman.  I appreciate it!

hoby

---

### Post by Herman on 2007-09-19
[http://en.wikipedia.org/wiki/Methylated_spirit](http://en.wikipedia.org/wiki/Methylated_spirit) Ah, the good old Wikipedia, that's one of my favorite sources of information too. :) 
Thanks hobybuntu, denatured alcohol was the other name for methylated spirits that I was looking for. Next time I'll be able to explain that better, so everyone will be able to understand me. :)

I'm glad you got your GRUB fixed too. Well done on solving your problems!  Happy Ubuntuing!
Regards, Herman :)

---

