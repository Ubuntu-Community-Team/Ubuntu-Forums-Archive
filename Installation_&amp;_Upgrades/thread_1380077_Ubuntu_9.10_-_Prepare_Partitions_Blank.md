---
title: "Ubuntu 9.10 - Prepare Partitions Blank?"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by A4orce84 on 2010-01-13
When I try to install 9.10, the prepare partitions page is blank.

I have 2 physical HD's in my computer, one with Win 7, and I wanted to throw ubuntu on the other one.

I have been able to do this before, but every time I start the install for 9.10 and get to the prepare partitions screen its blank.

Any ideas?

The only options I can set from the time it starts to boot are as follows:

1. Language
2. Time Zone
3. Key Board

Then immediately to Prepare partitions -- which won't let me do anything.

Thanks.

---

### Post by A4orce84 on 2010-01-13
anyone?

---

### Post by darkod on 2010-01-13
First boot with the cd, Try Ubuntu option, and open Gparted. Take a look at the drives. If it shows only /dev/sda, /dev/sdb, that's fine, but if you see a device like /dev/mapper/blabla then you have a hdd with raid settings remains on it. 9.10 can pick them up and it creates the confusion.
If this is the case, open terminal and execute:

sudo dmraid -E -r /dev/sda (or /dev/sdb, depending)
sudo apt-get remove dmraid

That should sort it out for you. Reboot and select Install Ubuntu and it should be better.

If it's not the raid settings, I don't have an idea right now.

---

### Post by Sef on 2010-01-13
What file system are the blank partitions?

---

### Post by A4orce84 on 2010-01-13
I am not using a RAID, its just 2 SATA HD's hooked up in my machine. 

I'm at work right now, but basically my system is set up as:

First Physical HD:
C: ----> 300 gig HD all NTFS

Second Physical HD:
D: ---> 150 gigs all NTFS  (backup partition)

E: ---> 50 gigs all NTFS  


Drives D and E: are partitions but are the same physical drive.



I want to throw Ubuntu on Drive E:  (50 gigs) so I can dual boot and still have my backup partition. 


I've been able to load Ubuntu on to to this system before (Version 8.10) and it worked fine when I tried to install. 

I'm just not sure why its not picking up ANY of my HD's in the 9.10 install.


I'll have some more detailed answers in a few hours, but does anyone else have any ideas or experienced anything similar?

Thanks.

--Asif

---

### Post by darkod on 2010-01-13
> **A4orce84 said:**
> I am not using a RAID, its just 2 SATA HD's hooked up in my machine. 



I never said you were running raid, I just said there might be raid settings remains. Either from you or someone else using the drive before. I've seen people wondering how raid settings got on their drives.
I even saw a case where there was only one hdd in the machine (and no raid level works with one hdd) and the drive was not showing up in the installer, and this was exactly the problem. Doing the remove dmraid command solved it.

The other command is just to make sure all settings are gone.

The data on the drives should be safe while executing these commands but having a backup wouldn't hurt just in case.

I would suggest running the commands, and if it doesn't help, we'll see. Another way to check for raid remains is during the live session go into terminal and execute:
sudo blkid

Besides showing your UUID it will also show the names of the drives. If you see /dev/mapper/blabla, you know what your problem is. Check like this first.

---

### Post by darkod on 2010-01-13
PS. Just for reference.
[http://ubuntuforums.org/showthread.php?t=1324025&page=2](http://ubuntuforums.org/showthread.php?t=1324025&page=2)

---

### Post by A4orce84 on 2010-01-14
You were right on the money darkod!!!!!!!!!!!!

Thank you sir, now I have a new issue to battle with over my wireless card:

[http://ubuntuforums.org/showthread.php?p=8664491#post8664491](http://ubuntuforums.org/showthread.php?p=8664491#post8664491)


Thanks for your help!


--Asif

---

### Post by Fejker on 2010-08-17
I know this thread is old but OMG thank you darkod ... I was this close ->||<- to letting Ubuntu go and installing Win7 on my workstation because of this stupid dmraid thing. THANK YOU THANK YOU THANK YOU!

I had a similar problem with my laptop which has a hardware RAID setup and Ubuntu wasn't letting me create the partitions. I had to create the partitions from Windows using a 3rd party software.

The only installation of Lucid that went smoothly was the headless server.

---

