---
title: "Installtion Issues | Ubuntu 10.10 Desktop"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by jgdsuresh on 2011-01-09
I have created a Bootable USB Flash Drive (8.GB Sandisk) for Ubuntu Desktop 10.10. Using the same, I have installed Ubuntu on my Notebook Compaq 420, which was already loaded with Windows 7. Ubuntu works great, and I am absolutely fascinated to use it, as I was fed up with the issues in Windows. (Please note that I am a novice as far as Linux is concerned. Long back I have worked with Red Hat Linux and Mandrake)

I have a PC (Intel 865 GBF mother board, Intel Pentium 4 HT 2.6 GHz processor, 2 GB DDR SD RAM, 300 GB Seagate Barracuda SATA, LG DVD Writer SATA, Riva TNT 2 with 32 MB RAM AGP Card, D-Link PCI Internal Modem with Motorola Chipset, Creative PCI Sound Card SBS 100 Live! ) that runs Windows 7 ultimate edition. 

When the system boots from USB, I get the following options:
1.	Run Ubuntu from this USB
2.	Install Ubuntu on a Hard Disk
3.	Test Memory
4.	Boot From first hard disk
5.	Advanced options
6.	Help

I have tried options 1 and 2. Both fail after some time.
The rolling text halts at the following entry:
4.887787] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
At this stage the system stops responding. The Keyboard does not respond.

I request to the Linux Geeks here to help me in identifying the trouble and install Ubuntu on my system. What could be this problem? Is it something related to the hardware? 

Incidentally I have installed Ubuntu on my friend’s system which is much older than mine. 

Kindly help.

---

### Post by oldfred on 2011-01-09
The issue is the video card/driver.

The Riva TNT 2 is older and usually older works, but I do not know about that card specifically.

With the liveCd it was f6 to get to options, yours looks like 5 advanced options. Try nomodeset and see it that works.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by jgdsuresh on 2011-01-09
Thank you OldFred.
I tried nomodeset and it worked.

---

### Post by oldfred on 2011-01-09
If you used nomodeset to install, you will have to use it for your first boot, so you then can install the Nvidia drivers.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.

Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

