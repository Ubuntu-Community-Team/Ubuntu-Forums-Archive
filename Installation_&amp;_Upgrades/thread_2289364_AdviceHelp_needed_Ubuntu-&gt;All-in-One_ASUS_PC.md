---
title: "Advice/Help needed Ubuntu-&gt;All-in-One ASUS PC"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by Coder88 on 2015-08-03
Hi, I have installed Ubuntu many times, but now I want to install it to a partition on an ASUS All-in-One PC and would appreciate any tips and how-tos so I do not screw this up. The PC has a single hard drive as Disk 0, 1.8TB, partitioned as follows (the Unallocated partition is what i just created by shrinking the Windows partition):

(C: partitions as shown in Control Panel System Admin Disk tools)
800MB Recovery, 260MB Recovery, 1.7TB Windows 8, 100GB Unallocated, 14GB Recovery

What I want to do is install Ubuntu 14.04.2 that I just downloaded and will burn as iso to a DVD, to install to that 100GB unallocated partition. But what is troubling me is how am i going to have dual boot, where if anywhere should i install the bootloader? And will Windows 8 play nice if the bootloader overwrites the Windows bootloader? I don't want to muck this up. I know there is some sort of bootloader manager that runs on the Windows system, can not recall its name, should I just use it? Other?

---

### Post by SeijiSensei on 2015-08-03
When you get to the partitioning step in the Ubuntu installer, choose "manual" or whatever it is called now and point the installer to the reserved partition.  Tell it to format the partition with ext4 and mount it as /.  When you get to the bootloader step, accept the default which installs grub to the boot record.  When you reboot after installation, you'll get a menu of options that will let you choose to boot Windows or Ubuntu.

---

### Post by grahammechanical on 2015-08-03
The Windows boot loader does not recognise any other OS than a Microsoft OS and until that changes those of us who want to dual boot Windows and Linux have no choice but to overwrite the Windows boot loader with the Linux boot loader (Grub). A way around this would be to have two hard drives - one for Windows and one for Ubuntu.

And there is another thing to consider. If this machine came with Windows 8.1 pre-installed then the motherboard would have an UEFI boot system and Windows would be installed in EFI mode. And that would mean that the Ubuntu DVD should be loaded in EFI mode and Ubuntu installed in EFI mode. Furthermore, there would be a partition for EFI boot files for Windows and that would be the place that the Ubuntu installer would put the EFI boot files for Ubuntu.

You do not mention a "boot" partition. So, there are matters to make clearer.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by Coder88 on 2015-08-03
Well sigh, I successfully installed Ubuntu 14.04 x64 to my 100GB partition, chose to install the bootloader there, rebooted and sure enough GRUB had option to boot into Ubuntu or boot into Windows. All looked great until I noticed there was no wifi, no way to connect to wifi, thus no internet. It gets worse. I figure I will try another distro that might have proper wifi drivers (I mean geesh my ASUS All in One PC is about 18 months old). But my BIOS/PC no longer boots from the DVD drive! I went into the BIOS to choose boot settings and the DVD drive is not even listed anymore as an option for a boot device. I am screwed. Somehow the Ubuntu install did a fubar on (mucked up) my BIOS, removing the DVD drive as a selectable boot device. WTF?!? This is disturbing, I have never seen this happen. Of course I chose defaults (F5 key) in the bios but that changed nothing for boot device options. My DVD drive works as a readable device, it is still listed in the BIOS as a device, it is just not in the drop down list of possible devices to choose for booting from! Looks like I might have to go to ASUS support and find a way to flash my bios to see if i can get it fixed, idk, but this majorly sucks. Like I said, I have never seen this happen before and I have installed linux to desktops and laptops a total of maybe 50 times.

---

