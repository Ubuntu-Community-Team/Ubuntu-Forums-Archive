---
title: "Unbootable after upgrading to Kubuntu 24.04"
date: 2024-05-22
forum: Installation &amp; Upgrades
---

### Post by genderneutralnoun on 2024-05-22
Hi. It's what it says in the title. I've basically spent all morning trying to troubleshoot this by myself, and I'm at my wit's end. I tried using boot-repair and got a paste to share: [https://paste.ubuntu.com/p/h4xD6bkMgJ/](https://paste.ubuntu.com/p/h4xD6bkMgJ/)
The troubleshooting steps I took:
Found a bug report about being unable to boot with the 6.8 kernel.
Tried booting with the 6.5 kernel, succeeded.
Followed the steps in the bug report for setting the older kernel to boot automatically; installed the 6.7 kernel with mainline, changed the grub menu with grub-customizer.
Restarted.
Booted with the 6.7 kernel, succeeded.
Shut down in order to bring my laptop back upstairs where I can be more comfortable.
Attempted to boot with the 6.7 kernel. Failed.
Attempted to boot with the 6.5 kernel. Failed.
Some other stuff I don't really remember, including trying using boot-repair.
Right now I can only boot by choosing recovery mode, then continue boot as normal, and *only* with the 6.5 kernel.
Any help would be greatly appreciated.

---

### Post by eduardp2 on 2024-05-23
Surely it is not related, but just in case it gives you some clue: In my case, after updating, no grub appears at the wake up of the system BUT in some cases, after a while, the system starts up.
New kubuntu 24.04 shows me Nvidia GPU as GPU2.
So, added the two together, I assume new GRUB is detecting the CPU's eGPU and sending its message through it.
I suppose I can solve it disabling the eGPU from BIOS.

---

