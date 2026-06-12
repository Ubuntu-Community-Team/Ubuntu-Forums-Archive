---
title: "How to recover my MSI wind!?"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by jorgb on 2008-11-28
Dear Ubuntu users,

I have a problem I can't really solve I hope an Ubuntu/Linux guru can help me..

I have a MSI Wind U100. It had Windows XP on the second partition. The first partition contains a recovery partition. I installed Ubuntu 8.10 on it and have overwritten the Windows XP partition. No biggie because I wanted Ubuntu. However the touchpath is acting up badly and I want to return it. 

Now comes the problem. The grub bootloader shows me the Windows XP boot partition, I can boot to it but because the partition is now ext3, it cannot restore the Windows XP installation on it. So I thought I would reformat the Linux ext3 partition to NTFS and then boot into the recovery manager so I can return this laptop, but the grub bootloader dies because it can't find /boot/grub/menu.lst which is understandable. 

So I am at a loss. What to do? I have no portable DVD player (too expensive) but I need to restore that laptop so I can return it. My idea is to put grub and the whole boot loader + files on a seperate partition that is still alive when I format the primary partition to let the restore tool do it's work

Any thoughts on this predicament? Thanks in advance!
- Jorgen

---

### Post by damis648 on 2008-11-28
I would download and boot [Super Grub Disk]("http://www.supergrubdisk.org/"). It will allow you to boot from the medium of your choice. Boot from this CD, and then navigate through to boot from the recovery partition.

---

### Post by jorgb on 2008-11-28
Thank you damis648, I will try to do that and see if I am able to boot from my Windows with a USB disk, if so my days is made! 

Regards,
- Jorgen

---

