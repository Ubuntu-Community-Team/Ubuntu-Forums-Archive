---
title: "Loading initial ramdisk freeze on new z170 chipset &amp; gtx 970"
date: 2015-09-13
forum: Installation &amp; Upgrades
---

### Post by dominik.mge on 2015-09-13
I recently bought a completely new build based on the intel z170 chipset and have tried installing Ubuntu on this new machine without much luck. I have been able to successfully install Ubuntu 15.04 (burnt Ubuntu DVD) using UEFI (Legacy worked as well but same problem) with almost no changes in BIOS other than insuring the correct boot option priorities. However, when I try to reboot/boot after the installation, I get stuck on the "loading initial ramdisk..." line. I have tried editing the commands in GRUB 2.02 by adding "nomodeset" at the end of the "linux" line as well as before/replacing "quiet splash" with no luck either. I am not able to start Ubuntu in recovery mode. I have tried re-installing Ubuntu using different methods and now even though I have always chosen "override all other operating systems" have 2 types of Ubuntu to choose from in the GRUB -> Advanced Options screen: "Ubuntu, with Linux 3.19.0-28" and "Ubuntu, with Linux 3.19.0-15". I have also tried booting the pc with and without the graphics card. The pc is custom build that I pieced together yesterday. I am able to successfully run "try Ubuntu before installing". I do not plan on a dual boot with Windows - hopefully we can successfully solve this problem together ;) I have been trying to install Ubuntu for the last 2 days straight (Sat/Sun).

The parts in my pc are as follows:

CPU: intel i7 6700k (Skylake)
GPU: Nvidia GTX 970 Turbo
Mobo: Asus Z170 Deluxe
SSD: Samsung 850 EVO (500GB)
HDD: WD 7200rpm (1TB)
RAM: Corsair Vengeance DDR4 4x4GB (2400MHZ)

Please let me know if any more information is required and thank you in advance for any help / suggestions.

---

### Post by grahammechanical on 2015-09-13
The difference between the live session and the session that is trying to load after installation is the live session does not use a proprietary video driver. Whereas, when we tick the box "Install third party software" we get a proprietary video driver. So, if the live session is working fine but things are not working on restart, then I suggest an install without ticking the box "Install third party software."

After installation we can install the third party audio and video codecs by searching in the Ubuntu Software Centre for Ubuntu Restricted Extras. And we can trying installing a proprietary video driver by going to System Settings>Software & Updates>Additional Drivers tab. We need to be connected to the internet and to allow time for the utility to find drivers for us.

How new is the GTX 970? It might be too new for the proprietary video drivers in 15.04. You may need to try your luck with Wily Werewolf (15.10). True it is still under development but release date is just over a month away. I have been using 15.10 development for months. It is stable. And it now has Linux kernel 4.2 and later Nvidia video drivers than 15.04. These are more suited to newer hardware. Just a thought.

Regards.

---

### Post by dominik.mge on 2015-09-27
Hi graham, thank you for your help - my pc works now! I reinstalled the ubuntu on Legacy instead of UEFI, installed Wily Werewolf 15.10 and the Nvidia-352 driver. Everything has been working great. Thank you very much!

---

### Post by piti.diablotin on 2015-10-14
Hi, I plan to buy almost exactly the same configuration as you :  the same mother board and the same graphic chipset Asus STRIX GTX970 4 OC.
I will use this computer for virtual machines as a small private server and as a gaming desktop (also in Virtual Machines)

I will use the KVM/qemu utilitiy for that purpose and I would like to know what is the wifi chipset and if you could tell me if the passthrough thechnology VFIO  is well supported for the wifi and both ethernet card ?
It should just need the VT-d technology which is available on any new core i5/7 6XXXX. 

I used [http://sharadchhetri.com/2014/10/09/install-kvm-kernel-based-virtual-machine-ubuntu-14-04-lts-desktop/](http://sharadchhetri.com/2014/10/09/install-kvm-kernel-based-virtual-machine-ubuntu-14-04-lts-desktop/) for installing KVM/qemu if you want to give it a try.

Thank you in advance for any detail you can provide/test.

---

