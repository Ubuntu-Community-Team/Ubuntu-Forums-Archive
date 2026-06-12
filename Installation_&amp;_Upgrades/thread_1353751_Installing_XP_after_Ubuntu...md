---
title: "Installing XP after Ubuntu.."
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by mustangzach on 2009-12-13
Okay, here's the deal. I have Ubuntu 9.10 as the main OS on my lappy.

There's a game I want to play that works under XP, but no matter what I try, I cannot get to work on Ubuntu. Sooo..

How can I install XP to the 15GB I have unpartitioned on my drive, without messing up GRUB? I want to use GRUB, not NTLDR, just use GRUB to pass everything down to NTLDR to load XP, just as it would regularly? Will I have to install GRUB again after installing XP?

Thanks in advance guys.. I just want to play this game lol :P

---

### Post by Megaptera on 2009-12-13
Hi,
Is this step by step guide with screenshots any help?

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by kellemes on 2009-12-13
[All you need to know.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Easiest method described is using [Super Grub Disk]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using%20the%20Unofficial%20%22Super%20Grub%20Disk%22").

---

### Post by wilee-nilee on 2009-12-13
> **kellemes said:**
> [All you need to know.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Easiest method described is using [Super Grub Disk]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using%20the%20Unofficial%20%22Super%20Grub%20Disk%22").

Super grub doesn't recognize ext4.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Install the XP in a virtual if you have enough ram.

---

### Post by sliketymo on 2009-12-13
Have you checked to see if the game is available,or supported under wine?

---

### Post by phillw on 2009-12-13
> **Megaptera said:**
> Hi,
Is this step by step guide with screenshots any help?

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

+1

Although it will hose your Grub2 as it is written for Grub legacy.  -- to recover Grub2 head over to -->[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  to have them living happily ever after.

Regards,

Phill.

---

### Post by Megaptera on 2009-12-14
My apologies!!

---

