---
title: "error: the symbol grub_puts_ not found [10.04 LTS]"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by 116e32s on 2012-08-23
I had Karmic Koala (due to an obsolete package that does not work in new
releases). This was getting a bit senile in other respects, and I found out that I could upgrade to 10.04 LTS and still run my finicky package with some simple kludges.  Plus I hate Prententious Pangolin desktop and would never use it for a million quid. This was on a dual-boot PC with Windoze on one hard disk and Ubuntu on the other.
So I downloaded the DVD ISO and installed it (after backing up the disks of course).  The setup told me that sda was FAT32/NTFS and sdb was ext4, so I installed Ubuntu to sdb. It said boot loader would go on sda, and I did not change that. But after rebooting I see from GRUB:
error: the symbol 'grub_puts_' not found
So I went to BIOS and changed the boot order, thinking that well I can at
least get Windoze running and search for an answer.
But I see the GRUB boot options, I chose Windoze and it still works.
I rebooted and chose linux and hey Ubuntu 10.04 slowly rises from the mist.
So what is going on?  I presume I must have some sort of boot loader on
both disks.  Was there some change between 9.10 and 10.04 where it goes
on a two-disk setup?
;)

---

### Post by YannBuntu on 2012-08-23
Hello
Please indicate your Boot-Info URL. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

