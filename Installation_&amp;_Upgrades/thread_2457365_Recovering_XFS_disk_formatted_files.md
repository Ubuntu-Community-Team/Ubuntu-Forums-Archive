---
title: "Recovering XFS disk formatted files"
date: 2021-01-31
forum: Installation &amp; Upgrades
---

### Post by jamesknox on 2021-01-31
I loaded Ubuntu on a VM partition (of Windows 10) in order to try and read an XFS-formatted (or so I believe) hard drive.  The drive was in a Linkstation 220DE (JBOD, not as a RAID), and was corrupted by a ransomware attack.  I do not believe, however, that the actual files were encrypted - just "hidden" somehow.  

So, the drive goes on a USB adapter, and I start Ubuntu.  Ubuntu can see all the partitions, but sees zero bytes on each partition (nothing free, nothing used).  Of course, the native Windows cannot read XFS.  So maybe the drive is too messed up to make any sense.  Or maybe it is the fact that Ubuntu is working *through* Windows.  [Ubuntu can see shared folders on Windows drives.]  

Any ideas?  Hopeless?  Or do I just need a particular driver for Ubuntu?

Thanks... jmk

---

### Post by CelticWarrior on 2021-01-31
Welcome.

First of all, very likely hopeless. This is only to set reasonable expectations.

A few things to know/consider. The first is sort of nitpicking (but then it isn't): A virtual machine is not a partition, it's a file. Running Ubuntu as a VM, for the intended usage, makes no difference as long as the virtualization software passes the USB device(s) correctly to the VM. The issue you're having is therefore unrelated to Ubuntu or running it in a VM. It has to do with specific settings of the NAS from where the disk come from.

Warning: Commercial software (shareware)
[https://www.ufsexplorer.com/articles/how-to/recover-data-from-linkstation.php](https://www.ufsexplorer.com/articles/how-to/recover-data-from-linkstation.php)
[https://www.ufsexplorer.com/download.php](https://www.ufsexplorer.com/download.php)

---

### Post by grahammechanical on 2021-01-31
This may help you to confirm that you have the necessary software tools available in Ubuntu.

[https://wiki.ubuntu.com/XFS](https://wiki.ubuntu.com/XFS)

Regards

---

