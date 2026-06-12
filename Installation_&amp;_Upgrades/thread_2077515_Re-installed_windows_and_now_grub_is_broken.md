---
title: "Re-installed windows and now grub is broken"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by austinb82 on 2012-10-28
Hi, I have an Acer netbook that I dual installed ubuntu along with windows. I am getting ready to sell the netbook in the near future so I wanted to uninstall ubuntu and reinstall windows. Since the netbook does not have a cd drive acer put a recovery partition on it and I used the "Acer eRecovery" program to restore windows to factory defaults. However, after doing so when I try to boot from the HDD I get an error message stating "error: no such partition." and on the next line it says "grub rescue>" and it has a command prompt with the blinking dash. I tried uninstalling grub and restoring the windows boot loader by creating an MS-DOS Boot disk on a flash drive and typing the "fdisk /mbr" command and it didn't work. I then made the flash drive into a windows vista setup disk and went used the repair feature to load the command prompt and typed "Bootrec.exe /FixMbr" into the vista command prompt. It said the operation completed successfully but when I restarted the computer and removed the flash drive I was still getting the "error: no such partition." message. Does anyone know how to fix this to get my computer back into a state where it can boot from the HDD? Thanks.

---

### Post by Frogs Hair on 2012-10-28
You can start here and I know there are more related links. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

