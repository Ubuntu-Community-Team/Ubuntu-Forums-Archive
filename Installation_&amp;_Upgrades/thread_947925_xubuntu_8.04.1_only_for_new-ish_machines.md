---
title: "xubuntu 8.04.1 only for new-ish machines?"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by inginear on 2008-10-14
hello all ):P  I am having a problem with installing hardy heron on an older machine, and I'm wondering if it is a bug with hardy.  The problem I am having is that hardy is not detecting my harddrive at all.

Machine specs. (all hardware is circa 2000-2002)
Motherboard: MSI KT3 Ultra
Processor: AMD Duron 1200 MHz
Memory: 512 Mb (random no name brand)
HDD: WD 120 Gb (IDE)
CD-Rom: Lite-On CD-RW (IDE)

The HDD jumper is set to master, and it is the only drive on the first IDE channel.  The CD-RW is set to master, and it is the only drive on the second IDE channel.  This test machine also does not have access to the internet.  For any internet activity I use my XP machine. (research, downloading, etc.)

In the past I have had Red Hat 7.2 and White Box Linux installed on this machine.  They both had their problems with installing regarding x and the network card.  However those problems were overcome with some reading and research around the web.

I checked the cd for defects and none were found.  The live cd of xubuntu boots up and seems to work fine, except for not detecting the hdd.  I have tried to install xubuntu from the cd boot menu and from inside the live session.  I have tried booting with "all_generic_ide" and "ide=nodma", but is still does not detect the hdd.  I have also tried the alternate xubuntu cd, but still no avail as far as detecting the hdd.  

I have also tried a few more distros with the following results: Debian 4.0 and Slackware 12.1 do detect the hdd with no problems.  Fedora 9 does not detect the hdd.

I have read somewhere that (x)ubuntu is based off of Debian, so I'm curious as to why Debian detects the hdd without any problems but xubuntu does not detect the hdd at all.

The machine currently has only White Box Linux installed.  I plan to make the machine into a quad Linux machine with Debian, Fedora, Slackware, and Xubuntu.  I am in the process of testing all the software compatibility with the machine before I decide on the exact partitioning scheme I am going to use.

Sorry for the long post, I figure the more information available, the greater chance of getting this problem solved sooner.



p.s. Great forums! I've learned a lot about Xubuntu in the last few weeks just by lurking and reading. :)

---

### Post by cariboo on 2008-10-14
When you say it does not detect your had drive, do you mean it does not automount, when using the LiveCD, or that the partiton utility does't detect a hard drive?

Jim

---

### Post by inginear on 2008-10-14
> **cariboo907 said:**
> When you say it does not detect your had drive, do you mean it does not automount, when using the LiveCD, or that the partiton utility does't detect a hard drive?

Jim

Both.  I have tried to mount the hard drive in the live session, but it could not find a hard drive connected.  And when I ran the installation wizard, it stopped at step four (4) with no devices listed in the partition box.

---

### Post by inginear on 2008-10-15
Anyone have any ideas as to how I can get Xubuntu installed?  I would really like to play around with an installed version instead of the live session.

---

### Post by adept_king on 2008-10-25
same here.  on my old ubuntu install, the drives just showed up in "places"  now, with ubuntu server, nothing mounts.  i installed xubuntu desktop over it and still nothing.  i had to install gparted just now, and gparted wont give me permission to mount any of my other drives or partition.

is there an autoconfig function for fstab?  why didnt the program that created fstab see those drives?  i tried adding them myself but to no avail.

--

i fixed it but as chance would have it, i dont remember how i got around the mount permission thing.  maybe from this...

**sudo mount /dev/sda2 /media**

i found the **uid** for the drives, sudied fstab a bit, now i can handle fstab.  **sudo nano /etc/fstab**  i dont know why they dont show up in my "places" menu, but its easy enough to go to /media by clicking on the "file system" icon.  theres a little weirdness in my sdcard reader (wont unmount from desktop) but who needs to look at sdcards on a server anyway?  im learning server, thats the only reason i slapped on xubuntu.

---

