---
title: "Error 22 after installing a slave drive"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by satpandy on 2008-06-11
PC has had Master IDE drive and also a SATA drive for some time.  Original OS is XP Pro on the IDE. From time to time I hook up a slave IDE for data recovery, backup etc. on behalf of friends/customers.  I liked the look of Ubuntu and wanted to try it so I scrubbed the SATA of old data and installed dual boot with Ubuntu on SATA.  All worked well and GRUB gave option to boot to Ubuntu (default if no action) or to XP.  However, when I hook up a slave IDE and then start up, the GRUB gives an error message Error 22 - end of story.

I am still keen to be able to attach a slave IDE from time to time.

Can someone point this ageing (but new to Linux) small time IT support person in the right direction ?

Cheers

---

### Post by overdrank on 2008-06-11
> **satpandy said:**
> PC has had Master IDE drive and also a SATA drive for some time.  Original OS is XP Pro on the IDE. From time to time I hook up a slave IDE for data recovery, backup etc. on behalf of friends/customers.  I liked the look of Ubuntu and wanted to try it so I scrubbed the SATA of old data and installed dual boot with Ubuntu on SATA.  All worked well and GRUB gave option to boot to Ubuntu (default if no action) or to XP.  However, when I hook up a slave IDE and then start up, the GRUB gives an error message Error 22 - end of story.

I am still keen to be able to attach a slave IDE from time to time.

Can someone point this ageing (but new to Linux) small time IT support person in the right direction ?

Cheers
Hi and welcome, I am really not good with the grub but this link may help
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
Good luck!
Just in case this link has some good info 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
but it is a lot of reading.

---

### Post by logos34 on 2008-06-11
> **satpandy said:**
> However, when I hook up a slave IDE and then start up, the GRUB gives an error message Error 22 - end of story.

The most likely explanation is that since Grub scans the IDE channels first, if you add a second pata drive, it bumps the sata to third place (regardless of its actual boot order).  So at boot grub stage1 is looking for stage2 (and menu.lst) on (hd1) instead of its new position, (hd2).

If it was a question of permanently adding the drive, all you'd have to do is reinstall grub to the mbr, pointing to the root partition at the correct bios address.  But if swapping the drive in and out, not sure how to go about it

Afterthought:
I'm not even sure if switching to sata as boot drive would solve the problem

edit#2:
you could add a [dedicated grub partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") to the windows ide drive, but you'd still need to  change the 'root' line each time you connect up the slave.  There may be a better/easier way, though, dunno

---

