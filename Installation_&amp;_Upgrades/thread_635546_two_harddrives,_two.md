---
title: "two harddrives, two"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by udyrfrykte on 2007-12-08
I want two use ubuntu for my everyday computing, but I also want to keep windows for the sole purpose of gaming. Right now I have two 80Gb Hard Drives

Hard Drive A: 
holds all  current files
currently has windows installed
will have windows xp OS for gaming

HardDrive B:
soon to be clean-formatted
will have ubuntu OS


Now, my problem, I want to first install ubuntu on HD B, and then transfer all my files from HD A, onto HD B.
after that I would format format HD A, and install a fresh copy of windows xp. 

 I want both HardDrives in my computer at once, and at bootup have the option from booting from either. Can anybody help me do this?

// oh and sorry about the incomplete thread title

---

### Post by technoidiot on 2007-12-08
From hard experience. back up all your files from your XP drives. Reformat and reinstall that drive first. then install Ubuntu on the second drive. By doing it this way your grub loader will read properly and you will have a choice of which drive you boot into. I have tried other ways and had nothing but problems. 

I am currently running three drives each with a different OS

---

### Post by fain on 2007-12-08
You can install Ubuntu first and backup all your files then install xp but xp will over write your boot record and you will need to restore it with super grub boot disk which isn't too hard. theres plenty of how-tos on how to do this. In fact I'm about to do it very soon because i am not re installing my server just for xp..

---

### Post by udyrfrykte on 2007-12-09
ok just to make sure I understand you,
1: install ubuntu on my second HD
2: copy my files from my current hard drive to the one with ubuntu
3: then clean install xp onto the first harddrive?

How do I transfer all my files to the ubuntu harddrive? 
Is it a simple drag and drop, or will it require software, or do I have to write it all to cds?

If I do have to write all my data to cds i'll take tech's advice and format the xp drive first.

also is there a built in program for formatting a harddrive that is installed as a slave in ubuntu? I'm going to be a first time user, so i'm just making sure i'm not going to be running into any problems during the install.

---

### Post by fain on 2007-12-09
no theres no xtra software. the Ubuntu installer should recognize the ntfs/fat partitions and mount them in a specified location. Then you just drag and drop yes. or you can use the cp command.

techs way is the easiest. but you need to backup that data before you format the drive.

i would suggest to make a temp NTFS or FAT partition on the drive_b copy the files you want to keep  there and after the format and windows install copy it back to drive_a. then install Linux on drive_b

the program for formatting drives is called "mkfs" short for make file system.

edit: or you can write the data to cds :) this would be the safest way. then no matter what you do you wont lose it.

---

### Post by udyrfrykte on 2007-12-09
With this kind of thing, i'm all for safety, so i'll just write it all to cds. I have some extras laying around anyway. 
Thanks for the help, I'll start this project after exams in two weeks.

:)

---

### Post by udyrfrykte on 2007-12-16
When I get both harddrives ready to go, do I need to install one as a slave? I'm assuming that I'd leave them both without any jumpers right?

---

### Post by fain on 2007-12-17
No, you want to check the drives for a diagram on the jumpers and mark one as master and one as slave or cable select. I think I've come across a few drives that the cable select configuration is no jumpers at all. But I always mark each drive (master/slave) so i know which is which.

---

