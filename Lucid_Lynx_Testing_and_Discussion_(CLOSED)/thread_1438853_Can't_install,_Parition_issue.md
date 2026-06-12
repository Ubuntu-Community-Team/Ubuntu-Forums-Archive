---
title: "Can't install, Parition issue?"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dubstin on 2010-03-25
Ok I made my iso burnt it to a disc, and I'm typing this from the demo mode.

Computer specs:

2.4ghz sis-645dx
2gb ram
80gb hdd
Ati 7000 64mb
Windows XP sp3

I'm trying to install Ubuntu and remove XP completely, the disc I have burned is Ubuntu 10.4

Ok heres the problem, when I get to the fourth step of installation (4 of 7) It shows me a list where I believe
partitions should be popping up, but the list is completely empty, and If I click next I get an error message:

"No root file system is defined, Please correct this from the partitioning menu"

I've went to the partitioning menu (i think Gparted is it) but It wont let me do anything with my Hd because it says its mounted.

I've tried formatting and unmounting, it won't let me unmount because it says the drive is in use, and I cant format it because it's mounted....

Is this a common problem?

---

### Post by 2hot6ft2 on 2010-03-25
In GParted right click and select unmount.
Your installation issues are probably already answered in this forum
[Lucid Lynx Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=377")
since you're trying to install a Beta of Lucid and that's where the beta testing and discussion is.

---

### Post by Dubstin on 2010-03-25
Thank you, But as I said i've tried unmounting it, it just gives me an error saying the drive is in use.

---

### Post by lindsay7 on 2010-03-25
One thing you can do to make sure that all the partitions are unmounted so that you can work on them is to download and burn Gparted from their web site. It will be an iso file and will start up your computer when it is in the cd/dvd rom drive when you start the computer.

---

### Post by Dubstin on 2010-03-26
Thanks I can try that tomorrow when I go buy some more blank cds.

When I click on:
"Disk utility" then "File System" for my 80gb hard drive it says it is mounted to /cdrom
But when I try to install it on other machines I have the hard drive is mounted to nothing at all.
This is getting to be annoying are there any other possible solutions?

---

### Post by Mark Phelps on 2010-03-27
You're trying to install a Beta version of an OS. Wasn't that already made clear to you?  Unless you're a seasoned, experienced Ubuntu user, you have no business messing around with Beta versions of the OS.

AND, you were told the correct forum in which to ask your beta-related questions.  Was that unclear too?

I'm asking the Mods to move this thread to the proper forum.  Look for any responses there.

---

### Post by jpeddicord on 2010-03-27
*Thread moved to **Lucid Lynx Testing and Discussion**.*

---

### Post by psusi on 2010-03-28
You should not need to mess with gparted at all, just choose "use the whole disk" when prompted in the installer.

---

