---
title: "Ubunto not going into second phase of installation"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by maverickdelta on 2005-11-13
I am very new at any Linux installing scheme, but am otherwise quite experienced in computers.

Okay, so I currently have WIN XP installed on my computer.  I bought an 80GB HD and hooked it up.  I started my computer and checked through Win XP that my drive was working properly.

Here is my setup:
Disk 0 (WD 80GB HD):  G: H: I: J:
Disk 1 (Seagate 80GB HD): C: D: (WIN XP installed in C: )
Disk 2 (Seagate 80GB HD): "newly acquired"

I restarted with a Ubuntu CD inserted and went through the standard (not server) installation scheme.  My intention was to install Ubuntu into my new drive.  At the partition manager, I chosed something along the line of "Erase disk..." making sure it refered to the new hard disk.  I did not choose the one with the LVM, or whatever it is called...  It automatically created one big disk and one small swap volume.

I continued on with the installation.  The software detected WIN XP and asked if I wanted to install the GRUB, which I did.  After some processing, it ejected the CD, asked me to clear all drives (floppy and CD) for rebooting.  After doing so, it rebooted.  But it seems that my computer did not see any Ubuntu installation and worked its way into WIN XP again, as if nothing happened.  Chekcing my disks showed that my new drive has been partitioned, but no drive letters have been assigned to them.

After reinstalling it three times, I though that I should go into my BIOS and use my new drive as the new booting hard drive.  I expected that Ubuntu would allow me to choose my OS from my new drive.  But that caused my computer to hang (as in "did not detect any boot drive" hanging...).

Seeing that most booting problem consists of WIN XP not booting anymore, I am quite surprised of my situation, that WIN XP ALWAYS booting without giving me a choice.

I MUST be doing something wrong, but I do not know what.  Need assistance here!
:confused:

---

### Post by kakashi on 2005-11-13
i think i know what your issue is. it is probably some setting in your bios. 
like you have staed.
try unplugging all your hdds except the ubuntu one.
then try to install. ubuintu.

---

### Post by maverickdelta on 2005-11-13
Okay.  I'm getting... somewhere.

I did what you suggested and disconnected all hard drives except the new one.

I installed Ubuntu and it went all the way through and loaded fine, desktop and all.

So I shut down the computer and reconnect all my hardrives again.  When I tried to boot-up into my new drive, it displayed an error message telling me I could not boot with the new drive.  I think it mentioned some file(s)s was(were) missing.  Sorry, did not write down those messages.

So I kept my BIOS configuration to boot up from my new drive, while maintaining connections to all my other drives.  Again, I went through Ubuntu Installation and rebooted for the second phase of the installation.

This time things are different.  GRUB loaded, but notified me that the hard disk Ubuntu was on no longer exists.  Now I had the choice of loading 3 different configuration of Ubuntu, all of which failed with an identical message stating that my drive does not exists, and Win XP.  At the end, I selected Win XP, went on the net and am writting this message.

Strange thing, I think, is if my new drive does not exist, were the heck is GRUB loading from?

I seem to be the only one that does not have Ubuntu loading, but Win XP always is...

I really need help!

---

### Post by kakashi on 2005-11-13
[QUOTE=maverickdelta]Okay.  I'm getting... somewhere.

I did what you suggested and disconnected all hard drives except the new one.

I installed Ubuntu and it went all the way through and loaded fine, desktop and all.

So I shut down the computer and reconnect all my hardrives again.  When I tried to boot-up into my new drive, it displayed an error message telling me I could not boot with the new drive.  I think it mentioned some file(s)s was(were) missing.  Sorry, did not write down those messages.

So I kept my BIOS configuration to boot up from my new drive, while maintaining connections to all my other drives.  Again, I went through Ubuntu Installation and rebooted for the second phase of the installation.

This time things are different.  GRUB loaded, but notified me that the hard disk Ubuntu was on no longer exists.  Now I had the choice of loading 3 different configuration of Ubuntu, all of which failed with an identical message stating that my drive does not exists, and Win XP.  At the end, I selected Win XP, went on the net and am writting this message.

Strange thing, I think, is if my new drive does not exist, were the heck is GRUB loading from?

I seem to be the only one that does not have Ubuntu loading, but Win XP always is...

I really need help![/QUOTE]
man your case is confusing. try this. 
maybe the fact that some of your hdd are secondary is the problem.
make your ubuntu hdd the primary master. (jumper setting on the primary master cable.
then reinstall ubuntu.
btw props for the effort to install ubuntu. i know i never will have enough patiance to do what your doing.
even though on my first try i did reinstall ubuntu 5 times ( total linux noob back then).
 i can assure you that once ubuntu is up and running you'll find that it was worth every drop of sffort and more.

p

---

### Post by maverickdelta on 2005-11-15
Installation attempts were delayed because I ran into the "CD not mounted" error.

After flash updating my BIOS, I still run into the same booting problems...

But I realised something.  When installing GRUB, the software says it is instaling on "hd0".  What is hd0?

If it is installing on my data drive (if I assume hd0 is DISK 0), then it is NOT loading it on the right disk!!  There is not WIN XP on that disk.  WIN XP is on  disk 1.  I want to have it installed on Disk 1 or Disk 2 (according to the scheme of the partition manager that comes with Ubuntu).

So here is my problem.  Assuming that my assumption about "hd0" is correct, how do I make one of my hardrives become "hd0"?  In my BIOS, my primary IDE master is my data hard disk (G: H: I: and J: ).  I have no secondary IDE master.

My third and fourth IDE masters are my SATA hard disks.  They are identical, and one of them is new.

Help?

-----------

UPDATE:

I retried installing Ubuntu with onlu one drive connected, the new SATA one.  Everything worked fine.  I rebooted several times just to make sure the loading is stable.  Then I started adding my data drive (my only IDE drive).  Again, everuthing worked fine, except that the data was (for the momment) not accessible.  I have read that you can eventually read Windows NTFS partitions but cannot write into them.  I'll deal with that issue later.

When I connected my last SATA drive (this would make 3 hard disk connected), the one with Windows XP, everything screws up and I can no longer access Ubuntu.

Note that I made sure that my BIOS kept booting from my Ubuntu drive.

---

### Post by kakashi on 2005-11-16
try making your windows drive a slave to the ubuntu drive. then reinstall ubuntu
i only know and understand ide drives so your sata thing is something i cannpt understand but maybe someone else can. 
if it were ide i would say make your ubuntu hdd primary master but since its not ide try to port this instruction to sata

---

### Post by maverickdelta on 2005-11-17
I think I got it.

I am currently writting in Ubuntu 5.10, with WIN XP in dual boot.

I think that the Ubuntu installer cannot install properly in dual-boot if the other OS, WIN XP, is NOT the first disk in the BIOS.  My situation was a data disk as DISK0 (Primary IDE), my WIN XP as DISK1 (Third IDE) and my Ubuntu as DISK 2 (Fourth IDE).  I can only have WIN XP and Ubuntu in the last slots, as they are the only ones that allow SATA connections.

I managed to get dual-boot when I disconnected my data disk.  Now everything is zen between the two OS.

What I suppose I could do is to install WIN XP into an ordinary IDE (not SATA) hard disk  and work from there.  This would allow WIN XP to be on the first drive on the BIOS order.

---

### Post by kakashi on 2005-11-17
i don;t know if this is  a bug in ubuntu or not and i have no way to reproduce it cuz i don't use SATA. but maybe you should post a bug report.

---

