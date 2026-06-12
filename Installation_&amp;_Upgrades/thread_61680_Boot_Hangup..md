---
title: "Boot Hangup."
date: 2005-09-01
forum: Installation &amp; Upgrades
---

### Post by novaspam on 2005-09-01
I am dual booting Ubuntu and Windows using NTLDR, ive done this dozens of times with lilo with absolutely no problems but Ubuntu uses GRUB, and its hanging.  I used DD to copy the first 512 bytes of my second HDD (which contains Ubuntu) and when I try to boot it just says GRUB, and hangs.  Im curious did it not copy to the MBR of that drive but do the disk in which case i need to DD size=1M? Also grub was installed to that drive per the installer.  Thanks.

---

### Post by tepaks on 2006-05-20
I have same problem with clean install (no muliti boot) on conpaq EVO 510 e-pc PIV 2.4  512 Mb 30 Gb. Initial setup goes fine until first reboot. It just displays "GRUB is loading please wait" and hangs. Tryed PCI=NOACPI option without succsess. Any ideas?

---

