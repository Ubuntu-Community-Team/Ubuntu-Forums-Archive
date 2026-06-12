---
title: "Problems with Smart Boot Manager"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by Kossatsch on 2004-10-26
I read [this](http://www.ubuntulinux.org/support/documentation/howto/SmartBootManagerHowto/view?searchterm=smart) about PCs that are not able to boot from CD and successfully installed SMB on a floppy.

The big problem is that SMB does not recognize my CD-ROM.

Any alternatives to SMB or suggestions to make SMB recognize the CD-ROM?

---

### Post by jdong on 2004-10-26
What kind of CDRom drive is it? IDE?

---

### Post by Kossatsch on 2004-10-26
It is SCSI.
TOSHIBA DVD-ROM SD-M1401

---

### Post by Kossatsch on 2004-10-27
[QUOTE=Kossatsch]It is SCSI.
TOSHIBA DVD-ROM SD-M1401[/QUOTE]
 I now tried several things, but without success.
Booting form ZIP would be possible. Any hint to follow this way?

---

### Post by bugmenot on 2005-02-01
This is a bug with libparted. Unfortunately, it's still not completely resolved.

Here is a link to the bug: [https://bugzilla.ubuntu.com/show_bug.cgi?id=2737](https://bugzilla.ubuntu.com/show_bug.cgi?id=2737)

---

