---
title: "Installation of Netbook Remix on Eee PC 1001PX"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by Otiosedodge on 2010-09-26
Hi All,

I'm trying to install from a USB drive. I followed the instructions given on an Ubuntu website, only to get the following output when booting from the drive:

SYSLINUX 3.86 2010-04-01 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al
No DEFAULT or UI configuration directive found!
boot:

Thanks in advance for any help.

---

### Post by sikander3786 on 2010-09-26
Hi.

Rename the isolinux folder on the USB to syslinux. And under syslinux folder two more files isolinux.bin and isolinux.cfg to syslinux.bin and syslinux.cfg respectively. Now it should work.

How was the driver prepared? Using unetbootin? Seems like a bug in the new version.

---

### Post by Otiosedodge on 2010-09-26
Worked like a charm! Just one thing for the absolute newbies: the isolinux.bin file is not listed with the .bin suffix. It's listed simply as isolinux. So I just changed that to syslinux.

I used the Universal USB Installer available from pendrivelinux.com. Hope that answers your question.

---

### Post by Townley89 on 2011-08-30
I'm installing desktop edition so if this doesn't apply, let me know, but I was having the same problem. 

In my USB creator, I have both a syslinux and an isolinux folder. Is that unique to desktop, or should I consolidate both into syslinux?

---

