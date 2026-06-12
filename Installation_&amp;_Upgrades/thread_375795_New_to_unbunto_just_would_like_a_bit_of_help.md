---
title: "New to unbunto just would like a bit of help"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by lttmik on 2007-03-04
I hit the start or install and it goes and brings uip the unbunto symbol and a bar that loads but after that i get a blinking line in the top left corner for a couple of seconds and then nothing I just would like a step by step directions on how to install this onto my computer I am using a blank HD.

---

### Post by xyz on 2007-03-04
Hi and Welome,
Are you trying to install Edgy or Dapper? How did you get it? Download, ship it...?
Did you check md5sum (cd integrity check).
Thnx for providing all infos you can provide.

---

### Post by lttmik on 2007-03-04
i downloaded unbunto live cd from unbunto.

---

### Post by frogotronic on 2007-03-04
> **lttmik said:**
> I hit the start or install and it goes and brings uip the unbunto symbol and a bar that loads but after that i get a blinking line in the top left corner for a couple of seconds and then nothing I just would like a step by step directions on how to install this onto my computer I am using a blank HD.

Welcome!

Which version are you trying to install?  Edgy Eft (6.10) or Dapper Drake (6.06)?

[BTW:  The Ubuntu numbering system is YEAR:MONTH; thus Edgy Eft was realeased in 2006, in October.  Fiesty Fawn will be released in April of 2007, and will have the numerical designation 7.04]

Are you using the "LIVE CD" or the "Altertnate CD"?

Is this a NEW blank HDD, from a package that has never been used in any computer system (if so, tell use which brand); or a drive that had M$ Windows and was subsequently erased?

- CH

---

### Post by lttmik on 2007-03-04
its version 6.10 and yes this HD had a version of windows that i erased not new.

---

### Post by lttmik on 2007-03-04
cd integrity fine

---

### Post by xyz on 2007-03-04
> **lttmik said:**
> its version 6.10 and yes this HD had a version of windows that i erased not new.
How did you erase it? I hope you can boot from CD-ROM. Normally you should be able to if it's a new computer. What brand is it?

---

### Post by lttmik on 2007-03-04
i built the computer myself just never dabbled with linux before its running:

athlon 3000:
512mb ram
ati 9800 pro 256
160gig seagate

any idea why it just stops after the blinking line? I can write while the blinking line is there btw.

---

### Post by lttmik on 2007-03-04
I still can't get this to work anyone know something im doing wrong should i be formatign the HD first and if so how do i do it?

---

### Post by xyz on 2007-03-04
If I understood you correctly, you no longer have a working OS since you erased Windows? Am I right?

---

### Post by xyz on 2007-03-04
You could download [GParted]("http://gparted.sourceforge.net/") burn the .iso and boot from it.

---

### Post by frogotronic on 2007-03-04
> **xyz said:**
> You could download [GParted]("http://gparted.sourceforge.net/") burn the .iso and boot from it.

Hello,

Yes, that would be my suggestion as well.  GParted LIVE CD is an excellent tool.  The Ubuntu EE installer also uses this, but it can be problematic.

Some points to consider:

1) Seagate has a low level format tool called DiscWizard(?) that will prep a drive - might be good idea to so that first.

2) Format the drive using the GParted LIVE CD for Ubuntu.

Then try your Ubuntu Live Installer CD.

Let us know
- CH

---

### Post by lttmik on 2007-03-04
I have done as u asked and its working (the gparted live cd) but it asked me to select a number i did the first one aserky but there were a bunch should i have picked a different one?

---

### Post by lttmik on 2007-03-04
am i supposed to load unbunto while using the other bootable or am i supposed to load unbunto as the boot after i format it.

---

### Post by frogotronic on 2007-03-04
> **lttmik said:**
> I have done as u asked and its working (the gparted live cd) but it asked me to select a number i did the first one aserky but there were a bunch should i have picked a different one?


What is 'aserky' ?  The video resolution?  You should choose "VESA" if you are unsure.

The file system that you should format the drive as should be "Extended 3", or ex3.

- CH

---

### Post by lttmik on 2007-03-04
I formated the drive in that ext3 format Ive loaded unbunto again and it does the same thing i click on the one that says install unbunto and it shows the load screen but it just shows the logo and then under that the bar that loads but nothing else is on the screen then it goes to a black screen with a flashing line in the corner and then it goes blank and thats it i have to do a hard boot. any ideas?

---

### Post by lttmik on 2007-03-04
is there a full download of unbunto not the live cd that would maybe do what i want? if so can someone send me the link i couldn't find it

---

### Post by frogotronic on 2007-03-04
> **lttmik said:**
> is there a full download of unbunto not the live cd that would maybe do what i want? if so can someone send me the link i couldn't find it

Yep, okay.  What you are experiencing is NOT usual.  Sometimes the LIVE CD won't work on certain machines.  Use the "Alternate CD" and install from that.

[http://ftp-mirror.internap.com/pub/ubuntu-releases/edgy/](http://ftp-mirror.internap.com/pub/ubuntu-releases/edgy/)

---

### Post by frogotronic on 2007-03-04
> **lttmik said:**
> is there a full download of unbunto not the live cd that would maybe do what i want? if so can someone send me the link i couldn't find it

Yep, okay.  What you are experiencing is NOT unusual.  Sometimes the LIVE CD won't work on certain machines.  Use the "Alternate CD" and install from that.

[http://ftp-mirror.internap.com/pub/ubuntu-releases/edgy/](http://ftp-mirror.internap.com/pub/ubuntu-releases/edgy/)

---

### Post by karachuonyo on 2007-03-04
I would also urge you to download the alternate cd and boot with it. Specify install in text mode and in disc partition ask to use the whole disc ( since you have already erases windows) then you can have the installer automatically setup the partitions( /, /home and swap area) or if feeling quite adventurers you can opt to setup the partitions manually. P.S. Do check the cd integrity when you first boot up and make sure it passes before installing. Welcome.

---

### Post by lttmik on 2007-03-04
it still does the same thing except now i did get it to install on the HD so im running it from there but it still gives me a screen that has the symbol and a load bar under it after its done it goes away and nothing else happens my screen stays black is this a video card problem i saw some stuff in here about that what do i hve to do to fix it?

---

### Post by lttmik on 2007-03-04
anyone help me?

---

### Post by xyz on 2007-03-05
Try and give [this]("http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=1410&view=previous") a try. Hope it works for you.

---

