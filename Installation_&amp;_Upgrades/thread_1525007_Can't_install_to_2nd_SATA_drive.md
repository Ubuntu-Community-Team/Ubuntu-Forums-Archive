---
title: "Can't install to 2nd SATA drive"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by choochoo22 on 2010-07-06
There are 2 identical 250GB SATA drives on the system.  SDA has Vista installed, SDB is an NTFS storage drive.  Vista works fine with both.

10.04 Live can mount and examine both drives.  GPARTED recognizes both drives and even re-partitioned SDB with about 120GB for NTFS and 120GB unpartitioned to make room for Linux.  The installation partitioner, however, only recognizes SDA with Vista, SDB is invisible.  I don't want to replace Vista, yet, I only want to install 10.04 on the second half of SDB to try things out.

How can I get past this problem?

---

### Post by dino99 on 2010-07-06
you may check the bios settings: select either ahci or automatic about sata and look too at boot order

---

### Post by fetuspuppet on 2010-07-06
Are you installing Windows first and then Ubuntu to the second drive? Also is the install through Wubi or a straight install off the Desktop disc?

You might have to either select which hard drive to boot from in the BIOS or have grub install an entry to your Windows hard drive boot area... This would tell the boot loaded to look on that second disk ans save you the headache of switching settings in the BIOS.

---

### Post by _Mark_ on 2010-07-06
I had the same problem
> sudo apt-get remove dmraid

should sort you out

---

### Post by fetuspuppet on 2010-07-06
> **choochoo22 said:**
> There are 2 identical 250GB SATA drives on the system.  SDA has Vista installed, SDB is an NTFS storage drive.  Vista works fine with both.

10.04 Live can mount and examine both drives.  GPARTED recognizes both drives and even re-partitioned SDB with about 120GB for NTFS and 120GB unpartitioned to make room for Linux.  The installation partitioner, however, only recognizes SDA with Vista, SDB is invisible.  I don't want to replace Vista, yet, I only want to install 10.04 on the second half of SDB to try things out.

How can I get past this problem?

Also!

Did you make the second drive Dynamic in Windows? Just curious.

Gparted Should see the NTFS and unpartitioned space on sdb...

If possible could you boot from the installer or live cd and open a shell?

Do a 

sudo fdisk /dev/sdb

Then hit p to print the output write that down and post what you get.

Hit cntrl c to exit fdisk without doing anything terrible.

---

### Post by fetuspuppet on 2010-07-06
Crap one last other thing... You don't have a RAID setup with both drives correct?

---

### Post by Pumalite on 2010-07-06
I bet is a Fake Raid

---

### Post by choochoo22 on 2010-07-06
There is a RAID on the MB but it is not in use, neither drive is connected to the RAID.  

Windows is already installed on sba.  

Gparted DOES see the second drive if I run gparted from the system menu, it actually created the empty space.  The second disk does not show up when installing.  Is gparted also used during installation or is it a different partitioner?

---

### Post by _Mark_ on 2010-07-06
Have you tried what i suggested?

---

### Post by choochoo22 on 2010-07-07
Thanks Mark, remove dmraid did the trick.  I only had a few minutes and didn't have time to try that this morning.

---

### Post by _Mark_ on 2010-07-07
Glad it worked for you, the same problem was driving me nuts when I installed Lucid a while back, gparted and the the disk utility could see both drives yet the installer wouldn't

---

