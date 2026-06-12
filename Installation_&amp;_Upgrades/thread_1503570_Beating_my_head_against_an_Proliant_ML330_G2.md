---
title: "Beating my head against an Proliant ML330 G2"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by sha.goyjo on 2010-06-06
Alright, I've been trying to do this forever, and I just can't seem to get the system to recognize the install and boot from it. Do I need to create a very small bootstrap partition or something?

Just for clarification, I've tried installing to the onboard ide controller as well as the raid controller. Both installed, but failed to be picked up on boot. The system only seems to be able to boot from cd. Furthermore, I can't seem to use the CD to boot from the hard disk.

Does anyone else have any experience with this model?

---

### Post by alterpinguin on 2010-06-07
i dont remember the old Proliant models at all. It was the time
this models were called Compaq Proliants and not HP(bought Compag later).
I used "old" RedHat for those DualCore-Proliants and without the proliant-setup-disk, it was not possible to install the linux-version because it was necessary to change some settings in the "bios" of those computers. Dont get me wrong, but this was the days, when hardware-settings could not all made from an built-in-bios-software.
There were options to setup the boot-sequence to boot windows-nt, linux, .. and i think there was later an bsd-option too.
RedHat was enhanced in these days with some compaq-drivers for the raid-system, fan, temperature, ..-- on-board ethernet... 
you might try to check/search for more information about those hardware - and like told, if the mainboard was setup to boot windows-nt i think there is no way to boot linux ...
(omg .. those days of the eisa-bus .. and other crazy hardware-stuff ..)

---

### Post by sha.goyjo on 2010-06-07
I have the smart start cd for setting up different old linux distros, but the whole point of the system is to run an openerp server. There are other options I guess, but I would really rather do it this way.

---

### Post by dino99 on 2010-06-07
have you seen this link: [http://wiki.debian.org/HP/ProLiant](http://wiki.debian.org/HP/ProLiant) ?

---

### Post by sha.goyjo on 2010-06-07
> **dino99 said:**
> have you seen this link: [http://wiki.debian.org/HP/ProLiant](http://wiki.debian.org/HP/ProLiant) ?

Yes, I have. Unfortunately, my Proliant is a g2 (not listed) and the g3 instructions don't work. Also, I have IDE raid instead of SCSI. I don't know if that makes a difference. 

But thanks for the advice anyways. I've been trying to get this sucker to boot for about a month. If I can get it up it'll save me about 3000 clams on office setup.

---

### Post by sha.goyjo on 2010-06-09
Still no other help?

---

### Post by kansasnoob on 2010-06-09
I'm not at all acquainted with that model, but thought this may be helpful:

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

But that deals with legacy grub and not grub 2. I'm just wondering if that might describe the basic situation :confused:

If so I'd investigate the BIOS limits and consider using a separate /boot partition. Generally if it's within the 33.8 or 137 GB limit I just begin with a 6 to 10 GB root "/" partition, then a /home and SWAP.

I haven't found any documentation regarding separate /boot partitions with grub 2.

---

