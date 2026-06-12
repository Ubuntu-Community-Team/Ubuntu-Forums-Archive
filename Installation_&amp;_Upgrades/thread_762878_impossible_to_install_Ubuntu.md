---
title: "impossible to install Ubuntu"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by king-greg on 2008-04-22
hello
i cant install ubuntu
i tried every version,7 and 8
every time it stop at the beginning , the progress bar stopp

i tried alternate
the install goes well but after booting the pc freeze at the progresse bar:

[[img]http://pix.nofrag.com/4/b/1/d1018cbc2f30de852cb6d7c98eb38t.jpg[/img]](http://pix.nofrag.com/4/b/1/d1018cbc2f30de852cb6d7c98eb38.html)

i do ctrl alt supp, it go on again and crash:

[[img]http://pix.nofrag.com/8/c/9/98af48ae1f191f6c91b52b180527bt.jpg[/img]](http://pix.nofrag.com/8/c/9/98af48ae1f191f6c91b52b180527b.html)

???? idea???

I ve got :

Athlon X2 64 bit 4400
2 Go RAM
GeForce 7600GT
DVBT tuner card DTV 2000H
chipset nvidia n force 4
Sound AC97
LCD display soundgraph IMon VFD

---

### Post by sandysandy on 2008-04-22
u may like to give the Ubuntu alternate CD a try.

regards

---

### Post by Cresho on 2008-04-22
look for hardy heron  alpha6. 5  or 4.  If you have an nvidia 8800gt, install that first.  then upgrade and when you boot up, do not boot up into the new kernel( you can try it because they are patching it up).  I was running the older kernels because of this as well and thank goodness I have a alpha version which I can boot into.  The new cd's wont be out anytime soon or maybee when the official hardy heron gets released.  As of this writting, the kernels are patched and i can use the new kernels.  But the official cd Isnt out yet.

---

### Post by Wazoot on 2008-04-22
If all else fails, you can always try Wubi and have Ubuntu installed like a windows application. With this you dont have to worry about partitioning, or anything else like that. It just installs Ubuntu under a folder on your hard drive, and puts it in the boot menu for when you restart your computer. Pretty much the only thing bad with Wubi is that it is slower than a standard Ubuntu install..but i can't tell, and neither can CPU magazine =]

---

### Post by samcompton on 2008-04-23
Any word on this?  I have the same issue on one of my computers.  I couldn't even install except with the alternate install CD.  Installed successfully and now it hangs on boot exactly where yours does.  I tried booting in verbose mode and see some errors regarding fd0 and irq 7.  Let me know if you figured out a fix.

---

### Post by king-greg on 2008-04-24
when i boot in recovery mode it appears to freeze at my TV card init, well i cant do anything...

it seems i m going to keep vista....

---

### Post by Tatty on 2008-04-24
What is a kernel panic:  [http://www.thexlab.com/faqs/kernelpanics.html](http://www.thexlab.com/faqs/kernelpanics.html)

Basically it means that the kernel recieved some instructions that it didnt like - possibly because of a bug, but more likely because the data got corrupted somewhere along the line, either due to data corruption or hardware failure.

It could be that the CD did not burn correctly - although since you have tried several CDs this seems unlikely.  Perhaps try one more time, but first check the [md5 hash]("https://help.ubuntu.com/community/HowToMD5SUM") of the .iso - then burn the CD really slowly (4x or less).  Finally use the "check cd integrity" option when loading the ubuntu CD.  

If all that is fine then it suggests a possible hardware problem.  The most likely problem will be damaged RAM - try replacing it if you have any spare sticks about (or can borrow some).  After that its probably best to just start following the list on the link at the top of this post.

**EDIT:** sorry i just re-read your main post - are you saying that you have actually installed ubuntu, but it wont boot up off the hard drive? if so then obviously forget what i said about the CD

---

### Post by samcompton on 2008-04-25
I started again with the Final release yesterday.  Problem gone.  Everything booted and installed as it should.

---

### Post by king-greg on 2008-04-30
Well i tried with the final release of 8.04
i removed my tv card,
remove my vfd front view
remove my sound card
remove every usb periphals

and... it crash after installation of alternate
i give up

---

