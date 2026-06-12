---
title: "Persistence file in USB installation"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by Ratul Saha on 2010-12-03
Hi,
When making a USB drive bootable by usb-creator in ubuntu 10.10, there is an option of making a persistence file. Is it possible to install the exactly same softwares and configurations I have in some other computer using that feature? If possible, how is it? How to use that persistence file? I believe if it is possible, I can install my exact computer configuration in some offline computer also.

Thanks a lot in advance,

Ratul.

---

### Post by efflandt on 2010-12-03
Persistent data in Startup Disk Creator is a loop mounted file system which is shown as casper-rw file if you look at the USB stick from another system.  However, that is not mounted when you initially boot from the USB iso until "after" the kernel boots and other things happen from a fixed squashfs file system.

So while persistent data from Startup Disk Creator allows you to add programs to that USB system, you should not attempt to update or install proprietary video drivers or new kernel or anything else that happens during boot before casper-rw is loop mounted  (see **dmesg | less** or /var/log/messages when booted from that system to see the sequence of events during boot).

You can do a "regular" install to USB (8 GB or larger recommended), but you have to make certain that you put grub on the USB and not your internal drive mbr.  In 10.10 you select where to put grub at the bottom of the manual partitioning screen.

---

### Post by Ratul Saha on 2010-12-03
Thanks a ton for your kind reply.
I am sorry, but if I have some softwares (like gimp and all) installed from normal internet and want my friend with offline computer to use them too then what should I exactly do? When I make persistence space full and make the bootable USB, it makes some kind of binary file (huge though) in the USB. Does it contain the softwares I have? And how to retrieve them back in the guest computer when installing ubuntu?

Thanks again,
Ratul.

---

### Post by C.S.Cameron on 2010-12-03
You can copy the casper-rw persistence file from one disk to another, as long as the versions are the same.
I see problems copying stuff from a full install to a persistent one though, although I have not tried it.

---

