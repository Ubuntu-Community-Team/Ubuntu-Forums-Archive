---
title: "Dual booting with Windows Vista"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by hypersoar on 2006-06-13
I just installed Windows Vista Beta 2 on my computer. The install went without any problems. I already had Ubuntu on the computer living on a different partition. I re-installed ubuntu after installing Vista, and the partitioning seemed to go without any problems. I gave Vista an NTFS partition, and Ubuntu an Ext3 partion with a 1GM swap, plus one FAT32 partition to share. No error messages showed up, and Ubuntu reinstalled. When I rebooted, GRUB didn't show Windows Vista, just the linux options.

Needless to say, I'd like to be able to boot Windows. Anyone know what's wrong?

---

### Post by DougC on 2006-06-15
I have read that Grub won't work with Vista:

[http://www.theregister.co.uk/2006/04/27/schneier_infosec/](http://www.theregister.co.uk/2006/04/27/schneier_infosec/)

Don't know if that stuffs in the beta though.

---

### Post by stupidkid on 2006-06-15
I remember reading on slashdot that this BitLocker thing is optional. So I would assume you can disenable it somewhere.

---

### Post by EndGame on 2006-06-15
Yes, you can enable/disable bit locker, but at this point that's not the whole picture..........Grub will not work correctly yet with Vista's new bootloader (BCD/boot.mgr). A program called "Vista Bootloader" will be releasing a new version soon which will allow changes to make booting Ubuntu or any Linux easy.

---

### Post by PhoenixP3K on 2006-06-15
Any idea of when such an update might be made available? I want to tri-boot Vista, XP and Ubuntu but for now I'm locked out of my Ubuntu...

---

