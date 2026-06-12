---
title: "GRUB/Uninstallation worries"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by Yirimyah on 2006-09-18
I've been having issues recently with uninstalling GRUB. I have a desktop with two hard disks, one of which is Breezy and the other being WindowsXP. I want to remove the Windows XP one so that my friend can use it in her computer, but obviously when I simply boot her computer from the WinXP disk it gives me an error #21. (cannot find disk). So what I want to know is: How do I get rid of GRUB on that disk without formatting? I would just format the Ubuntu disk, as I had it backed up, but as is apparent GRUB is also on the Windows HD. As I said, the Windows disk can't be formatted- it has heaps of stuff on it which I don't want to download again.

---

### Post by randell6564 on 2006-09-18
> **Yirimyah said:**
> I've been having issues recently with uninstalling GRUB. I have a desktop with two hard disks, one of which is Breezy and the other being WindowsXP. I want to remove the Windows XP one so that my friend can use it in her computer, but obviously when I simply boot her computer from the WinXP disk it gives me an error #21. (cannot find disk). So what I want to know is: How do I get rid of GRUB on that disk without formatting? I would just format the Ubuntu disk, as I had it backed up, but as is apparent GRUB is also on the Windows HD. As I said, the Windows disk can't be formatted- it has heaps of stuff on it which I don't want to download again.

HI!
OK, let me get this straight. You HAD two HD's on YOUR box, You removed ONE of which houses WINXP, and gave it to your friend for HER box.

After you installed your friends new HD, and tryed to boot, you NOW get the 'error 21'.

IF this is correct then just slip a Windows boot disk into your friends box and do an 'fdisk /mbr'  That should rewrite the Windows boot loader and allow you to get your Windows back!

But NOW what about your Ubuntu?! You know, the HD that YOU kept?
By removing the HD that you gave to your friend, you removed the GRUB boot loader also, correct? So now you can't boot into Ubuntu!

---

### Post by Yirimyah on 2006-09-18
..Close. I *intend* to give the second HDD to my friend, so I can still do stuff with it when it actually boots. So I can do a fdisk /mbr from the windows installation CD? Or do I need to boot?

I don't really care about that Ubuntu: It's breezy, it's backed up, I have dapper on this laptop, and I have a Dapper CD around somewhere. So no worries on that score.

---

### Post by randell6564 on 2006-09-18
> **Yirimyah said:**
> ..Close. I *intend* to give the second HDD to my friend, so I can still do stuff with it when it actually boots. So I can do a fdisk /mbr from the windows installation CD? Or do I need to boot?

YEAH, you could probably repair the Boot loader using the WinXP CD!

OR just get a [win98 boot disk]("http://www.bootdisk.com/") and do it the old way!

---

