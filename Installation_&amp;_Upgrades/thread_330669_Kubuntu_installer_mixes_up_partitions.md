---
title: "Kubuntu installer mixes up partitions?"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by broxtor on 2007-01-03
My computer has two harddisks:
1: 300 Gig SATA disk, which I have partitioned as follows:
    /dev/sda1:  NTFS
    /dev/sda2: extended partation containing following volumes:
    /dev/sda5: FAT32
    /dev/sda6: Linux swap
    /dev/sda7: ReiserFS with Kubuntu Dapper
    /dev/sda8: ReiserFS with Kubuntu Dapper (for testing purposes)

2: 30 Gig IDE disk, which has only one partition (/dev/hda) and I only use to back up some important stuff in case the SATA disk crashes.

Today I tried to install Edgy on /dev/sda8. At least, I think that's the one I need. But when I choose manual partitioning in the installer, it shows that /dev/sda6 is ReiserFS containing Kubuntu instead of my swap partition. According to this partioner, my swap partition is /dev/sda8. But when I try to mount /dev/sda6, I can't do that because it's my swap partition. Mounting /dev/sda8 (or /dev/sda7) works fine. 
So that's the point where I cancelled the installer because I have no idea what will happen if I tell the installer to install Edgy to /dev/sda6. For all I know, it could also install to /dev/sda7 and that's not desirable.

Could someone explain to me what is going on here?

---

### Post by ajgreeny on 2007-01-03
In one of your working linux installs do:-
sudo fdsk -l
which will tell you for certain which partitions are formatted as which fs type.
You should then be able to mount them as appropriate and see what is on each partition using nautilus.  That should show where everything is without any uncertainties.

---

### Post by broxtor on 2007-01-04
Thnx for your response.
When I do the things you propose _I_ will know for certain which data is on which partition. But how can I be sure that if I tell the installer to format /dev/sda6 it will in fact format /dev/sda8?

---

### Post by Bartender on 2007-01-04
> **broxtor said:**
> Thnx for your response.
When I do the things you propose _I_ will know for certain which data is on which partition. But how can I be sure that if I tell the installer to format /dev/sda6 it will in fact format /dev/sda8?

Well, if you tell it to format sda6 it should format sda6, not 8.  ;) 

If you've got broadband download GParted LiveCD and make a bootable CD from that.  Practice on an old HDD if you can.

---

