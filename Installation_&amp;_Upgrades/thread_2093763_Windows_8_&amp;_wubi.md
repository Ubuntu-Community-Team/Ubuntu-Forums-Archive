---
title: "Windows 8 &amp; wubi"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by LinuxOSUser96 on 2012-12-11
Hi, all!  ):P
Longtime mint/ubuntu user here. So how well does the windows ubuntu installer (wubi) work with Windows 8 (if it works at all)? Anyone had any problems so far?

[LEFT]~ LinuxOSUser96 ;)
[/LEFT]

---

### Post by bcbc on 2012-12-11
It works fine unless you are using UEFI to boot. All new computers with preinstalled Windows 8 are using UEFI. The issue is that Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI).

If you upgraded to Windows 8 and you use BIOS or hybrid UEFI to boot from a MBR partition table disk, it works fine.

---

### Post by 12roby21 on 2013-01-28
> **bcbc said:**
> It works fine unless you are using UEFI to boot. All new computers with preinstalled Windows 8 are using UEFI. The issue is that Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI).

If you upgraded to Windows 8 and you use BIOS or hybrid UEFI to boot from a MBR partition table disk, it works fine.

 As a novice computer user, how would one do that? How can i get my windows to use BIOS? Still stuck.

---

### Post by bcbc on 2013-01-28
> **12roby21 said:**
> As a novice computer user, how would one do that? How can i get my windows to use BIOS? Still stuck.

The amount of effort would make the use of Wubi redundant (it's supposed to be easy).

You'd need to:
1. switch to legacy boot mode
2. format the disk, switching to a MBR partition table
3. use a special tool to remove the leftover GPT data that isn't removed
4. reinstall Windows and restore all data

Instead... just do a normal dual boot. It's a bit new so you might want to do some research, but you can read about it here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

