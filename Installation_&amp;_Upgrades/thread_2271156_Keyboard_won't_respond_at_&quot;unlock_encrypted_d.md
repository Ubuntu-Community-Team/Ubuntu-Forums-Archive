---
title: "Keyboard won't respond at &quot;unlock encrypted disk&quot; screen"
date: 2015-03-27
forum: Installation &amp; Upgrades
---

### Post by opus1 on 2015-03-27
Upgraded from 12.04 to 14.04 by doing a complete re-install from scratch with LVM/encrypted partitions. The USB keyboard works in the BIOS screen and in grub, but as soon as I get to the "Unlock Encrypted Disk" screen, the keyboard doesn't work, rendering the computer useless. If I put in the minimal install cd and go in to rescue mode, the keyboard works. When running the live CD on the system, the keyboard works.

I tried two different keyboards, both USB. I tried using a PS2 adapter on both.  In no case can I get the keyboard to respond at the unlock screen.  

I looked through the forums for the last hour and a half and couldn't find anyone with the same issue, although I did find a bug report at launchpad that looked like the same problem ([https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1066376](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1066376)), but that report says that a fix was released. 

I'm desperate to find a solution because this is the family's main computer.

---

### Post by opus1 on 2015-03-28
I re-installed again from the minimal install CD (like last time), and this time when it came to "Drivers to include in the initrd", I didn't choose "targeted".  That solved the problem for me and I am able to unlock the encrypted disk now.

---

### Post by Vladlenin5000 on 2015-03-28
Nice :p

Please use the thread tools to mark this one as solved.

---

### Post by opus1 on 2015-03-28
Hmm... I marked it as solved last night.  I guess I will try it again.

---

### Post by opus1 on 2015-03-28
I just went to mark it as solved, and the only option I have is to mark it "unsolved"?  Something doesn't seem right here...

---

### Post by Vladlenin5000 on 2015-03-29
It shows SOLVED already. Thank you and happy Ubuntuing.

---

