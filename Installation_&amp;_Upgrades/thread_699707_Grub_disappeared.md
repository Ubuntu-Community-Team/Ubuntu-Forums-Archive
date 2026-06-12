---
title: "Grub disappeared"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by yoghurt on 2008-02-17
Hi Ubuntu users and fans,
I've got a problem. I had a perfectly working dual boot system with WinXP Pro and Ubuntu 7.10. After some action I don't exactly remember I chose to reinstall Ubuntu. After doing so, my Grub stopped working (was giving me errors when trying to boot to Win and even to Ubuntu) and as I wasn't able to fix that I booted from WinXP install CD and performed the recovery console command "fixmbr".
This did help me to boot WinXP OK, but that's where the problem started....

I cannot make my Grub work. Each time I start up my PC, there is simply no Grub. I've looked around these forums and have seen the basic help:

- boot Ubuntu liveCD
- open terminal, perform "sudo grub"
- find /boot/grub/stage1
- root (hd?,?) -> outcome of the find command
- setup (hd0)
- quit

This all worked nicely and there was no error message. Much to my surprise this didn't help though and I still only get WinXP with NO grub at all. I've tried re-installing ubuntu couple of times, but to no avail.

My HDD config is:

- IDE HDD with ntfs partition (winXP "c:\")
- SATA HDD with 1/2 ntfs and 1/2 ext3 (ubuntu)

EDIT: my problem was solved

---

### Post by logos34 on 2008-02-17
try switching the boot order in the Bios so the sata with ubuntu is first.  Anything?  If you get the grub menu screen but it gives you error trying to boot either OS, try pressing 'e' to edit, 'e' again on the 'root' line and changing it from (hd0,?) to (hd1,?) or vice versa.

---

### Post by yoghurt on 2008-02-18
Thanks, I'll give it a go. Will post the results here...

EDIT: I think I've thought about all possible solutions from the more rational ones, like "it must be some hidden trick in Grub setup" to the crazier ones like "I'll buy a new HDD and screw the partitioning", but this simple idea has never entered my tired mind.
So BIG THANKS to Logos34 for this advice.

---

