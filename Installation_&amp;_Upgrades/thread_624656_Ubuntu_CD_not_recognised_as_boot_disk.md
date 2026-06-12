---
title: "Ubuntu CD not recognised as boot disk?"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by sroberts on 2007-11-27
Hi All,

I am attempting to install linux on one of my older computers at home, in order to pass it on to a (computerless) friend as a Xmas present.  I chose to install use Ubuntu 7.10, and downloaded the CD iso.

However, when I attempt to boot off the CD, the CD simply doesn't work.  After the CD drive spinning for a few seconds, the two computers I have tried it on have simply moved on to booting off the hardrive.

I have verified the md5sum of the downloaded ISO,  and have burned the ISO onto two separate disks, each time using a separate burning program.  Both CD's have the same error.

Does anyone have any ideas what may have gone wrong?

Sam

---

### Post by taurus on 2007-11-27
Have you checked the BIOS to see if you have CDROM as the first boot device?

---

### Post by doowgof on 2007-11-27
I had this problem too. The solution is simple: just go to the booting menu (in my case I press F12 I guess), insert the CD (if the CD's already in the drive then leave it there), select "booting from CD" but do not push enter right now, give it some time to allow the drive "talk" to the CD, if you hear a smooth CD turning sound, press enter then. The system will be booted from CD then.
I did that just because my CD drive wouldn't recognise the CD fast enough, so just gave it some time. And it worked on my laptop.

---

### Post by sandysandy on 2007-11-27
> **sroberts said:**
> Hi All,

I am attempting to install linux on one of my older computers at home, in order to pass it on to a (computerless) friend as a Xmas present.  I chose to install use Ubuntu 7.10, and downloaded the CD iso.

However, when I attempt to boot off the CD, the CD simply doesn't work.  After the CD drive spinning for a few seconds, the two computers I have tried it on have simply moved on to booting off the hardrive.

I have verified the md5sum of the downloaded ISO,  and have burned the ISO onto two separate disks, each time using a separate burning program.  Both CD's have the same error.

Does anyone have any ideas what may have gone wrong?

Sam
hi

what are your system specs. How much RAM do you have. also what bit (32 / 64 bit) is your computer and what bit ISO have you downloaded.

regards

---

### Post by jespdj on 2007-11-27
Are you writing the ISO image to a CD the correct way?

If you are creating a data CD and you're just putting the ISO file on a data CD, then it will not work. You need to use CD writing software that knows how to write an image to a CD.

See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by sroberts on 2007-11-27
Thanks for the suggestions everyone,

I have verified the booting sequence, and I downloaded the x86 desktop ISO, which I think is correct for my computer (Intel 32 bit processor.  1 Gig of RAM, btw).

I am pretty sure that both CD's were created correctly, but the second time I created the boot CD I followed the sequence (and used the programs) suggested in your guide to burning CD's, just to make sure.

I will try doowgf's suggestion soon, and let you know how it goes.

Many thanks,
Sam

---

### Post by sroberts on 2007-11-27
Hi everyone,

The computer I am trying to put Ubuntu on only lets you choose a boot device using the boot sequence, it doesn't let you directly select a device (as far as I can tell).  I disabled everything except the CD drive to see if that made a difference, but the computer simply insists that the CD is not a boot CD, and asks me to insert a boot CD.  My windows XP cd works fine, btw.

My laptop does let me directly choose a boot device, but even when I waited for the computer to recognize the CD before selecting the CD drive, the computer still booted off the hard-drive.

I am at a loss ... 

Maybe I should try a different ISO?  Any suggestions?  A different version of Ubuntu perhaps?

Any suggestions appreciated,
Sam

---

### Post by sandysandy on 2007-12-01
make sure that in the [COLOR="Blue"]BIOS the booting sequence is set to CD[/COLOR] first followed by hard disk. u have mentioned that u have disabled everything in booting sequence other than CD. if the computer is booting from hard disk, then the hard disk must be in booting sequence. please check.

Secondly if u r able to boot with windows XP CD, u must check again whether the Ubuntu CD is burned correctly.

regards

---

### Post by Pumalite on 2007-12-01
Clean the lens in your burner, try the CDs in a different computer.

---

