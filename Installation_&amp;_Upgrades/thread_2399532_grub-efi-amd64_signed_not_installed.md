---
title: "grub-efi-amd64 signed not installed"
date: 2018-08-26
forum: Installation &amp; Upgrades
---

### Post by opaotti on 2018-08-26
at the end of the new of ubuntu 19 I got he message "grub-efi-amd64 signed not installed in /target". The same ocurred at  the installation of the new Linux Mint. Is there somebody who can explain me the reason for that? My machine is a Dell optiplex 7010, which I shortly bought as used after a totally core-meltdown of my old computer during a hot summerday.
Thanks in advance for any answer.

opaotti

---

### Post by oldfred on 2018-08-26
Just to see details, then we can make suggestions on best way to fix:

Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jiruiwu on 2019-03-13
Did you try install from cd/dvd-rom ?
 
I try to install Ubuntu Desktop 16.04.5/17.10/17.10.1/18.10 via PXE Server have same issue.
PS: I use "Erase disk and install Ubuntu" to install, it will create an EFI System partition. So, it's not partition problem.

But If install OS via Internet, it's not found this message.
=> After boot netboot via PXE Server. Under the Live-OS, I try to setting network to connect Internet.
Then click Install to install OS via Internet instead of local PXE Server. This issue was solved.


Refer this: [http://linuxbsdos.com/2017/08/29/solution-to-grub-efi-amd64-signed-package-failed-to-install-into-target/comment-page-1/](http://linuxbsdos.com/2017/08/29/solution-to-grub-efi-amd64-signed-package-failed-to-install-into-target/comment-page-1/)

---

