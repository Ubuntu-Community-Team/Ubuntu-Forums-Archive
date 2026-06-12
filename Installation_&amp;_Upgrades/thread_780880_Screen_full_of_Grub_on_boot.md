---
title: "Screen full of Grub on boot"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by jimmy678 on 2008-05-03
Hi,
I'm tryimg to install Ubuntu on a PC. I'm entierly new to Linux but have dowloaded 8.04, burnt the disk and installed it. It works fine however it will not boot without loading Grub or having the LiveCD in the machine and selecting boot from first harddrive. If I don't have either of these I get a screen full of "Grub" - every line full of the word. 

I have used fdisk and the partitions seem to make sense to my very limited understanding of things. The machine has two SCSI disks in it 60Mb and 8Mb. I've also tried to reinstall using both the whole disk option and the 95% disk option.

Any advice would be appreciated.

---

### Post by Herman on 2008-05-04
Try going into your BIOS settings and find where your hard drives settings are and check whether your hard drives are set on 'auto' or 'user'.
In some BIOSes it might be 'auto detect' and 'CHS'.
Whatever it is, try changing it the the other setting and see if that helps.

I would think that 'auto', or auto detect' would be most likely to be the proper setting, but some people report the opposite works for them, I suppose it depends on your hard disk.

---

