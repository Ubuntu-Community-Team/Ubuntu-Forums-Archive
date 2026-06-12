---
title: "Grub2 issue: Unable to boot Mint 19 with LVM and LUKS filesystem"
date: 2018-12-30
forum: MINT
---

### Post by linuxnutt2 on 2018-12-30
I've managed to foobar my system. It will not boot anymore. I've restored a TimeShift Image. The OS is Mint 19 with cinnamon desktop with a standard install  tooking defaults, and at disk configuration (no custom partitioning just defaults)  I choose whole disk encryption with LVM. I did not encrypt the home directory. I need help booting Mint19 with LVM and LUKS filesystem. I have LVM VG mint-vg, LV root as ext4, LVM VG mint-vg, LV swap_1 as swap, and partition #1 of scsi1 (0,0,0) (sda) as ESP. 

Its been a week now working on trying to get my system to boot after restore searching google, Mint forum, and Ubuntu forum for a solution. I think I understand somewhat the issue but I'm having trouble figuring out what I need to do on grub console to boot the system. I do not know what syntax I need to use at the grub editor to get it to boot. I have a one disk instill, sda with Mint 19 installed using LVM and LUKs, but somehow can not make grub2 boot Mint 19. I'm a little paranoid to do something wrong to the system, very conflicted with the next steps. Need some guidance and assistance here. 

I have a Lenovo Thinkpad W530 laptop. When I boot it drops me into Grub2 console version 2.02 black screen, like this
+Ubuntu
Advanced options for Ubuntu
System Setup

If I choose "Ubuntu" or "Advanced options" (will let me choose a kernel to boot), but both fail to connect to lvmetad, and it can not find volume group "mint-vg". It falls back to device scanning and eventually drops me into a Busybox v1.27.2 shell. 

I have tried to use Ubuntu and Mint documentation reinstalling Grub 2 / Fixing s Broken System,
Boot-Repair via Mint 19 Live CD. I've included Boot-Info Summary. 
  pastebin:
[https://paste.ubuntu.com/p/mRtPkBfNMc/](https://paste.ubuntu.com/p/mRtPkBfNMc/)

I would appreciate any help here to fix my boot problem. Please be specific with the commands  that I need to use for this fix. 
Let me know what further information you need from me to fix my situtation.

Thanks,

---

### Post by QIII on 2018-12-30
Moved to ***MINT***

---

### Post by oldfred on 2018-12-30
Do not know LVM, nor Mint.

Boot-Repair's report looks ok. But for Boot-Repair to fully work you have to manually mount the encrypted LVM and give the pass phrase so it can see kernel & details.

If you are getting grub menu, you normally are beyond grub issues.
You may need kernel boot parameters in grub for system to fully boot.
What video card/chip? 

In advanced options can you boot recovery mode?

---

