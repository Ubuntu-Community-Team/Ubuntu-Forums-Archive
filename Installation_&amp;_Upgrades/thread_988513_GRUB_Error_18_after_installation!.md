---
title: "GRUB Error 18 after installation!"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by crik91 on 2008-11-20
I have a laptop: Toshiba Satellite A60-332.
I installed Ubuntu through AlternateCD without errors. 
I used noapic nolapic.
When:
GRUB Loading stage 1.5.


Grub loading, please wait ...
Error 18
I have tried to solve SuperGrub without success.
Someone can help me please?
Thank you!!!

---

### Post by pennacook on 2008-11-20
Grub error 18 means that your hard drive is larger than the BIOS can address. Linux only uses the BIOS to address the hard drive during boot so boot is the only time the problem can appear.

The way to solve the problem is to create a small partition -- maybe 300 megs or so -- at the beginning of the hard drive and place /boot in that partition

---

### Post by crik91 on 2008-11-20
How to do that?I'm newbie. :)
Thank you...

---

### Post by caljohnsmith on 2008-11-20
In addition to your other partitions, just create a ~200 MB ext3 partition at the beginning of your HDD like pennacook mentioned, and then when you go through the Ubuntu installation process, set the mount point on that partition as "/boot". If you need more specifics, how about first opening a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by crik91 on 2008-11-22
Hello, thanks for your help.I put /boot after the MBR then there is Windows then the rest of Ubuntu.Now GRUB works. :KS

---

