---
title: "Grub error 18"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by steflik on 2005-07-12
I just did a network install of Ubuntu, everything seemed to go OK until it tried to reboot, then Grub spits out the error 18 message and hangs. The machine is a Toshiba Portege with a 266 Mhz P2 and 64 Mb of Ram and a 30 Gb harddrive. It was set up dual boot with W98 and Debian with LILO and worked good. I reformatted the Debian partition and installed Ubuntu to the reformatted partition. Can I switch back over to LILO, if so how do i installit from a boot floppy  since neither W98 or Ubuntu boots.

Dick Steflik

---

### Post by JaM on 2005-07-12
> 
18 : Selected cylinder exceeds maximum supported by BIOS
     This error is returned when a read is attempted at a linear block
     address beyond the end of the BIOS translated area. This generally
     happens if your disk is larger than the BIOS can handle (512MB for
     (E)IDE disks on older machines or larger than 8GB in general).

I think you / parition is over 8GB.

Perhaps you find an anwer in this topic: [http://ubuntuforums.org/showthread.php?t=11764](http://ubuntuforums.org/showthread.php?t=11764)

I always make a small /boot partition (128 MB) in ext3 so that most common boot problems are solved.

---

### Post by steflik on 2005-07-12
Yes, all of my partitions are over 8 Gb (except the swap partition) the partition size never bothered LILO when I was running Debian, can I replace Grub with LILO? If so how do I do i?

Dick Steflik

---

### Post by JaM on 2005-07-12
```

sudo apt-get install lilo
sudo gedit /etc/lilo.conf
sudo /sbin/lilo

```
Remember with lilo you have to run lilo everytime your kernel or lilo.conf changes.

---

