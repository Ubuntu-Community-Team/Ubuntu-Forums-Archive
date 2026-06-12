---
title: "Sata 6GB crashes ubuntu install"
date: 2014-01-04
forum: Installation &amp; Upgrades
---

### Post by michealmachado87 on 2014-01-04
Hello I am tring to install ubuntu on my desktop. I have spent all morning disconnecting hardware and such. My ubuntu live cd will boot and even install if i unplug the sata 6GBs on my mobo. However if I plug the addiotnal hard drives into them it freezes. So far I have gone into the bio and tried changing it to ide mode and no sucess.

The mobo is a rampage maximus V formula and its the black satas that make it crash.

Please help.

---

### Post by Bashing-om on 2014-01-05
michealmachado87; Hi ! Welcome to the forum.

Regret the delay in responding.

How are the hard disk(s) partitioned ? .. The old partitioning schemes do not deal with partitions larger than 2GB. With Large partitions GPT partitions are recommended.
See:
[http://ubuntuforums.org/showthread.php?t=1952953](http://ubuntuforums.org/showthread.php?t=1952953)
[http://ubuntuforums.org/showthread.php?p=12254717#post12254717](http://ubuntuforums.org/showthread.php?p=12254717#post12254717) 
in particular post #19

As good places to start. By all means post back with the need of further assistance.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2014-01-06
You will have to do some research on your motherboard, particularly the SATA/IDE support.  Some chipsets don't work well mixing SATA3 with SATA2 or SATA1 or IDE.  So you have to make a decision--how important are the older/slower drives?  The other option is to get a PCIe card with SATA ports and use that.  A new SATA card would have a newer chipset and by being on the PCI bus, it will be buffered from the other drives.

Although less likely, it's possible the new drive is pulling too much power for the motherboard or power supply.

---

