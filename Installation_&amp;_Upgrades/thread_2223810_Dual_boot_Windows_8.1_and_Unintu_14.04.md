---
title: "Dual boot Windows 8.1 and Unintu 14.04"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by Anny_Hsu on 2014-05-13
Hi everyone!
I'm trying to dual boot Ubuntu LTS 14.04 (x64) alongside my Windows 8.1 (x64). 
I successfully install Ubuntu but there's a problem booting it. 
I install boot-repair, and here comes the error: [http://paste.ubuntu.com/7455939/](http://paste.ubuntu.com/7455939/)

Anyone knows what's the problem and how I could fix it?
I appreciate your help. Thank you!

---

### Post by oldfred on 2014-05-13
It looks like you originally installed Ubuntu in BIOS boot mode as you have grub2's boot loader in the protective MBR.
But now you have grub in the efi partition.

Can you boot an ubuntu entry from UEFI menu or one time boot key?

What model Dell?

Did you leave Ubuntu suspended? Swap says it is swsuspend?

---

