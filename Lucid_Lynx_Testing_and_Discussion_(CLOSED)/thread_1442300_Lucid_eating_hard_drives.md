---
title: "Lucid eating hard drives:"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kuvanito on 2010-03-29
i have installed lucid on about 3 pcs by now and it had twice screwed the hard drives to no fix available,both IDEs. any one seen this problems?

i tried repairing the HDs and could not,had to replace them both.

installing Lucid behaves different from pc to pc,it's kind of weird,it never happened when I was trying Jaunty.
Jaunty behaves a lot different.

I am doing clean installs,erasing and using the entire hd.hate to lose more hds.

---

### Post by VMC on 2010-03-29
> **kuvanito said:**
> i have installed lucid on about 3 pcs by now and it had twice screwed the hard drives to no fix available,both IDEs. any one seen this problems?

i tried repairing the HDs and could not,had to replace them both.

installing Lucid behaves different from pc to pc,it's kind of weird,it never happened when I was trying Jaunty.
Jaunty behaves a lot different.

I am doing clean installs,erasing and using the entire hd.hate to lose more hds.

How did you try to repair them? Try using *testdisk*.

---

### Post by emarkay on 2010-03-29
What do you mean "screwed with"?  What is the actual problem - error message - fail mode?

What makes you think it's a Lucid issue; instead of a hardware issue, for example?

---

### Post by psyke83 on 2010-03-29
> **kuvanito said:**
> i have installed lucid on about 3 pcs by now and it had twice screwed the hard drives to no fix available,both IDEs. any one seen this problems?

i tried repairing the HDs and could not,had to replace them both.

installing Lucid behaves different from pc to pc,it's kind of weird,it never happened when I was trying Jaunty.
Jaunty behaves a lot different.

I am doing clean installs,erasing and using the entire hd.hate to lose more hds.

Assuming that Lucid really is causing this problem (and you're not misinterpreting this with an unrelated installation issue in Lucid), it seems more likely to be a problem with the IDE controller driver rather than with individual drives.

Also, please define "screwed"...

---

### Post by ronacc on 2010-03-29
also try a standalone gparted disk   [http://downloads.sourceforge.net/gparted/gparted-live-0.3.9-13.iso ](http://downloads.sourceforge.net/gparted/gparted-live-0.3.9-13.iso )

---

### Post by Jerry N on 2010-03-29
I had the same problem the first time I tried to install Lucid (alpha 3), also with an IDE drive (40gb).  Gparted would neither delete the faulty partition nor allow a new partition to be created.  The WD diagnostics and Spinrite thought the disk was OK.  I had to use a DOS boot disk to clean off the partitions and format a new partition.  I then installed Win98 on the drive just to make sure the drive still worked.  I haven't tried another Ubuntu install on that drive yet but I am convinced that Lucid somehow screwed up the drive.  A later install of Lucid beta 1 on a different drive (same computer) went OK but then Lucid deteriorated from fabulous to unuseable after several days of updates.

Jerry

---

### Post by ronacc on 2010-03-29
try setting up and formating the partitions using the standalone gparted I linked to above , then select manual when the installer gets to the partitioning section and manualy assign / and /home ( or however you setup your drive) , then DO NOT FORMAT . it may bitch about not formating but it will install ok . The built in partitioner sometimes don't get things right .

---

### Post by ezsit on 2010-03-30
> The built in partitioner sometimes don't get things right .

What? During beta testing, some parts don't work quite right? That's just spooky! That's why I haven't upgraded since getting a perfect Intrpeid install and configured just so. I'll wait til 10.04 is released, maybe even until July when they pump out 10.04.1 and then upgrade. I don't like fixing borked systems, I need mine to work and never give me any shiiit.

---

### Post by emarkay on 2010-03-30
If you are Beta Testing, you should never presume it's perfect - assume it's completely flawed, then smile when it works!

Yes, in thin case I recall some installer issues that affected partitions - I always use Gparted first anyway, but in Beta, it's essential.  

Also, be prepared to reformat, frequently as that is the only way to know you are testing a "Clean" install at the most basic level.

---

