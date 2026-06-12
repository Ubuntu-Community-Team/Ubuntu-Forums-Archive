---
title: "Dapper GRUB failure stage 1.5 cant find files???"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by 51m0n on 2007-04-26
OK I gave up on Feisty went to Dapper.

In Dapper I can get to GRUB Loading Stage 1.5 and then nothing at all, no error.

I can, however boot using the Grub Super Disk!

Hooray!

Once into Dapper I start a terminal and:-

>sudo grub

grub> find /boot/grub/stage1

Error 15: File Not Found



How the hell did I manage to boot here at all??

I guess this is the root of the problem I've got here.

Interestingly Grub Super Disk refers to hda1 and in every distro I've ever run its lways been hde1 as its on the RAID controller (though just used as an IDE controller)

This is on an ABIT KG&-RAID board using the Highpoint controller as a secondary IDE (no raid). I've previously had this working with all sorts of distros, it seems however that all the new Debian derivatives fail now.

One last point, clearing the MBR boots into W2K no problem at all....

Any clues anyone?

---

