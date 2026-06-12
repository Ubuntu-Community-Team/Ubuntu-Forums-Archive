---
title: "Installing multiple Ubuntus ... will this work?"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by dryder on 2008-02-01
Hi,
I have 5 HDD's.

One disk for Windows OS and another disk for its programs and data, two other drives are used for special needs.

When I installed Ubuntu some time ago (edgy?) I unplugged all the disks except a disk for Ubuntu - since upgraded to Feisty the same way. It has the usual /boot, /home, /swap and a /my-graphics. This way Windows MBR  knows nothing of Ubuntu Feisty and  Ubuntu grub doesn't know about Windows. Ubuntu Feisty 32 bit is the default boot drive.

As  I have a spare hard drive and my processor is 64 bit I want to install on this drive a 64-bit Ubuntu to try it out. So that neither Ubuntu know about each other and to also keep it unknown from Windows I was going to unplug all other drives when I installl it.

I can manually boot to any drive I choose so could manually choose to boot from the drive with the 64 bit installation when I wanted, the default remaining unchanged. But I was wondering if, once all the drives are plugged back in, having two /boot, /home and /swap partitions on different physical disks would cause problems, even though one set is 32 bit and the other 64 bit?

Any help would be appreciated - thanks.

David

---

### Post by confused57 on 2008-02-01
> I can manually boot to any drive I choose so could manually choose to boot from the drive with the 64 bit installation when I wanted, the default remaining unchanged. But I was wondering if, once all the drives are plugged back in, having two /boot, /home and /swap partitions on different physical disks would cause problems, even though one set is 32 bit and the other 64 bit?

No, it shouldn't be any problem...since you unplugged the other drives when you install 64-bit...the 32-bit and 64-bit installs won't know the other exists.

---

### Post by dryder on 2008-02-01
confused57
many thanks.
David

---

