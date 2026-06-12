---
title: "GRUB and Acer MBR"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by brancalessio on 2011-02-26
Dear All,
  my system is an Acer Aspire One Happy netbook. It runs Windows 7 OEM.

I installed Ubuntu Netbook Remix, which works fine. Unfortunately, I put GRUB in the MBR (I wanted it on Ubuntu partition in order to use Win 7 bootloader). Acer netbooks seem to have a particular MBR (in order to run e-Recovery Management), which is different to the standard Windows 7 MBR. Moreover, in the internet there are instruction to restore Acer MBR, but they do not seem useful, since I do not find the MBRWRWIN.EXE and RTMBR.BIN files on the hidden partition.

Is there a way to tell GRUB to remove itself and restore the previous content of the MBR (something like the old "lilo -u")?

Does GRUB make a copy of the content of the MBR before installing itself? Where is it, if it is so?

Thanks for all answers!

---

### Post by brancalessio on 2011-02-28
May be I can restore the MBR in this way.

After resizing Win 7 partition and creating in the free space two unformatted partition (one to be mounted on /, the other as swap), I made a backup of the MBR doing

```
dd if=/dev/sda of=old_mbr bs=**512** count = 1
```

After that I installed Ubuntu Netbook Remix (the two partitions where formatted and GRUB installed in the MBR).

Is it OK to do now

```
dd if=old_mbr of=/dev/sda bs=**446** count=1
```

in order to restore the old MBR? It may be a problem the fact that the MBR backup was done with unformatted partitions (whose type was not 82 and 83).

Thanks for your answers!

---

### Post by brancalessio on 2011-03-01
It just worked!

I will now re-install Ubuntu more carefully. Anyway, I must say that GRUB2 lauches the Acer Recovery System much better that the Acer MBR itself!

---

