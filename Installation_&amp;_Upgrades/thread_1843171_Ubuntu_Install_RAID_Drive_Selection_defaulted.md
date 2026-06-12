---
title: "Ubuntu Install RAID Drive Selection defaulted"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by puleen on 2011-09-13
Folks, I am trying to install Ubuntu 10.10 on a set of newly formatted drives.

I have 3 drives as follows:

1. 160GB SATA (Ubuntu)
2. 160GB SATA (unallocated)
3. 250GB SATA (NTFS)

I don't want to install RAID, want to do a JBOD type install.

Each time I try to install it gives me a screen which looks as follows:

[[img]http://www.imgsrc.com/thumbs/ubuntu1010.png[/img]](http://www.imgsrc.com/?v=ubuntu1010.png)

Can anyone point me in the right direction? I also want to install Windows 7 on a separate partition within drive #1.

Thanks,

---

### Post by YesWeCan on 2011-09-14
Hi. It looks like your drives were once part of a Windows RAID. You need to remove the RAID super-blocks.
In the live session, open a terminal and run
[COLOR="DarkSlateBlue"]sudo fdisk -lu[/COLOR]
to see the names of your drives
then run this for each drive, subtituting x for each drive letter
[COLOR="DarkSlateBlue"]sudo dmraid -E -r /dev/sdx[/COLOR]


As an additional precaution you should disable all RAID options in your BIOS.

---

### Post by puleen on 2011-09-15
That seems to have done it. Once I install Windows on the second partition, I will see what happens and let you know.

The two drives no longer get detected as part of a RAID and do show up individually. :)

You are a savior! :)

---

### Post by YesWeCan on 2011-09-15
Good stuff. If everything is working please mark this as solved in [COLOR="Red"]Thread Tools[/COLOR].

---

