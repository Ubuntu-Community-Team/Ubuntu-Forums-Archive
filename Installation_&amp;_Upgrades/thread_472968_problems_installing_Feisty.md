---
title: "problems installing Feisty"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by DoctorDruid on 2007-06-13
I've been using Ubuntu 7.04 for a couple of weeks now from the live CD and am really enjoying it, however when I finally decided to take the plunge and install it on my system I have had a problem.

At step 4 of 7 in the installation procedure I selected "guided" for resizing the partition and decided to keep it fairly low at 42% or 54.6GB of my 160GB HD, it of course said partition resizing may take a long time but it got kind of ridiculous when it was still sitting at 0% after 6 HOURS!!

I decided to cancel the operation, restart my machine and try again but gave up after another 3 HOURS and still 0%

I have a reasonably fast machine with a pentium 4 (3.02GHz) and 2GB DDR2 so it should not have taken that long to complete the WHOLE process never mind still sit at 0%

I really do want to give linux, in particularly Ubuntu a serious go but this is kind of off putting, I could have installed about 8 Microsoft operating systems in that time.

---

### Post by merlinus on 2007-06-13
Here are a few suggestions:

Defrag your windows partition several times beforehand.  (I am assuming you wish to create a dual-boot system???}

This may be hanging up the process.

You can also use gparted live cd to do the partitioning first, and then install into the ones you have created.  I recommend three, /home, / and /swap.

Swap should be about 1.5 times your RAM, and the others can be split up equally.

gparted is available at:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by RichPicker on 2007-06-13
I had the same problem trying to install Edgy via partition. I gave up and wiped the disk.

---

### Post by DoctorDruid on 2007-06-13
I keep my drives fully defragged at all times and always clear unecessary clutter before every shut down, but I will give the app you metioned a try.

Thanks

---

### Post by Pumalite on 2007-06-13
> **DoctorDruid said:**
> I keep my drives fully defragged at all times and always clear unecessary clutter before every shut down, but I will give the app you metioned a try.

Thanks

Make sure you erase all temp files too.

---

### Post by DoctorDruid on 2007-06-13
I think I will just stick to using the Live CD from now on...if I even continue to want to use Ubuntu any more.

I downloaded the gparted live cd as suggested and ran it from boot BUT MADE ABSOLUTELY NO CHANGES TO MY SYSTEM since I wan't too sure what to do, and when I went to re-boot Vista in order to go online and find documentation on the use of gparted I couldn't get my machine to boot back up

I had to run the inbuilt system start up repair due to major problems.

It almost Screwed my machine up and that was, as I said, WITHOUT HAVING MADE ANY CHANGES TO ANYTHING!!

Pfft!!!

---

### Post by DoctorDruid on 2007-06-13
> **Pumalite said:**
> Make sure you erase all temp files too.


oh and when I said I clear all unecessary clutter, I meant things like temp files!!!

I may be a noob to Linux, but I aint a dummy!!

---

### Post by Gremlinzzz on 2007-06-13
Try making a small partition say 20gb or 10 then delete it.this makes it free space.then when asked  choose use  largest contineus free space.works every time.:D

---

### Post by Gremlinzzz on 2007-06-13
If your using vista you dont need gpart.hit start just right click on computer choose manage. then click Disk Management.then right click on C; window and choose shink volume.this will make a partiton you choose what size. after' right click on the partition you created and delete it making it free space.

---

### Post by merlinus on 2007-06-13
FWIW, if you had originally said you were trying to dual-boot with vista, this would have been a much shorter and more useful process.

vista has its own disk manager, since it uses a dynamic partition, and tries its best to not co-exist with anything that does not come from redmond.

-merlin

---

### Post by Gremlinzzz on 2007-06-13
:DI dual boot with vista so far i tried 3 differrant linux systems .had no problems installing.:Dstaying with the ubuntu =vista dual boot.

---

### Post by merlinus on 2007-06-13
It would seem that most of the problems with vista are due to folks not using its disk manager to shrink the partition before installing.

gparted does not seem to work for this.

-merlin

---

