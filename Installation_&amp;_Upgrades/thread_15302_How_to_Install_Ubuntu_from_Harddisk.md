---
title: "How to Install Ubuntu from Harddisk???"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by moufranica on 2005-02-13
Hi guys,
Is there a way to install Ubuntu from windows xp? I have downloaded the iso file, but my CD-Rom can't boot from CD. Is there a way to do a Hard Drive install? Thanks.

---

### Post by tim1 on 2005-02-13
Every CD-Rom should be able to boot from CD. If the Ubuntu CD doesn't boot it is either corrupted, or the computer is not set up to boot from CD. This can be changed in the BIOS. When your pc boots, you can press a certain key (usually Del) and the BIOS configuration appears. Somewhere the is an option in which order the pc tries to boot from the devices. You have to set the CD-Rom to be before the harddisk, then everything should work fine.

greets, tim

---

### Post by az on 2005-02-13
"Every CD-Rom should be able to boot from CD"

No.  That is wrong.


Ther is a utility called smart boot manager:

[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

[http://slackware.at/data/slackware-current/rootdisks/sbootmgr.dsk](http://slackware.at/data/slackware-current/rootdisks/sbootmgr.dsk)

dd if=sbootmgr.dsk of=/dev/fd0 


You can boot from floppy and then it will detect and boot your disk.

---

### Post by moufranica on 2005-02-14
[QUOTE=tim1]Every CD-Rom should be able to boot from CD. If the Ubuntu CD doesn't boot it is either corrupted, or the computer is not set up to boot from CD. This can be changed in the BIOS. When your pc boots, you can press a certain key (usually Del) and the BIOS configuration appears. Somewhere the is an option in which order the pc tries to boot from the devices. You have to set the CD-Rom to be before the harddisk, then everything should work fine.

greets, tim[/QUOTE]

Sorry, I wasn't clear, what I meant was that my system cant' boot from CD-ROM. Plus I have no CD Writer. I was wondering if I could do a Hard Disk Install. Like in Mandrake Linux. Thanks for help.

---

### Post by welly on 2005-03-01
[QUOTE=moufranica]Sorry, I wasn't clear, what I meant was that my system cant' boot from CD-ROM. Plus I have no CD Writer. I was wondering if I could do a Hard Disk Install. Like in Mandrake Linux. Thanks for help.[/QUOTE]

Did you ever find out how to do this? I'm trying to do the same.

---

### Post by welly on 2005-03-01
[QUOTE=welly]Did you ever find out how to do this? I'm trying to do the same.[/QUOTE]
 Well I've tried every source I could possibly try to discover a way of installing from the hard drive but have had no luck and absolutely no response on this forum in a number of posts I've made about the subject so I'm taking it as it's not possible to install directly from the hard drive.

---

