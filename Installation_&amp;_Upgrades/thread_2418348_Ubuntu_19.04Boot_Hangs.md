---
title: "Ubuntu_19.04/Boot Hangs"
date: 2019-05-05
forum: Installation &amp; Upgrades
---

### Post by ve3pkc on 2019-05-05
I recently tried to upgrade my Ubuntu 18.04 distribution on my HP desktop to 18.10, but it became corrupted. So I decided to load a fresh 19.04 instead, because I installed it on my Laptop and it worked well (used VMWare). I have a dual boot with windows on my desktop. I installed from a USB stick, and the installation went well. After it was completed it asked for a reboot, and my GRUB menu showed the two windows partitions and the Ubuntu. It booted fine, no problems. Later that day, I tried another boot into windows, fine, then Ubuntu but this time the boot hanged. By pressing "esc" I saw the last entry in the bootup screen "started hold until boot finishes" it was stuck at this. I have seen various issues such as this, but I wonder if it isn't very simple, because with the first reboot it worked fine?
Thanks for your help.

---

### Post by oldfred on 2019-05-05
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 

Have you updated UEFI from HP? Many HP have needed that.

---

### Post by ve3pkc on 2019-05-06
Fred:
Many thanks for getting back to me. I inserted the boot_usb and went into Ubuntu Live. I went through the boot repair process. It worked fine on the first boot, very fast boot! Then on the second attempt, it hung as before with the last entry being "a start process is running for hold until boot process finishes". The paste URL:

[http://paste.ubuntu.com/p/HWtdkRj6Jt/](http://paste.ubuntu.com/p/HWtdkRj6Jt/)

Previously I had a /root partition and /swap partition when I ran 18.04/16.04etc. When I deleted all the Linux partitions, the 19.04 installation used an extended partition. I wonder if this is a problem in my case. Thanks for your help, I will keep digging. Can I access the boot log file from the boot_usb/Live session? Would this indicate what is causing the hold?
BR/JC

---

### Post by oldfred on 2019-05-06
If slow booting see this:
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

That you have older Windows with BIOS/MBR configuration means you just about have to have Ubuntu in a logical partition inside an extended partition.

You can remove the old wubi install. If you had any data in it back that up first. But that would only make some difference to Windows not to Ubuntu.

---

### Post by ve3pkc on 2019-05-08
Tried installing 18.04 that I previously had on the extended partition that setup uses, but it hangs as well. Then I went to what had previously worked, a root partition and swap and that hung with 19.04. Finally tried original setup of root and swap with 18.04 and it works. So I guess my machine does not like the extended partition with either 18.04/19.04. At least I am back up and working.

---

### Post by oldfred on 2019-05-08
Seems a bit strange, they all should have worked the same.
Logical or primary  should not make any difference.
But I now only use gpt partitioning, not old MBR. But Windows in BIOS mode must have MBR, so you cannot change.

Whatever works is always a good solution.

---

