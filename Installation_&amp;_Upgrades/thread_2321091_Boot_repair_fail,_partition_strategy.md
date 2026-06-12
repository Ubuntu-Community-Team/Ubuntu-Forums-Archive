---
title: "Boot repair fail, partition strategy"
date: 2016-04-20
forum: Installation &amp; Upgrades
---

### Post by plotor2 on 2016-04-20
[COLOR=#000000][COLOR=#000000]I bought a new laptop yesterday, a MSI GS60 Ghost Pro-002 with a Core i7 (6700HQ 2.60 GHz) and an Nvidia Geforce GTX 970M, 128GB SSD and 1TB HD. Came installed with Windows 10 obviously, and for the sake of trying, I figured I would dual boot this machine instead of wiping Win10 off completely. I got last nights build of the amd64 install of 16.04 and got it installed to a few different (new) partitions[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000].  [/COLOR][/COLOR]After installation, no grub menu, boots to Windows. boot-repair utterly fails, but I ultimately fixed the boot order in BIOS settings.

After the install completed, the laptop rebooted, and went straight to Windows, no GRUB menu appeared. When I was doing the installation, I chose custom settings, because I wanted / mounted on a SSD partition, but I wanted /home mounted on a new partition on the HD. It asked where I wanted the boot installation, and I chose the SSD device, but not a specific partition (wasn't sure what the best option was tbh). So I was able to pull up the boot menu by holding F11 at the MSI logo before Win10 launches, and choose the ubuntu partition, and launch GRUB. I figured the smart thing to do would be to install and run boot-repair. However, it would always get up to the step that says "Unhide boot menu. This may take several minutes" and effectively hang. Progress bar stopped, and I couldn't even open the System Monitor to see what the CPU was up to. In the end, I fixed it by going into the BIOS and promoting the Ubuntu partition above the Windows partition.  Although this fixed it, I don't understand why boot-repair failed.

I wasn't sure about my partitioning strategy, especially since Win10's is so complicated to begin with. But I basically carved out about 24 Gigs of the SSD for the root installation, and about a third of the HD for the ext4 /home mount partition (and another 4GB for swap).  In case I decide to factory reset and reinstall Ubuntu, is there a different partition strategy that I should try?  Is there any way to diagnose why boot-repair failed to work?  Thank you.

---

### Post by oldfred on 2016-04-20
You have several threads.
We do not want the same issue in multiple threads.
But do want different issues in different threads.
Not sure but they seem related?

Post link to summary report from Boot-Repair.
Did you install Ubuntu in UEFI boot mode? Above report will confirm.

---

