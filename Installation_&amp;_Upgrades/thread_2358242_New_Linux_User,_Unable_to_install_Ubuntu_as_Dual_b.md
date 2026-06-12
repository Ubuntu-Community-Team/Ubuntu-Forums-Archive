---
title: "New Linux User, Unable to install Ubuntu as Dual boot with Windows 10"
date: 2017-04-11
forum: Installation &amp; Upgrades
---

### Post by saurabhg59 on 2017-04-11
Hi,

I am a new Linux user and am unable to install Ubuntu as a dual boot with Windows 10.

I have created multiple bootables using Rufus, Universal USB installer and Linux Live USB creator.

I have tried using Ubuntu 16.04.02 LTS and 16.10 and get stuck at the same step.

I have tried using the same bootable on a different laptop and it works fine.

The issue is, after I select USB from boot menu, I get the screen with 4 options, 
1. Try Ubuntu without installing
2. Install Ubuntu
3. OEM insall for manufacturers
4. Check disk for errors

If I select option 1 or 2, I get a page saying Ubuntu and 5 dots below it which change to red/white to indicate loading.
At this page the dots will stop changing colors and the system will get stuck. I have tried leaving the system for around 20-30 minutes with no progress. I am unable to proceed from here.
Can anyone please help me.
The system that I am using is ASUS ROG GL552VW laptop with the below specifications
8 GB RAM
Nvidia 960 M 4GB
Intel i7 [COLOR=#212121][FONT=Roboto]6700HQ.[/FONT][/COLOR]

---

### Post by oldfred on 2017-04-11
With nVidia you probably need nomodeset. But your Asus may also need pci=nomsi.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

Once installed, you should only need nomodeset until you install the nVidia driver from Ubuntu repository. Do not install directly from nVidia.

 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

