---
title: "[SOLVED] Fiesty installation stops at 75%"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by ashikahamed on 2007-08-27
Fiesty installation stops at 75% installing packages (configuring wvdial) .I don't get any error messages.It justs stops there and i couldn't see any progress even after waiting for two  hour.I'm using alternate install cd and it  passed the integrity check and my computer has the following configuration

Intel(R) Pentium(R) 4 CPU 2.40GHz 
640 MB DDR2 RAM (512mb+128mb)
Intel(R) 82845G chipset
Realtek RTL8139 Family PCI Fast Ethernet card
C-Media AC97 sound device
SONY DVD RW AW-G170A 

and I had been using ubuntu 6.06 LTS successfully earlier

The problems i encountered during installation were  my hard disk partitions which had hda,hdb as names in ubuntu6.06 are shown as sda,sdb.My ethernet card was not detected and i opted to configure network later during installation

can anyone help me installing fiesty?

---

### Post by Pumalite on 2007-08-27
Feisty will recognize your drives as sda, sdb,etc. You have good hardware. Your choice of Alternate CD is excellent. We have to concentrate on iso, md5sum, check CD for corruption before install, burning at 4x, etc. Did you do md5sum and compare it to the one from which you downloaded?

---

### Post by charles woodward on 2007-08-28
I have this same problem on feisty and Gutsy - problem is that as I was loading Gutsy onto a second partition the failure in the install script also corrupted the grub - so I had to install a command line version just to get my live system back into working order.

I've spent two days trying various things, and reading the forums - there are loads of people with problems caused when wvdial is being installed - but no real responses.  I wonder how many newbies have had the same problem and just given up?

---

### Post by ashikahamed on 2007-08-28
Finally i got Fiesty running in my computer!
I disconnected all the peripherals and installed fiesty.The installation finished successfully.Everything works fine now.

I also burned my install cd again at the lowest speed possible in my burner (8x)

[COLOR="Red"]Thanks for your help guys[/COLOR]

---

