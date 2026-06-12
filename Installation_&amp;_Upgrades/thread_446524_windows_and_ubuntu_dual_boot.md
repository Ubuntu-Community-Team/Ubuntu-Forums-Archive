---
title: "windows and ubuntu dual boot"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by venix on 2007-05-17
ok 1st i want to say i am compete newbie woth linux 
at the moment my pc got windows installed
i want to ask if i can install now ubuntu and keep the windows like they 
with choose menu at the boot 

ubuntu using ntfs file sistem or i will have to partytion my hd 1 partition for ububtu and 1 for windows ?

i just want to test ubuntu and see if cover me and remove forever the asdsadwqe windows :)

---

### Post by encompass on 2007-05-17
Linux runs off of the live cd and you can test many of the things there...
If you are ready to take the next step and install great...
Someone will have to confirm with me but you can shrink ntfs partitions and then put linux on the free space.  Or better, just put it on a seperate drive. like you were saying.
Good luck, it will be a great learning experience for you.

---

### Post by Wim Sturkenboom on 2007-05-17
You need to repartition. I suggest the following schema
partition for windows OS and programs
partition for windows data (you can configure windows to put its 'my documents' there)
partition for filesharing (FAT32) between the two OSes
partition for Ubuntu
partition for Ubuntu's /home (similar to 'documents and settings' in windows)
The sizes are up to you (can't really advice without knowing your disk size)

When you install Ubuntu, it will install a bootloader (GRUB) as well; during the installation it will automatically pickup the windows partition and add it to the boot menu

To testdrive Ubuntu, you can use the live CD (you need at least 256MB of RAM for that). I'm not really a supporter of liveCDs, mostly as I don't know how they work, and sometimes they give trouble with specific hardware.

If you don't have enough memory, you need to use the alternate CD for installation.

Last note: make a backup of all your important data before installing. There's always a chance that something goes wrong during the partitioning (power failure, you make a mistake, program crashes)

---

### Post by venix on 2007-05-17
my pc spec is athlon amd 64 3000+ slot 754
                                   1,5gb ram 400mhz fsb
                                   ati radeon x1650pro
                                  2xhd 40 gb ide and 200 gb sata
                                  my problem to make partition is mostly i have to backup 160 gb files :/ 
 i was thinking somethink like the 40 gb hd for windows theya re some games realy love like gothic 3
and the 200gb sata for linux

but with out changing the hd format and keeping my files

---

### Post by bulldog on 2007-05-17
> **venix said:**
> my pc spec is athlon amd 64 3000+ slot 754
                                   1,5gb ram 400mhz fsb
                                   ati radeon x1650pro
                                  2xhd 40 gb ide and 200 gb sata
                                  my problem to make partition is mostly i have to backup 160 gb files :/ 
 i was thinking somethink like the 40 gb hd for windows theya re some games realy love like gothic 3
and the 200gb sata for linux

but with out changing the hd format and keeping my files

You want to change nothing when you install ubuntu??:confused:

No go,you have to make space for a new OS and use another file system for it,simply as that.

---

### Post by Wim Sturkenboom on 2007-05-17
It sounds like your serious about Linux (200GB only for Linux).

How do you currently use the disks. If the second HD only contains data, I suggest that you move it to the SATA drive and install Linux in the second disk; while testing, you can keep it one partition (and a small swap partition). You can consider to make it two (one for the OS and one for /home (similar to 'documents and settings') and a small swap partition.

It also sounds like you're not concerned about your data as you're not willing to create backups. Not even related to the installation of a dual boot, what are you going to do when your HD just crashes for whatever reason?

---

### Post by venix on 2007-05-17
if my hd crush god may help me :P 
i am using the 200gb hd for storage videos music etc so i will not have problem to manage em from 
linux 40gb it's enougth for my games and windows since i am not playing more than 3 games every period time
looks like i have to buy 20-25 dvd to backup :/ boooring :P

btw i am not computer newbie i am linux newbie :P

---

