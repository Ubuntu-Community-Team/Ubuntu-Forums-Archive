---
title: "Dual boot on 2 HD"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by mac173 on 2012-09-05
I have installed Ubuntu on a second hard drive. The HD had WIN8 on it, but I replaced it with Ubuntu. The problem is that when I boot up, I get the Win7 bootloader, and it does not show Ubuntu. I see "Window's installer" and "Windows 7". If I pick window's installer, it fails. Apparently the installer is still on the boot partition. 

How do I get Ubuntu onto the Win 7 bootloading screen?

---

### Post by oldfred on 2012-09-05
Grub may have installed to the other drive. Try changing in BIOS to boot Ubuntu drive or try one time boot key - f12 on my system.

Windows often combines boot files into the first install,  which can cause issues if you remove one install. Windows will not boot Ubuntu. But ideally you want to keep the Windows boot loader on the Windows drive and the grub2 boot loader on the Ubuntu drive. Then each drive works without the other and in an emergency or hard drive failure you have another system to boot.

If booting other drive does not work, download this into liveCD/USB and post link to BootInfo.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by mac173 on 2012-09-06
Boot Repair did the trick. I really wish the installer could get this right. Every distro I have ever tried, from Red Hat 6.0 to now, has needed tweeking to get the dual boot working. I have always said that the difficulty in getting dual boot to work, and to get the system set up (todays distros are MUCH better) is what kept the desktop from being more popular. 

Thanks for the help on that, my machine is booting correctly now.

---

