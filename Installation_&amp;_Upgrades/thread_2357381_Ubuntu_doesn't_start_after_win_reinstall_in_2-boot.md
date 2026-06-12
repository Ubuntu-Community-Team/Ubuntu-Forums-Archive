---
title: "Ubuntu doesn't start after win reinstall in 2-boot hdd"
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by gipsyshadow on 2017-04-01
I've got an old notebook with 512MB ram with a dual boot windows xp / lubuntu 16.04 and the last one was installed by an alternate cd because of the few ram amount. The hdd is partitioned in this way:
sda1 swap
sda2 win
sda3 linux
sda4 logic

After windows reinstallation grub2 was missed and I used the alternate lubuntu cd to restore it. I followed this way:

start screen -> Rescue a broken system, F6, ESC, typed "forcepae -- forcepae" at the end of the bottom string
go on as a normal installation till
device you wish to use as your root file system: /dev/sda3
Enter rescue mode -> Reinstall GRUB boot loader 
Device for boot loader installation: /dev/sda
Reboot the system

Grub2 menu reappeared but when I select ubuntu (first line of the list of course) it doesn't start. I don't understand very well what appears because I'm very noob but I think it's a sort of emergency mode because I can read lines like these:
ERROR child device config size 27 is too small
ERROR cpu pipe a fifo underrun
ERROR cpu pipe b fifo underrun
/dev/sda: recovering journal
/dev/sda3: clean...
nsc-ircc wrong chip version ff
....
A start job is running for dev-disk-by\x2duuid-1ca46b....
...
Welcome to emergency mode! After logging in...
...
(or press control-d to continue)

What kind of mistakes did I do in grub restoring by alternate cd? Why doesn't ubuntu start?

I tried with supergrubdisk following the steps recommended:
put the .iso in a pendrive with yumi
started
selected "detect and show boot methods"
kernels list appeared and I selected the last one I used "...4.4.0-70-generic (hd1, msdos3)"
emergency mode started and I waited for a while because of the 1m30' countdown for "A start job is running for dev-disk-by..."
then I typed my password and gave these commands:
```
grub-install /dev/sda
```
output ok, then 
```
update-grub
```
ok too
I rebooted and the usual grub menu appeared, selected ubuntu but the usual emergency mode routine started as described above.

Could you tell me what's wrong with my booting and how to fix ubuntu start?
...maybe did I type my username wrongly during alternate cd grub restoring steps attempt?
(sorry for my bad english)

---

