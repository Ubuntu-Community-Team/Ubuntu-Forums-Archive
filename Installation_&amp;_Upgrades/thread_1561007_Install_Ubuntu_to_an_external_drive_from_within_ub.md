---
title: "Install Ubuntu to an external drive from within ubuntu"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by techxcell on 2010-08-25
Hey Guys! I need to know how, if I even can, install ubuntu to a disk (other than the active one, internal or external) from within Ubuntu.

Say I am running Ubuntu Desktop. It is attached to the Internet. The system is fully operational, and now I want to install ubuntu-minimal onto an HDD attached via the USB.

How do I go about it? Even if someone can tell me a way to initiate the installation of a specific package (like just ubuntu-minimal) would be highly appreciated.

Thanks!:popcorn:

---

### Post by oldfred on 2010-08-25
You can directly boot an ISO from your hard drive with grub2 and a loopmount entry that you can add to 40_custom.

Direct boot on drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO](http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO)

Be sure to use the advanced button during the install so you install the grub2 boot loader to the external drive.

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

External is just another drive so this is a good site to review.
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by techxcell on 2010-08-25
Thanks a lot @oldfred. Gonna check the links now. And I WILL remember to mark the thread as SOLVED :)

---

