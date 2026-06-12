---
title: "What happens to grub on Gutsy upgrade"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Aya Dream on 2007-11-06
Having recovered my Feisty installation (after a c: drive wipeout) and set up a dual boot floppy disk for Ubuntu/WinXP (to avoid Ubuntu booting from the C: drive mbr I want to know what will happen when I upgrade to Gutsy.

1) if I use the update manager will the update simply write grub to the mbr in hd0 or will it give me an option of where to install it?

2 if I use a CD upgrade should I use the LiveCD(Desktop) or the Alternate Installer?

At the end of the day I want the new /boot/grub along with menu.lst on the floppy disk (fd0).

Chhers
AD

---

### Post by bulldog on 2007-11-06
First of all,installing GRUB in the MBR of hdd 0 is perfectly okay.
It's rather easy to remove,that is if you have a windows install cd.
Grub is easely reinstallable too,so what is the problem here.

I think,but I'm not totally sure,you can skip installing GRUB with the altenate cd,or place it to another hdd.
Don't know if installing it on a floppy is one of the possebillity's .

---

### Post by Aya Dream on 2007-11-06
Hi Bulldog...again!   soooo quick in replying. Thanks.

I have this thing about putting grub on my c: drive mbr. What happened previously, the last problem you helped me with yesterday, was that bad RAM corrupted my c: drive mbr. When I booted up the machine it was looking for grub which controlled my ability to boot into Windows and Ubuntu so I couldn't boot into anything.

I fixed the windows boot problem by fixmbr which overwrote the grub. With your guidance I fixed my Ubuntu boot by putting grub on to a floppy (which can also boot my WinXP if necessary). So basically at the mo I'm happy.

All I want the upgrade to do is write the updated grub to my floppy or not at all (in which case I will manually configure grub on the floppy myself). I just don't want it to install on the c drive mbr again!

Cheers
Aya

---

### Post by bulldog on 2007-11-06
In that case I would use the alternate cd and see how it goes.
If grub should be installed,I know,you don't want it:),just remove it with the windows cd and make the entry on your boot floppy.
Otherwise I wouldn't know,I put grub always on the linux hdd and keep my windows hdd clean.
But you need to have two hdd's to do so.

---

### Post by Aya Dream on 2007-11-06
That's okay...I have two HDD's. You say 'I put grub always on the linux hdd (my s: drive) and keep my windows hdd (my c: drive) clean', then how do you boot into one or the other? Do you change BIOS to boot in to the OS (HDD) you want use?

---

### Post by bulldog on 2007-11-06
Nope,I set the linux hdd as first boot device in the BIOS,so grub will always start and I have a windows entry in the menu.lst,so I can start all of the OS's [5 at the moment] with grub.
If grub fails for what ever reason,I can change the boot order back and make the windows hdd the first boot device so windows will boot from it's own loader.

I even have the F11 button to push at startup and choose which device I want to boot on the fly.

Basically I have three hdd's.
One with 4 different distro's [8x10GB partitions so I can install some more if I want] a /home partition240GB and one swap partiton 
The second has three NTFS partitions for the windows stuff
The third is a 500GB disk with three ext3 partitions for all my files,ISO's,music,and other stuff I want to keep.
In this way I can install a lot of distro's with the same /home and swap,only thing you have to do is to choose a different username for each distro,so you get in your /home different folders for each distro.
[you can only see that as root though]

---

### Post by Aya Dream on 2007-11-06
Wow that sounds really neat. I'll give it a try. Thanks

I hate to go off topic but how did you set up the F11 button to determine boot device?
Is that a BIOS specific feature. My Bios is AMI 0704

---

### Post by bulldog on 2007-11-06
Didn't do a thing for that,it's a feature which comes with the board.[Asus A8N SLI de luxe]
But I had MSI boards that could do that too,look in the manual,or look at the screen at boot time,it's displayed at the bottom of the first bootscreen,it can be any key,like push del to go to the BIOS

---

### Post by Aya Dream on 2007-11-06
Ok, I've got an ASUS board (P4V800D-X) so I'll keep my eyes open at the next re-boot

Thanks for all your help.
Later
Aya

---

