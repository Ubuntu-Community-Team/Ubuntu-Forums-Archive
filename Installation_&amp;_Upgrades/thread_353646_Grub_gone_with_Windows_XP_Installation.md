---
title: "Grub gone with Windows XP Installation?"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by WardLoockx on 2007-02-04
I have one sata-2 drive with three partitions
[LIST]
[*]Swap
[*]Ext3 Linux Partition
[*]NTFS Windows Partition
[/LIST]

First I installed Ubuntu and afterwards I created the NTFS partition in linux to install my XP. But when it had been installed it only booted windows xp and didn't had access to Grub. Can I Fix this problem?

---

### Post by pay on 2007-02-04
Yes its fixable. You need to reinstall grub using the live cd. ```
grub-install /dev/hda
```Might help without going into detail. For more detail try the [Gentoo Handbook](http://www.gentoo.org/doc/en/handbook/index.xml). It will tell you howto do it.

---

### Post by Kateikyoushi on 2007-02-05
It is a common issue, there is a thread about it in the forum. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

