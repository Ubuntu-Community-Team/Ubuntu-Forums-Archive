---
title: "quick question"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by jewishbob on 2006-02-28
will this wipe my harddrive when i install...

---

### Post by frodon on 2006-02-28
Which harddrive (datas or your OS hdd) ?
What are you trying to do, an install, an upgrade, from warty, hoary ?
Could you provide more details ?

---

### Post by jewishbob on 2006-02-28
basically im running windows XP pro and i want to switch to linux...and i wanted to reformat along with the switch (no partitions)

i downloaded the PC install CD for breezy last night and i tried 3 different ways of running the cd and it wouldnt install...
1.when it was done burning it went straight to nero and burned
2.i mounted the ISO file to a ghost drive with Alcohol120%
3.burned it again with the windows burning wizard

should i order a CD from the company...?

---

### Post by frodon on 2006-02-28
When you burn the CD, take care to burn the CD with the "burn an image file" option it's needed to make the cd bootable.
Also to boot on the CD you may need to enter in the BIOS to set your computer to check cdrom for boot first.
You will find a lot of useful informations here : [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Bartender on 2006-02-28
jbob -
At least you don't write on and on for too long like me :-D 

What happened after those 3 different attempts to make an install CD?  

Did you put it in the tray, and it started to spin up, but then nothing?
Or did it start to install, then hang at some specific stage?
Or did each CD hang at a different stage?
Or did you forget about going into your BIOS and asking the PC to boot from the CD device?

More specifics, please...

---

### Post by LordBug on 2006-02-28
> will this wipe my harddrive when i install...
> basically im running windows XP pro and i want to switch to linux...and i wanted to reformat along with the switch (no partitions)
Little confusion here.  If you truly want to blow away your HD and start fresh, you very easily can with the Ubuntu install CD.  It sounds like you want this?

If you're trying to keep XP and dual-boot Ubuntu, you can do this.  It just takes more prep work, as you'll need to re-configure your partitions somehow before you install Ubuntu.

---

### Post by trorion on 2006-02-28
Forget all that cd burner program stuff.  Windows actually has a fully functional CD Burner that is fast, clean and works with .img, .iso, etc files.  They just don't tell anyone about it so you end up spending boatloads on lousy software that has bad programming

Download this:
[http://www.microsoft.com/downloads/details.aspx?familyid=9d467a69-57ff-4ae7-96ee-b18c4790cffd&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=9d467a69-57ff-4ae7-96ee-b18c4790cffd&displaylang=en)
from microsoft.  Install it and reboot.

save the ISO to C:\
START -> RUN ->"Command"
type:
```
cdburn [cd_drive_letter]: c:\[iso_name].iso
```
Everything in between [] is something you enter in (for example if your CD burner is drive d: and your image is 'c:\ubuntu.iso': cdburn d: c:\ubuntu.iso


That will burn the CD for you in the proper format.

---

