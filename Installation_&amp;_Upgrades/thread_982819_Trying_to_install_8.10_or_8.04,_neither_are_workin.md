---
title: "Trying to install 8.10 or 8.04, neither are working"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by asenine on 2008-11-15
Hi,

I have been trying to get Ubuntu into a dual boot with my XP, I have the drive split into two partitions, one formatted for XP (which is installed), and one not. I tried to install 8.10 earlier this morning, but it gave me 'I/O error' and an option to reboot. I don't recall what the exact message was, because now I have 8.04 on the disk.

Anyway, 8.04 opens up fine, but when I go to install it it says the following about 15 seconds after the bootload screen comes up (with the moving bar):

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)ata1.00: revalidation failed errorno=-5
ata1.00: revalidation failed errorno=-5
ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
ata2.00: status { DRDY }
ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
ata2.00: status { DRDY }
ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
ata2.00: status { DRDY }
ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
ata2.00: status { DRDY }
...
```

Etcetera.

And then, every 300 seconds or so, it says:

```
ata2: Warning, synchronous SCSI scan failed without making any progress!
```

Eventually my screen turns off (at about 700 seconds or so) and then comes back on.

Does anyone know what I should do to fix this? Thanks. :)

EDIT: Just to let you know, I can do whatever is needed with the drive, everything is nice and backed up onto an external drive.

Also, I have tried various distros, but none seem to want to boot further than this - I am downloading the latest Debian DVD distro to see if that does it as we speak, but I don't see how that would be any different. **I *can* boot into Windows XP, if you want any commands run there.**

---

### Post by asenine on 2008-11-15
A note, this ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635")) seems very similar, what should I take from that? (Bear in mind, Gutsy isn't booting either)

---

