---
title: "Kernel problem"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2007-02-23
Hey I have new kernel 2.6.20 and when every time when i boot i get following lines

 PCI: BIOS Bug: MCFG area at f0000000 is not E820-reserverd
 PCI: Not using MMCONFIG

How can i fix this?
I have HP NX7400 laptop.

---

### Post by mid_night gypsy on 2007-02-24
howdy,
 I am having the same message just as the system boots. I have not found the answer,But hope others could help. Note: I'm running Feisty (i386) with no problems....Just that message. Thanks gypsy

---

### Post by john_brown_jr on 2007-03-01
The same message for me (HP nx7400 on 2.6.20)

---

### Post by mid_night gypsy on 2007-03-12
Hello,
 Today, I found a fix to this problem (boot errors). I hope it can help someone else to. What I did was edit /boot/grub/menu.lst and added pci=nommconf noapic to the end of # defoptions= and to the end of # altoptions=....Here is an example (# defoptions=quiet splash pci=nommconf noapic) -( ) your's may be a little diffent. Also add pci=nommconf noapic to the end of kernel(s) line(s).Here is an example (/boot/vmlinuz-2.6.20-9-lowlatency root=UUID=93f61ebf-e7e0-4d12-a03e-6eef85625ca7 ro quiet splash pci=nommconf noapic) I hope this helps Thanks gypsy

---

