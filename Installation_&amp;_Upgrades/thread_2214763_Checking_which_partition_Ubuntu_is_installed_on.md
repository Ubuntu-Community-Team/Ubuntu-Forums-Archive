---
title: "Checking which partition Ubuntu is installed on"
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by Vincent_Siu on 2014-04-03
Hey guys, So I've installed Ubuntu 12.04 alongside windows 8 on my labtop, and it just isn't working out, I can't use it at all, so I want to uninstall it and try a different version. Biggest problem though: how to find out which partition ubuntu is installed on? (I didn't use WUBI to install ubuntu, I used this method [http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)) 
I attached a picture of the disk manager (I know for sure that it's not OS or DATA or Recovery.) and the disk stuff

---

### Post by ajgreeny on 2014-04-03
Your ubuntu install is on sda6 according to the **df -h** output.  I think in the Windows disk management it is drive H:, though I have to admit a dislike of the way windows detects and describes partitions as it is a bit meaningless for Linux filesystems.

You probably also have a swap partition but I can not be sure about that, nor which partition it is, so the output of command **sudo parted -l** in terminal would also be useful.

---

