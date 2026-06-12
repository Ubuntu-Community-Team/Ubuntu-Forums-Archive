---
title: "Installer doesn't recognise current existing partitions"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by epb613 on 2005-11-13
Hey:

I have installed Ubuntu on my laptop at least 20 times over the past year with no problems. Recently, I reinstalled Windows XP SP2 onto my main partition. Afterwards I went to then reinstalled Breezy on one of the other partitions. But upon entering the partitioning part of the installer, it shows that my HDD has no partitions on it. This is not the case obviously as I quit the installer and then booted right back into Windows. Furthermore, when I boot using the Live CD, I access each of my partitions with no problem.

Anybody have any ideas of how I could get the installer to view my current partitions?

Thanks.

---

### Post by tseliot on 2005-11-14
[QUOTE=epb613]Hey:

I have installed Ubuntu on my laptop at least 20 times over the past year with no problems. Recently, I reinstalled Windows XP SP2 onto my main partition. Afterwards I went to then reinstalled Breezy on one of the other partitions. But upon entering the partitioning part of the installer, it shows that my HDD has no partitions on it. This is not the case obviously as I quit the installer and then booted right back into Windows. Furthermore, when I boot using the Live CD, I access each of my partitions with no problem.

Anybody have any ideas of how I could get the installer to view my current partitions?

Thanks.[/QUOTE]

Perhaps the Ubuntu Hoary 5.04 installer worked for you while Breezy's doesn't. 

Install Ubuntu Hoary

then upgrade to Breezy by following these steps:

Type

```
sudo gedit /etc/apt/sources.list
```

Replace the word "Hoary" with the word "[COLOR="Blue"]Breezy[/COLOR]" in the whole document

Save and exit

then type:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

And when it finishes, can restart your computer

---

### Post by az on 2005-11-14
Unless you create an empty partition table with fdisk before installing windows, the windows installer can really screw up the partition table.  It cannot deal well with non-microsoft partitions.

It is not the ubuntu installer's fault.

---

