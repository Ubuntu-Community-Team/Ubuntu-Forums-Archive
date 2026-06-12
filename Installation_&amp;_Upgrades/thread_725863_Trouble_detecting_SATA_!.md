---
title: "Trouble detecting SATA !"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by mono.maryam on 2008-03-16
Hi, I've got a new PC, but I've problem installing Ubuntu :((

AMD Athlon(tm) x64 X2 Dual Core Processor 5600+
Mainboard: MSI K9 Neo V3 
RAM : 2GB Geil
HDD : Maxtor 250 Sata II  (STM3250310AS)

At first, my HDD was connected to the SATA2 port. I could boot to the live CD, but the installation was unsuccessful. The partitioner (phase 5) could not detect any HDDs, in about 30 minutes !
I tried "sudo fdisk -lu" but no result ! GParted could not find any hard drive either !

I read about connecting the hard drive to the SATA1 port somewhere in the forum, did it, but now I can not even boot to the live CD !!!
now It fails in PCMCIA services ! and some kind of errors appear in the screen :
ata1 : translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 03/1/104
buffer I/O error device dm=0 , logical block .....

I do really need help :( :confused:

---

### Post by Pumalite on 2008-03-16
How many SATA ports do you have? Have you tried the other ports?

---

### Post by mono.maryam on 2008-03-17
I have 4 ports for sata, I tried the first 2 !!!! I doubt if trying the two left will help !
In the first port, I get the black page errors when the RAID option of my mainboard is set to IDE. And when it's configured in AHCI, I can boot to the live CD, but the Gnome Partitioner can not detect my HDD ! 
PLEASE HELP !!!!

---

### Post by Pumalite on 2008-03-17
Try the last 2 ports.

---

### Post by PmDematagoda on 2008-03-17
Did you verify if the BIOS detected the hard drives at all?

---

### Post by mono.maryam on 2008-03-18
BIOS does detect it !
I'm running a Win XP on it !

---

### Post by Pumalite on 2008-03-18
Before going after cables and connections; get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. See what it sees.

---

