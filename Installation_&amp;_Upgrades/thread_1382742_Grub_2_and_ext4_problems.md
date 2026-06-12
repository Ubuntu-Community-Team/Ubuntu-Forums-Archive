---
title: "Grub 2 and ext4 problems"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by usedvendingmachines on 2010-01-16
Hi everyone

I have been using Ubuntu 9.04 for some time now and am fairly comfortable with it, however I recently tried to upgrade my 3 machines (HP desktop, Packard Bell desktop and Advent laptop) to 9.10 the live CD loads fine and I can install the system but on reboot after installation all 3 systems fail to boot, on the first I just get a flashing cursor, on the second I get the GRUB boot menu, but pressing enter on any selection just reboots the machine and on the third Ubuntu starts to boot but it hangs at the logo.

I assumed it was a problem with my hardware all approx 3 years old and the new Grub 2, so I had planned on swapping back to Grub, but I had read the ext4 which 9.10 uses will not work with this.

If anyone has any ideas, I would be glad to hear them, I would really like to upgrade to 9.10 without buying new hardware, as a last point I also tried Mint 8, which I believe is based on 9.10 and I had exactly the same problems, I even downloaded 9.10 several times and used different blank CD's and burners just incasr there was a problem there.

Thanks in advane for any pointers.

---

### Post by falconindy on 2010-01-16
grub-legacy will support your ext4.

[Source](https://bugs.edge.launchpad.net/ubuntu/+source/grub/+bug/314350)

---

### Post by oldfred on 2010-01-16
Wow, I installed Karmic on two computers that are about 3 years old and had no problems at all. It was so much better than all the upgrades in place I was impressed.

I would first try reinstalling grub2 on the first two machines and the third may be stopping because of a video issue (or it could be anything but video is often the most common). On the third machine did the liveCD work and could you tell if it made any special settings as part of the running of the liveCd?

I would also test using the liveCD and boot using the hard drive as that may bypass grub in the MBR and see if reinstalling grub would help.

---

