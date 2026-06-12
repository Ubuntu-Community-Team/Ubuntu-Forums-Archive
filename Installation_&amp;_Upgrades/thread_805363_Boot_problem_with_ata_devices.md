---
title: "Boot problem with ata devices"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by masdaq on 2008-05-23
I have download and installed Ubuntu 8.04 via Wubi on a desktop with Windows Vista already installed.  Installation went fine until reboot.  I have successfully boot and updated, but it hangs more often than it works.  It often hangs on reboot right from the first 'Ubuntu' splash screen.  If I reboot and try the recover option, it works most times, but some does it does not.  I am current 'stuck' now trying to boot.  I am seeing the following message repeatly:

[ <TIMESTAMP?> ] ata2.00: status: { DRDY }
[] ata2: soft resetting link
[] ata2.00: configured for UDMA/33
[] ata2: EH complete
[] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[] ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00:00/a0 tag 0 pio        36 in cdb 12 00 00 00 24 00 00 00   00 00 00 00 00 00 00 00
res 40/00:..:00/00 Emask 0x4 (timeout)

A ubuntu newbie, so if addition information is required, please be explicit.

Thanks

---

### Post by epidemiks on 2008-05-24
I am getting very similar errors after upgrading.
This thread may help you: [http://ubuntuforums.org/showthread.php?t=800232](http://ubuntuforums.org/showthread.php?t=800232)

No joy for me though.

I think i'm going to format ubuntu drive and find my gutsy cd.. that worked.

---

