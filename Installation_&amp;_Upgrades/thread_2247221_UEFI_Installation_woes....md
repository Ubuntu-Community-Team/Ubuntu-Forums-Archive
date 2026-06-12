---
title: "UEFI Installation woes..."
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by jochen-blacha on 2014-10-06
Hi!

I have a rather strange "Installation" problem with Ubuntu 14.04.1 and UEFI...

Before I dig into the actual problem there's one thing I'm curious about, because I can't figure out why it doesn't want to work:

When I tried installing Ubuntu onto a USB 3.0 connected SSD (Crucial M500 240GB in a Sharkoon QuickPort XT dock connected to a Gigabyte 990FXA-UD3) the installation actually works (grub was written to the MBR of the SSD to "dual-boot" via the firmware boot-menu therefore keeping it from messing about with Windows Loader) but upon trying to boot the installed system all that happens is that the drive just "sits there" doing some I/O for some prolonged amount of time (~20 seconds?) until grub throws a "Attempted to read beyond partition boundaries" error back. Funnily enough, it works once the drive is connected to a USB 2.0 port, but that leaves more transfer-speed to be desired. Any chance Linux not yet being able to fire up itself from a USB 3.0 drive?

Anyway, back to the UEFI problem (the SSD is now internally connected to the SATA ports)...

I created the partitioning according to the Wiki (BIOS data area, grub area, boot partition, root partition, home partition, swap) and am able to successfully install Ubuntu. After the installation is done it boots up just fine (the firmware's boot-menu even shows me "ubuntu" instead of the device identifier) ... BUT ... once I let it install a kernel update it self-destructs. This means that upon re-boot grub will throw an error about not being able to load the kernel and call it a day. Even manual intervention (messing about with that pile of grub - sorry, I don't like grub at all, never had) doesn't get the system to boot again.

Setting the firmware (BIOS) of the motherboard to activate "Legacy BIOS support", re-partitioning and re-installing in a classic MBR scheme (just boot, root and swap partitions) works just fine (not really to any greater surprise when we "fake" a legacy BIOS system).

Any thoughts why the system "self-destructs" when running UEFI exclusively and how to rectify the problem?

---

### Post by Vladlenin5000 on 2014-10-06
Hi, welcome.

It could be a kernel update or something else. Really hard to tell right away. Perhaps the logs have some clues?!?

---

### Post by oldfred on 2014-10-06
It would be better to see the summary report from Boot-Repair to know how system is configured.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some systems need extra settings:
      
 IOMMU for USB3 ports Gigabyte board
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Linux kernel enable the IOMMU &#8211; input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)

---

### Post by jochen-blacha on 2014-10-06
> **Vladlenin5000 said:**
> Hi, welcome.

Thank you.

> **Vladlenin5000 said:**
>  It could be a kernel update or something else. Really hard to tell right away. Perhaps the logs have some clues?!?

Well, there's the problem. The installation of the kernel updates ("Update Manager" window expanded to see the console output - referring to the linux-* packages that get installed) goes without a hitch, there's not a single error that would give a clue about why it fails too boot at re-boot.

Since it doesn't boot anymore (just the grub error about not finding the kernel image) there are no usable logs... if it would crash during boot there would at least be something to work with.

> **oldfred said:**
> It would be better to see the summary report from Boot-Repair to know how system is configured.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Okay, will do a UEFI-reinstall (currently a "Legacy BIOS" install) tomorrow and see that I get you that log.

> **oldfred said:**
> Some systems need extra settings:
      
 IOMMU for USB3 ports Gigabyte board
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Linux kernel enable the IOMMU &#8211; input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)

The IOMMU problem in relation to AMD "FX" CPUs, does not longer exist (AMD FX8350 on a Gigabyte GA-990FXA-UD3 running the latest and greatest firmware). On Ubuntu 12.04.x the system would go totally wonky when not having "iommu=pt" passed to the kernel (tons of repeating errors in the syslog with the Nvidia proprietary driver, not really a problem with "nouveau" (which I don't consider 'being ready as a daily driver)). With 14.04(.1) the system works fine with the default "Lazy I/O TLB flush" behaviour (no more errors with the Nvidia driver, and I never had the NIC problem anyway).

The only thing I needed to fix, that includes passing arguments to the kernel, was plymouth, which still fails to play nicely once you resort to using "teh evil" Nvidia (or ATI for that matter) proprietary driver.

Anyway, like I wrote above I'll re-try a UEFI install and get you guys the logs; though I doubt there's anything of real value as the actual package install goes through fine and with grub no longer booting there's no boot/syslog to work with.

---

### Post by jochen-blacha on 2014-10-06
Also, for what its worth, I'm able to replicate the problem with VirtualBox (just finished the evaluation test)...

Windows 7 SP1 x64 Host OS (same base hardware) with latest VirtualBox, Ubuntu 14.04 amd64 "desktop" install ISO (the source out of which I created my USB stick for real metal installation), VM set to EFI (I know, experimental and not exactly the same as UEFI), 8GB RAM, all 8 cores and uncapped, Nesting and IOMMU enabled, 120GB virtual HDD, 128MB framebuffer and acceleration enabled, ICH9 emulation, Intel HD Audio emulation, virtual hard drive AND virtual DVD drive bound to a SATA controller (took out the PIIX4 controller and re-attached the DVD drive emulation to the SATA Port 1).

I boot off the ISO, do the same as I did on the real iron (efi data area partition, grub data partition, boot partition, root partition, swap (RAM*2), no /home for this test), install Ubuntu, reboot, install VBox guest additions, reboot, install the kernel updates, reboot, and... VBox jumps into the EFI console instead of loading grub.

This ends in the about the same result... nuked install once the kernel updates got applied (though on the real iron it doesn't jump into the UEFI console but shows me grub complaining about not finding the kernel image).

This looks somewhat weird... the VM is by no means the same thing as the real iron, but it ends in the same dead end.

Leads back to the question: Do i do something wrong, or is there a fundamental problem once the kernel updates get applied?

---

