---
title: "Ubuntu install messed my WinXP HD - Please help"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by Cranio on 2008-07-29
**Please help!**

I've a Toshiba laptop with WinXP and made a [SIZE="3"]big[/SIZE] error.

I was trying to install **Ubuntu Hardy** on an **external drive**, attached via USB (it was actually a SATA drive of another Compaq Laptop, plugged via adapter).

I went on, just to discover that **GRUB had overwritten the laptop's boot record** even if installing the OS on an external disk ... with the external disk detached, GRUB issued an error.

Recovery consoles of WinXP install CD just **didn't recognize** the hard disk!

So I went to downloading **ms-sys** package for Debian Etch and followed the guidelines at [http://ubuntuforums.org/showpost.php?p=4691608&postcount=2]("http://ubuntuforums.org/showpost.php?p=4691608&postcount=2"), using a terminal with the Ubuntu Live CD in the laptop.

I issued the commands in that tutorial, and thought I had the problem solved.. I did a boot, this time WinXP recognized the hard disk, then I got into Recovery Console and issued:

**fixboot**

Then I called **CHKDSK /R**, but it says my C: volume is still not valid...

I've very important data on that disk and I wish not to lose them, but I'm really lost on what to do....

---

### Post by Potatoj316 on 2008-07-29
boot into linux (installed version, not live CD version) and post the output of this command
```
fdisk -l
```
(thats a lowercase L not a number one)

---

### Post by Cranio on 2008-07-29
> **Potatoj316 said:**
> boot into linux (installed version, not live CD version) and post the output of this command
```
fdisk -l
```
(thats a lowercase L not a number one)

Alas, I cannot boot into an installed version. The sort of "fix" I've tried prevents me to boot in the aforementioned Ubuntu installation (the one on the external drive).

Anyway, from LiveCD I issued
```
sudo fdisk -l
```

It says that
a) **/dev/sda** is 160 GB (and it's correct)
b) partition** /dev/sda1** is the only partition, and it's HPFS/NTFS (it should be correct too)

Tell me if you need other info, and, btw, thanks for the fast answer and for the time spent helping me, I appreciate it so much.

I copy the full output:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
[...]

   Device Boot      Start    End    Blocks   Id   System
/dev/sda1  *            1   19457  156288321  7   HPFS/NTFS

```

---

### Post by Potatoj316 on 2008-07-29
ok in the live CD mount all the drives you can and then run the command again.  Also copy and paste the output if possible. If you dont have internet in the live environment try saving the output in a text file and then pasting it here. I need to know what filesystems each uses not just size and location.

edit: and there it is

---

### Post by Potatoj316 on 2008-07-29
ok so have you tried installing grub again?  There are many tutorials avaliable online for how to do this.  Try googling it or searching in this forum.

---

### Post by Cranio on 2008-07-29
> **Potatoj316 said:**
> ok [cut]

edit: and there it is

Yes sorry I had to copy it by hand, and surely you wanted to know also if the disk was bootable, right?

EDIT: ok I'll give a try on reinstalling GRUB... I head of [SuperGRUB]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"), maybe it's worth a try?

---

### Post by Cranio on 2008-07-29
> **Potatoj316 said:**
> ok so have you tried installing grub again?  There are many tutorials avaliable online for how to do this.  Try googling it or searching in this forum.

Now the boot seems simply to hang... no clue...

---

### Post by Potatoj316 on 2008-07-29
how did you install, supergrub or the normal grub install from live CD?

---

