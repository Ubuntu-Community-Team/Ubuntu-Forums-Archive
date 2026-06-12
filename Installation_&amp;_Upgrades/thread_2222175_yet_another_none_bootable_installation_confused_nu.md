---
title: "yet another none bootable installation confused nuuuuubee"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by ruggb on 2014-05-05
I first tried a dual boot - WinXP and Linux Mint 13 (Maya).
XP worked but when I installed Linux - either something else, defining the partitions, or just let it do its thing, it would only boot from CD
All the partitions and files seem to be there just no boot to Linux without the cd.
I then did a reformat with the windows install CD and a clean install of just linux. same issue.

I tried some solutions in other threads but no joy.

I am in GNU-GRUB and    "ls" yields (hd0) (hd0,msdos5) (hd0,msdos1)
and of course   "ls (hd0,msdos5)" >> not a known filesystem

If I boot to linuxCD and view the filesystem there, all the files appear to be on the HDD.
there is also CDROM but it shows me over 800MB - for the CD???
So maybe I am reading that all wrong. The first screen shows the HDD and "filesystem"
Both show similar folders but there r more files on the HDD in boot/grub
so I am not sure what "filesystem" is showing me.


So what is going wrong with the install that it is showing msdos partitions?

I have used the same CD to install on another laptop and it is working OK.
I had to do a 'nomodeset" trick on that one b/c it would not even boot the CD

---

### Post by zombienerd1 on 2014-05-05
If you're getting a Grub Rescue prompt, then grub just didn't install properly.

MBR partitions (how most drives are partitioned), will show up as msdos in grub rescue mode, that is normal.

Follow this guide to re-install grub properly from a live cd:

[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

