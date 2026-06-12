---
title: "Uuid"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by kurianthayil on 2007-07-29
im quite new to ubuntu and debian.. i was using red hat and fedora flavors till now.. i happened to see UUID in /etc/fstab.. wat is the significance of it????? is it similar to a label in red hat and fedora??? plz reply...

---

### Post by bbzbryce on 2007-07-29
> **kurianthayil said:**
> im quite new to ubuntu and debian.. i was using red hat and fedora flavors till now.. i happened to see UUID in /etc/fstab.. wat is the significance of it????? is it similar to a label in red hat and fedora??? plz reply...

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=223182&highlight=uuid](http://ubuntuforums.org/showthread.php?t=223182&highlight=uuid)

Basically UUID is better than /dev/hda1 because if you reconnect your devices in a different order then fstab will not correspond correctly. With UUID no matter how you connect fstab will be valid.

---

### Post by MQMike on 2007-07-29
To see your UUIDs, use the command (at a terminal in Ubuntu):  
 
$ ls /dev/disk/by-uuid/ -alh   

(Note: “ls” is “l” as in “list”; and “-alh” is also with an “l” as in”list”)

---

### Post by louieb on 2007-07-29
> **bbzbryce said:**
> Basically UUID is better than /dev/hda1 because if you reconnect your devices in a different order then fstab will not correspond correctly. With UUID no matter how you connect fstab will be valid.
That's the theory, but in practice my swap partitions UUID has changed a couple of times with kernel updates. And I've seen threads about the UUID changing when a partition gets re-sized, not only the re-sized partition but others on the same drive.

---

### Post by forestpixie on 2007-07-29
I had a UUID change 2 days ago - took me ages to find that, I'd got rid of windows - moved Ubuntu - ended up with two root partitions - reformatted the old one and kapow - couldn't get the partition to mount till I found the UUID change

---

### Post by MQMike on 2007-07-29
That’s my understanding, too.  Any change to partitions/filesystems will change the UUIDs.
I also noticed swap partitions changing UUIDs, maybe they are assigned dynamically?  Don’t know.
Any changes MAY also change how your system dual-boots, so the fstab must be checked along with the /boot/grub/menu.lst (your kernel lines), and you can always use that command I gave above to check things.

Also, previously in Ubuntu, SATA drives were sda, sdb, etc., and PATA drives were hda, hdb, etc.  Now both are referred to using sda, sdb, etc.   [https://wiki.ubuntu.com/LibAtaForAtaDisks](https://wiki.ubuntu.com/LibAtaForAtaDisks)

This change is at the operating system level.  It is not a change in GRUB (or some other place).
But it affects how GRUB passes the root device to the operating system in the kernel line of the GRUB configuration file (ie, in /boot/grub/menu.lst).

---

