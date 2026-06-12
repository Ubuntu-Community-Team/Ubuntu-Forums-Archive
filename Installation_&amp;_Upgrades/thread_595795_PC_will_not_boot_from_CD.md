---
title: "PC will not boot from CD"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Symmetric on 2007-10-29
Hi there,

I tried to reinstall Linux recently, after reinstalling WinXP. I previously had dual boot using Grub - the Linux partitione still exists, but my PC is booting from windows at the moment.

Now to the problem - when I try to boot from a CD, my mobo gets through POST and then says "PRESS A KEY TO REBOOT" at the point it would normally boot from the CD. This happens both with my Ubuntu boot CDs, and with my WinXP cd as well. I have checked the disks in other computers and they are fine. I have checked that my boot order is correct, and even tried unplugging the HD that windows boots from.

Any ideas on what could be causing this problem? Are any pieces of hardware other than my mobo and dvd drive involved at this stage of the boot process?

Thanks in advance,
Paul

---

### Post by Symmetric on 2007-10-30
I've realised that it might be useful to provide my PC specs... here they are.

ASUS P4G8X Deluxe motherboard
P4 2.5Ghz
1GB RAM
ATI Radeon 9800Pro
2x DVD writers
2x Maxtor 80GB IDE HDD (one is my Windows disk, one has my Linux partitions)
1x Maxtor 160GB SATA HDD
1x WD 500GB SATA HDD

Cheers,
P

---

### Post by Chappy7777 on 2007-10-30
Take a look at the thread about 3 above your, titled

Can't boot ubuntu cd   
billgoldberg 

He is having the same hassles as you and you two should work together on finding an answer.

Seems like you set your Boot Order is the BIOS, right?

When you 1st boot up, so you see your CD listed as Secondary Master, or Primary Slave, or whatever?
Is it listed is the point. If yes, then the MB is seeing it. If not, it ain't. 

Try changing the IDE cable. They do die.

---

### Post by Symmetric on 2007-10-30
Thanks for pointing out that thread.

My boot order is definitely correct, and I get the same thing when attempting to boot from both of my DVD drives. They are working fine otherwise, so it seems unlikely that it's something to do with the cable, or the drives.

It seems to me that this must be a problem with the motherboard, BIOS, or DVD drives. Could it be anything else?

Cheers,
Paul

---

### Post by vasalos on 2008-05-08
It is too strange, but i am having the same problem too. I cannot but my Hardy disk.I believe that disk's MBR is not working properly with all BIOSes.Am I missing something?

---

### Post by bigken on 2008-05-08
I would try unpluging all the hdd and cd/dvd roms then  try 1 cd/dvd at a time

---

### Post by weee on 2008-05-08
When you downloaded Ubuntu, did you use a cd burner to transfer the ISO file to cd?

---

### Post by speedgator on 2008-05-11
Tried creating my own thread, but couldn't and this seemed close enough.
My issue:

Have XP, repartitioned drive with Parted Magic, have a 10GB partition now set aside for Ubuntu. Boot from 8.04 Ubuntu cd from iso and get "No setup signature found"
Tried googling but no concrete answer(s) thus far.
Any help appreciated.

I did "Check CD for defects" and "Install Ubuntu" and get a popup window with:

Boot loader
/casper/vmlinuz

Hit Enter and nothing. ?

---

