---
title: "Install ubuntu from a pen drive"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by alessioalx on 2013-02-12
Hi there!

I want to install ubuntu in Fujitsu Amilo Pi 1505 from a pen drive but when I try to boot this error appears:

```
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
Boot: 
```I read [this]("http://pestit.wordpress.com/2012/05/03/error-no-configuration-file-found-ubuntu-from-usb-drive/") article and I tried all solutions but they don't work for me.

Any ideas? :(

---

### Post by C.S.Cameron on 2013-02-12
Check the MD5SUM.

Try a different flash drive installer, say UNetbootin rather than Startup Disk Creator or vice-versa.

If this is one of them new UEFI computers research UEFI or Secure Boot.

Start here:

[http://www.theregister.co.uk/2013/02/11/linux_foundation_uefi_workaround/](http://www.theregister.co.uk/2013/02/11/linux_foundation_uefi_workaround/)

---

### Post by alessioalx on 2013-02-12
I tried different ISOs (12.04, 12.10) and different pen drives. If I try to boot from the pen drive in another notebook it works.

It's an old notebook, it isn't UEFI.

---

### Post by bantuvez on 2013-02-12
Format your pendrive to FAT16 instead of FAT32.

---

### Post by fdrake on 2013-02-12
> **alessioalx said:**
> I tried different ISOs (12.04, 12.10) and different pen drives. If I try to boot from the pen drive in another notebook it works.

It's an old notebook, it isn't UEFI.
is the laptop a 32bit or 64 ?  what about the ubuntu image : i384 or x86_64?

---

### Post by alessioalx on 2013-02-12
I'm trying to install this iso: ubuntu-12.04.1-desktop-i386.
I suppose the notebook is 32 bit.

---

### Post by alessioalx on 2013-02-12
I have just tried with a fedora distribution and the result is the same :(

Any ideas?

---

### Post by bantuvez on 2013-02-12
Have you done what I told you?

---

### Post by alessioalx on 2013-02-12
I try to format it in FAT16.

Attached you can see a screenshot. Is it right?

---

### Post by lordievader on 2013-02-12
Have you tried C.S.Cameron advice? I had a similar problem a few days ago. Made the live-usb with unetbootin, got this error, then I made it with the startup-disk creator and it fixed the problem. I might have switched the software... Can't remember which of the two worked.

Good luck,
-lordievader.

---

### Post by alessioalx on 2013-02-12
Ok, solved formatting pen drive in ext2 ](*,)](*,)

Thanks!!!

---

### Post by bantuvez on 2013-02-12
That wasn't formatted to FAT16 it was still FAT32 ("Tipo: FAT (versione 32bit)")  I dont know what does the other raw try to mean with W95 FAT16 (LBA) . 

But anyway it's good that you figured it out and managed to boot. :)

---

