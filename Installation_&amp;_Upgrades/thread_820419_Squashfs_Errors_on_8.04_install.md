---
title: "Squashfs Errors on 8.04 install"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Arador Aristata on 2008-06-06
Hi everyone

I downloaded the ISO for Hardy today and ran home to write a Disk. Once this was done I set my boot order and it booted from the CD.

Upon selecting install it took a few minutes at the Ubuntu start up screen and finally that went away to be replaced with a screen full of errors that kept running.

Unfortunately I did not write the exact wording down but it looks something like this

[170.234] SQUASHFS ERROR: Could not read from block ###########
[170.235] SQUASHFS ERROR: Could not read from block ###########
[170.236] SQUASHFS ERROR: Could not read from block ###########
[170.237] SQUASHFS ERROR: Could not read from block ###########
[170.238] SQUASHFS ERROR: Could not read from block ###########

This kept running at some speed as the number on the left increased. I left it for a few minutes but this just continued.

My Specs:

Intel Core 2 Duo 2.3GHz, 1333Mhz FSB
Intel Pearl Creek Classic Board
2048MB Hynix DDR2 800
Geforce 8600GT, 512MB DDR3
500GB Western Digital SATA II drive partitioned as follows:
[80GB-Windows XP Pro][40GB Reserved for Ubuntu][380GB Data Drive]

Please could you help me?

Thank you
David

---

### Post by mxg01 on 2008-06-06
It looks like an issue with your CD. Did you check the MD5 sums on the ISO before burning it? Also it's worth burning the CD at a slow speed like x4 or less.

---

### Post by Arador Aristata on 2008-06-06
I have checked the disk yes and I have checked the MD5 sums. I tried putting in the "all_generic_ide floppy = off irqpoll" option and that gave me mixed results. The first time it booted up and allowed me to start the installation. But when it came to loading the disk partitioner it say "Can not run gnome-session-save -- kill" and hung.

The next time I tried it it just hung while loading the files directly after I selected installation.

Please, if anyone has an idea what else it can be, let me know.

---

### Post by Arador Aristata on 2008-06-06
I spoke too soon. Even if the MD5 and disk check succeeded, writing the disk at 4x solved my issue. Thank you.

---

