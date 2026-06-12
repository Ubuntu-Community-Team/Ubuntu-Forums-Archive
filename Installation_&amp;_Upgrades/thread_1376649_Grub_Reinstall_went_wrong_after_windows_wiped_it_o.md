---
title: "Grub Reinstall went wrong after windows wiped it out."
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by Sicarius1 on 2010-01-09
Hello,

Some days ago I decided to reinstall windows, of course windows wiped Grub of the MBR. No problem. I booted of the live CD (9.10) and tried to reinstall grub, I had Ubuntu 9.10 installed before windows wiped grub. I tried the following tutorial:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

My fdisk -l output is the following:
root@ubuntu:~# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f2962

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2675    21486906    7  HPFS/NTFS
/dev/sda2            2676       37638   280840297+  83  Linux
/dev/sda3           37639       38792     9269505   83  Linux
/dev/sda4           38793       38913      971932+  82  Linux swap / Solaris

sda3 is my root partition, sda2 is the partition where all my media files are located.

I mounted /dev/sda3 to /media/root  and then I tried to reinstall grub with:
sudo grub-install --root-directory=/media/root /dev/sda

It came out with no errors, and then I restarted my computer.
Grub started, but with a command line. It was the 1,97 beta-4 version.
Since I'm quite unfamiliar with GRUB (or really technical linux stuff)
I don't know what to do.

Any help would be really appreciated!

Best regards,
Niels

---

### Post by oldfred on 2010-01-09
That should have worked.

Can you manually boot using the command line?
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

scroll down to this heading for detailed instructions
**[B][SIZE=2]U[/SIZE]**[SIZE=2]sing CLI to Boot[/SIZE][/B]



Then reinstall again from your system.

---

### Post by kansasnoob on 2010-01-09
I think it would possibly save us a lot of time to see the output of the Boot Info script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Sicarius1 on 2010-01-09
sorry kansasnoob I didn't know that, anyway it worked. I can now enjoy a fully working Grub :) thanks everybody! You are the best!

---

