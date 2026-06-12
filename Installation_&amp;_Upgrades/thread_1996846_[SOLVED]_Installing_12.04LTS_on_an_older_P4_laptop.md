---
title: "[SOLVED] Installing 12.04LTS on an older P4 laptop"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by Youngblood52 on 2012-06-04
Last month the 12.04LTS dual-boot installation on my Vista Ultimate dual-core Pentium 4GB Dell Inspiron 1545 laptop went smoothly ... so I decided to dual-boot one of my several old XPPro P4 2.4GHz 1GB Dell Latitude C640s ...

... and found that persistence may sometimes be of value in these endeavors.


The HDD in the C640 is, nominally, 150GB in size, so I repartioned it to 2 Primaries (100GB ntfs & 30GB ext4) and 1 Extended with 2 Logical Partitions (2GB swap & 17GB fat32).

1st Attempt:
I booted via LiveCD, established wireless conx and chose the 3rd Installation Option ("Something Else"?).  I also chose the 2 additional options, the first having to do with the downloading of update software during Install and the second having to do with the D/L of 3rd Party software.

After the Install completed successfully (apparently), I rebooted into XPPro to assure that that aspect was still happy.

I then rebooted with a SysResCD and used Terminal to create UBUNTU.BIN that I then, after rebooting into XPPro, I moved to C:/ and then added to BOOT.INI

I then rebooted, and selected to new "Ubuntu 12.04 LTS" choice ...

... and ended up on a blank screen with:

error: out of disk.
grub rescue>

After researching and applying my new knowledge I found that ... SET told me that SET & PREFIX were properly CFGed and LS could "see" the contents of the root dir ... but no deeper.

I decided that I would try again rather than spend an extended amount of time reading & tweaking.  I wiped the Linux partition.


2nd Attempt:
Same as the 1st except that this time I left unchecked the 2 additional options ("the first having to do with the downloading of update software during  Install and the second having to do with the D/L of 3rd Party software")

This time, after providing a fresh UBUNTU.BIN for the BOOT.INI pointer, I rebooted ...

... into a blank, black screen with a blinking cursor in the upper left corner.

So, once more ... I wiped the Linux partition.


3rd Attempt:
Same as the 1st except that this time I left unchecked the *second* of the 2 additional options.

And everything works as it should and is, apparently, stable.

I am providing this as encouragement for those who may find themselves wrestling with like issues. :)

---

### Post by Paddy Landau on 2012-06-05
How strange. Thanks for sharing.

What you want to do now is fully update your system. You can do this from your Update Manager, or, if you prefer, enter the following two commands in the terminal:
```
sudo apt-get update
sudo apt-get dist-upgrade
```Once you have updated, if you would like to have the third-party software (I recommend that you do), go to the Ubuntu Software Centre and install [Ubuntu Restricted Extras]("apt:ubuntu-restricted-extras").

---

### Post by Youngblood52 on 2012-06-05
Thank you, kind sir!  :)

---

