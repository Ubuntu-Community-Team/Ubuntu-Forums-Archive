---
title: "Installer not finding Hard Drives"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by indym79 on 2010-01-21
I am attempting to install on a HP ML110 box.  It has 2 SATA drives installed.

From the live cd I can do fdisk -l and see both drives, I can see both from GPated but during the actual install it doesn't see any drives in which to install.

---

### Post by Chrisn02 on 2010-02-05
I had the same trouble too with a different pc yesterday.  

Found this.
[http://ubuntuforums.org/showthread.php?t=1311512&highlight=ubuntu+install+shows+-hard+drives&page=2]("http://ubuntuforums.org/showthread.php?t=1311512&highlight=ubuntu+install+shows+-hard+drives&page=2")

1) Boot into Ubuntu 9.10 using LiveCD (without installing)
2) Open Terminal and run sudo apt-get remove dmraid or remove using the Synaptic Package Manager.
3) Start the installer by double-clicking on its icon on the desktop

Might be the same for Xubuntu.

---

