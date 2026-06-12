---
title: "Can't boot into Windows after Gutsy install"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by hangman_jdf on 2007-12-02
I am a noob but have been using ubuntu since dapper.  I did a clean install of gutsy about 1 week ago and have had very little trouble getting things to work.  I currently dual-boot with windows xp.  I needed to use windows today but after Grub loaded and I selected windows.  I received this message:  

"A problem has been detected and windows has been shut down to prevent damage to your computer.
Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check you hard drive to make sure it is properly configure and terrminated Run ChKDSK /F to check for Hard drive corruption, and restart your computer."

My windows partition can still be seen by when I boot into ubuntu so I didn't delete it.

Output of sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        4260    34178287+   b  W95 FAT32
/dev/sda3            4261       14412    81545940   83  Linux
/dev/sda4           14413       14593     1453882+   5  Extended
/dev/sda5           14413       14593     1453851   82  Linux swap / Solaris

I am not really sure what to do except reformatting hard drive and reinstalling windows and then ubuntu again.  But I would really want to avoid this as much as possible.

Thanks for any advice.

---

### Post by baxterdog on 2007-12-02
Did you try SP2? And format the ubuntu partition with ext3?

---

### Post by hangman_jdf on 2007-12-02
Sorry, but I am unsure what you mean by SP2.  I did take my windows Cd and booted into recovery and tried chkdsk /r.  It gave me the message about more than one error to fix or something like that.

As for the ext3, that is what I chose to use on the clean install of 7.10.

---

