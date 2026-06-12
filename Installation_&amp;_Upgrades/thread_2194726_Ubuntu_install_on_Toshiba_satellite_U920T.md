---
title: "Ubuntu install on Toshiba satellite U920T"
date: 2013-12-20
forum: Installation &amp; Upgrades
---

### Post by gcampbell2 on 2013-12-20
Hi Everyone, i am having a bit of trouble installing Ubuntu 12.04 on my laptop. I have attempted to install the OS and every time i do i just get "Insert system disk" when the machine starts up. I have been trying to diagnose the issue and think that it may be caused by UEFI. I attempted to fix the issue by running Boot-repair (please see [http://paste.ubuntu.com/6605774/](http://paste.ubuntu.com/6605774/)) but this does not seem to fix the problem.

Can anyone please advise on how i could fix this issue? 

Many Thanks.

P.S I have disabled a number of options in the BIOS including SecureBoot and FastBoot but disabling these has not helped.

---

### Post by tfrue on 2013-12-20
Here is site that might be able to help:
[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[/URL]
Here is another link for a fix:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by oldfred on 2013-12-20
Did you intend to erase Windows?

Is this an Ultrabook. If so you may have to remove the Intel SRT RAID meta-data from the drive.

       Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

