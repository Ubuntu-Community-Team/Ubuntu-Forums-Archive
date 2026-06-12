---
title: "Booting 9.10 from USB and initrd.gz missing!"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by Eisenhorn on 2009-12-28
I am trying to make a USB stick that boots Ubuntu 9.10. I created 2 partitions ("usb" vfat and "casper" ext2). Then i donwloaded the iso unpacked it and copied the data to usb part. With syslinux -sf i copied the bootloader to part usb.
Now when i start from USB i come to the ubuntu menu but when selecting Start up a message box comes named "Boot loader" and saying "initrd.gz". I can only find initrd.lz on the 9.10 image? Can anybody help me/ give me a clue why there is no initrd.gz? Can I convert lz to gz with tar or something?

---

### Post by pi.boy.travis on 2010-01-10
> **Eisenhorn said:**
> I am trying to make a USB stick that boots Ubuntu 9.10. I created 2 partitions ("usb" vfat and "casper" ext2). Then i donwloaded the iso unpacked it and copied the data to usb part. With syslinux -sf i copied the bootloader to part usb.
Now when i start from USB i come to the ubuntu menu but when selecting Start up a message box comes named "Boot loader" and saying "initrd.gz". I can only find initrd.lz on the 9.10 image? Can anybody help me/ give me a clue why there is no initrd.gz? Can I convert lz to gz with tar or something?


This one took me WEEKS to figure out.  You need to edit the file text.cfg in the syslinux folder on the root of your usb drive.  Just change any reference to initrd.gz to initrd.ls

Hope this helps!

---

