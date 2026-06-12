---
title: "UEFI Boot Problems"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by linthusiast on 2011-10-10
Hi, I've spent the last few days trying to get my machine with an Asus P8P67 (rev 3.1, B3) that has UEFI firmware to automatically boot Natty 64 bit successfully. To simplify matters, I have a single 64GB SSD, with no other OS and no intention to install any OS apart from Ubuntu.

I installed Ubuntu on the SSD. Before installation I manually created the following partitions:
1) 200MB FAT16 (EFI, /boot/efi) a.k.a. /dev/sda1
2) 55GB approx (ex4, /) <-- my root partition a.k.a. /dev/sda2
3) 8GB approx (swap) a.k.a. /dev/sda3

I instructed Ubuntu to install the bootloader to the EFI partition. The installer completed installation and requested that I remove the USB drive and press [enter]. Pressing [enter] did nothing, so I manually rebooted the machine. I accessed my EFI settings on my motherboard and noticed a new "ubuntu" entry along side my SSD as the only positive boot options. The "ubuntu" entry was flagged as UEFI, while my SSD was not. I set ubuntu as my primary boot option and rebooted and all I got was a purple screen with no further reading from my SSD.

I manually rebooted, and attempted to boot my live USB so I could at least get shell access. After several unsuccessful attempts to boot the live version, I got in and removed grub-pc and replaced with grub-efi-(the 64bit version) & efibootmgr. I rebooted my machine and it still failed to boot in to Ubuntu on my SSD. Still with the blank purple screen and nothing else.

So upon reboot instead of accessing my UEFI settings, I can simply press F8 to bring up a list of boot options. "ubuntu" is in that list and when I select it I can boot straight in, but when I select "ubuntu" as my primary boot option in my UEFI settings, I simply get a purple screen and it doesn't work. Right now I am in Ubuntu on my machine after pressing F8 and manually selecting "ubuntu" as the boot option. When I power on the PC, it won't boot up on it's own, so my only option is to manually press F8 and select "ubuntu". This has been working for me for the past few boots today, but I don't trust any method 100% at this stage.

Here is what I get from **dmesg | grep EFI**
```

[    0.000000] EFI v2.00 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x0000000000067000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x0000000000067000-0x0000000000078000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000078000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x000000000054d000) (4MB)
[    0.000000] EFI: mem05: type=7, attr=0xf, range=[0x000000000054d000-0x0000000000f00000) (9MB)
[    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000000f00000-0x0000000001000000) (1MB)
[    0.000000] EFI: mem07: type=4, attr=0xf, range=[0x0000000001000000-0x0000000001425000) (4MB)
[    0.000000] EFI: mem08: type=3, attr=0xf, range=[0x0000000001425000-0x0000000001429000) (0MB)
[    0.000000] EFI: mem09: type=4, attr=0xf, range=[0x0000000001429000-0x0000000001435000) (0MB)
[    0.000000] EFI: mem10: type=3, attr=0xf, range=[0x0000000001435000-0x0000000001438000) (0MB)
[    0.000000] EFI: mem11: type=4, attr=0xf, range=[0x0000000001438000-0x000000000147d000) (0MB)
[    0.000000] EFI: mem12: type=3, attr=0xf, range=[0x000000000147d000-0x000000000148b000) (0MB)
[    0.000000] EFI: mem13: type=4, attr=0xf, range=[0x000000000148b000-0x0000000001495000) (0MB)
[    0.000000] EFI: mem14: type=3, attr=0xf, range=[0x0000000001495000-0x000000000149d000) (0MB)
[    0.000000] EFI: mem15: type=4, attr=0xf, range=[0x000000000149d000-0x00000000014a3000) (0MB)
[    0.000000] EFI: mem16: type=3, attr=0xf, range=[0x00000000014a3000-0x00000000014a6000) (0MB)
[    0.000000] EFI: mem17: type=4, attr=0xf, range=[0x00000000014a6000-0x00000000014ae000) (0MB)
[    0.000000] EFI: mem18: type=3, attr=0xf, range=[0x00000000014ae000-0x00000000014b1000) (0MB)
[    0.000000] EFI: mem19: type=4, attr=0xf, range=[0x00000000014b1000-0x00000000014b5000) (0MB)
[    0.000000] EFI: mem20: type=3, attr=0xf, range=[0x00000000014b5000-0x00000000014b7000) (0MB)
[    0.000000] EFI: mem21: type=4, attr=0xf, range=[0x00000000014b7000-0x00000000014c2000) (0MB)
[    0.000000] EFI: mem22: type=3, attr=0xf, range=[0x00000000014c2000-0x00000000014c4000) (0MB)
[    0.000000] EFI: mem23: type=4, attr=0xf, range=[0x00000000014c4000-0x00000000014c5000) (0MB)
[    0.000000] EFI: mem24: type=3, attr=0xf, range=[0x00000000014c5000-0x00000000014c6000) (0MB)
[    0.000000] EFI: mem25: type=4, attr=0xf, range=[0x00000000014c6000-0x00000000014c7000) (0MB)
[    0.000000] EFI: mem26: type=3, attr=0xf, range=[0x00000000014c7000-0x00000000014c8000) (0MB)
[    0.000000] EFI: mem27: type=4, attr=0xf, range=[0x00000000014c8000-0x00000000014cb000) (0MB)
[    0.000000] EFI: mem28: type=3, attr=0xf, range=[0x00000000014cb000-0x00000000014ce000) (0MB)
[    0.000000] EFI: mem29: type=4, attr=0xf, range=[0x00000000014ce000-0x00000000014d4000) (0MB)
[    0.000000] EFI: mem30: type=3, attr=0xf, range=[0x00000000014d4000-0x00000000014d6000) (0MB)
[    0.000000] EFI: mem31: type=4, attr=0xf, range=[0x00000000014d6000-0x00000000014ec000) (0MB)
[    0.000000] EFI: mem32: type=3, attr=0xf, range=[0x00000000014ec000-0x00000000014f7000) (0MB)
[    0.000000] EFI: mem33: type=4, attr=0xf, range=[0x00000000014f7000-0x00000000014fb000) (0MB)
[    0.000000] EFI: mem34: type=3, attr=0xf, range=[0x00000000014fb000-0x00000000014fd000) (0MB)
[    0.000000] EFI: mem35: type=4, attr=0xf, range=[0x00000000014fd000-0x0000000001513000) (0MB)
[    0.000000] EFI: mem36: type=3, attr=0xf, range=[0x0000000001513000-0x000000000151e000) (0MB)
[    0.000000] EFI: mem37: type=4, attr=0xf, range=[0x000000000151e000-0x0000000001525000) (0MB)
[    0.000000] EFI: mem38: type=3, attr=0xf, range=[0x0000000001525000-0x000000000152c000) (0MB)
[    0.000000] EFI: mem39: type=4, attr=0xf, range=[0x000000000152c000-0x0000000001538000) (0MB)
[    0.000000] EFI: mem40: type=3, attr=0xf, range=[0x0000000001538000-0x000000000153b000) (0MB)
[    0.000000] EFI: mem41: type=4, attr=0xf, range=[0x000000000153b000-0x000000000194e000) (4MB)
[    0.000000] EFI: mem42: type=3, attr=0xf, range=[0x000000000194e000-0x0000000001950000) (0MB)
[    0.000000] EFI: mem43: type=4, attr=0xf, range=[0x0000000001950000-0x0000000001951000) (0MB)
[    0.000000] EFI: mem44: type=3, attr=0xf, range=[0x0000000001951000-0x0000000001956000) (0MB)
[    0.000000] EFI: mem45: type=4, attr=0xf, range=[0x0000000001956000-0x000000000195c000) (0MB)
[    0.000000] EFI: mem46: type=3, attr=0xf, range=[0x000000000195c000-0x000000000195e000) (0MB)
[    0.000000] EFI: mem47: type=4, attr=0xf, range=[0x000000000195e000-0x0000000001973000) (0MB)
[    0.000000] EFI: mem48: type=3, attr=0xf, range=[0x0000000001973000-0x0000000001975000) (0MB)
[    0.000000] EFI: mem49: type=4, attr=0xf, range=[0x0000000001975000-0x0000000001978000) (0MB)
[    0.000000] EFI: mem50: type=3, attr=0xf, range=[0x0000000001978000-0x0000000001979000) (0MB)
[    0.000000] EFI: mem51: type=4, attr=0xf, range=[0x0000000001979000-0x000000000197c000) (0MB)
[    0.000000] EFI: mem52: type=3, attr=0xf, range=[0x000000000197c000-0x0000000001995000) (0MB)
[    0.000000] EFI: mem53: type=4, attr=0xf, range=[0x0000000001995000-0x00000000019ad000) (0MB)
[    0.000000] EFI: mem54: type=3, attr=0xf, range=[0x00000000019ad000-0x00000000019b5000) (0MB)
[    0.000000] EFI: mem55: type=4, attr=0xf, range=[0x00000000019b5000-0x00000000019b7000) (0MB)
[    0.000000] EFI: mem56: type=3, attr=0xf, range=[0x00000000019b7000-0x00000000019bf000) (0MB)
[    0.000000] EFI: mem57: type=4, attr=0xf, range=[0x00000000019bf000-0x00000000019c5000) (0MB)
[    0.000000] EFI: mem58: type=3, attr=0xf, range=[0x00000000019c5000-0x00000000019d9000) (0MB)
[    0.000000] EFI: mem59: type=4, attr=0xf, range=[0x00000000019d9000-0x00000000019da000) (0MB)
[    0.000000] EFI: mem60: type=3, attr=0xf, range=[0x00000000019da000-0x00000000019e5000) (0MB)
[    0.000000] EFI: mem61: type=4, attr=0xf, range=[0x00000000019e5000-0x00000000019f0000) (0MB)
[    0.000000] EFI: mem62: type=3, attr=0xf, range=[0x00000000019f0000-0x00000000019f7000) (0MB)
[    0.000000] EFI: mem63: type=4, attr=0xf, range=[0x00000000019f7000-0x0000000001a29000) (0MB)
[    0.000000] EFI: mem64: type=3, attr=0xf, range=[0x0000000001a29000-0x0000000001a37000) (0MB)
[    0.000000] EFI: mem65: type=4, attr=0xf, range=[0x0000000001a37000-0x0000000001a38000) (0MB)
[    0.000000] EFI: mem66: type=3, attr=0xf, range=[0x0000000001a38000-0x0000000001a3b000) (0MB)
[    0.000000] EFI: mem67: type=4, attr=0xf, range=[0x0000000001a3b000-0x0000000001a40000) (0MB)
[    0.000000] EFI: mem68: type=3, attr=0xf, range=[0x0000000001a40000-0x0000000001a43000) (0MB)
[    0.000000] EFI: mem69: type=4, attr=0xf, range=[0x0000000001a43000-0x0000000001a44000) (0MB)
[    0.000000] EFI: mem70: type=3, attr=0xf, range=[0x0000000001a44000-0x0000000001a73000) (0MB)
[    0.000000] EFI: mem71: type=4, attr=0xf, range=[0x0000000001a73000-0x0000000001a81000) (0MB)
[    0.000000] EFI: mem72: type=3, attr=0xf, range=[0x0000000001a81000-0x0000000001a83000) (0MB)
[    0.000000] EFI: mem73: type=4, attr=0xf, range=[0x0000000001a83000-0x0000000001a94000) (0MB)
[    0.000000] EFI: mem74: type=3, attr=0xf, range=[0x0000000001a94000-0x0000000001ab4000) (0MB)
[    0.000000] EFI: mem75: type=4, attr=0xf, range=[0x0000000001ab4000-0x0000000001b7d000) (0MB)
[    0.000000] EFI: mem76: type=3, attr=0xf, range=[0x0000000001b7d000-0x0000000001b82000) (0MB)
[    0.000000] EFI: mem77: type=4, attr=0xf, range=[0x0000000001b82000-0x0000000001b84000) (0MB)
[    0.000000] EFI: mem78: type=3, attr=0xf, range=[0x0000000001b84000-0x0000000001b89000) (0MB)
[    0.000000] EFI: mem79: type=4, attr=0xf, range=[0x0000000001b89000-0x0000000001b93000) (0MB)
[    0.000000] EFI: mem80: type=3, attr=0xf, range=[0x0000000001b93000-0x0000000001b98000) (0MB)
[    0.000000] EFI: mem81: type=4, attr=0xf, range=[0x0000000001b98000-0x0000000001ba0000) (0MB)
[    0.000000] EFI: mem82: type=3, attr=0xf, range=[0x0000000001ba0000-0x0000000001ba4000) (0MB)
[    0.000000] EFI: mem83: type=4, attr=0xf, range=[0x0000000001ba4000-0x0000000001ba8000) (0MB)
[    0.000000] EFI: mem84: type=3, attr=0xf, range=[0x0000000001ba8000-0x0000000001bac000) (0MB)
[    0.000000] EFI: mem85: type=4, attr=0xf, range=[0x0000000001bac000-0x0000000001bae000) (0MB)
[    0.000000] EFI: mem86: type=3, attr=0xf, range=[0x0000000001bae000-0x0000000001bb0000) (0MB)
[    0.000000] EFI: mem87: type=4, attr=0xf, range=[0x0000000001bb0000-0x0000000001bb6000) (0MB)
[    0.000000] EFI: mem88: type=3, attr=0xf, range=[0x0000000001bb6000-0x0000000001bb9000) (0MB)
[    0.000000] EFI: mem89: type=4, attr=0xf, range=[0x0000000001bb9000-0x0000000001bbf000) (0MB)
[    0.000000] EFI: mem90: type=3, attr=0xf, range=[0x0000000001bbf000-0x0000000001bc4000) (0MB)
[    0.000000] EFI: mem91: type=4, attr=0xf, range=[0x0000000001bc4000-0x0000000001bd9000) (0MB)
[    0.000000] EFI: mem92: type=3, attr=0xf, range=[0x0000000001bd9000-0x0000000001bdb000) (0MB)
[    0.000000] EFI: mem93: type=4, attr=0xf, range=[0x0000000001bdb000-0x0000000001bdf000) (0MB)
[    0.000000] EFI: mem94: type=3, attr=0xf, range=[0x0000000001bdf000-0x0000000001be1000) (0MB)
[    0.000000] EFI: mem95: type=4, attr=0xf, range=[0x0000000001be1000-0x0000000001be5000) (0MB)
[    0.000000] EFI: mem96: type=3, attr=0xf, range=[0x0000000001be5000-0x0000000001be7000) (0MB)
[    0.000000] EFI: mem97: type=4, attr=0xf, range=[0x0000000001be7000-0x0000000001be8000) (0MB)
[    0.000000] EFI: mem98: type=3, attr=0xf, range=[0x0000000001be8000-0x0000000001bfa000) (0MB)
[    0.000000] EFI: mem99: type=4, attr=0xf, range=[0x0000000001bfa000-0x0000000001c06000) (0MB)
[    0.000000] EFI: mem100: type=3, attr=0xf, range=[0x0000000001c06000-0x0000000001c0a000) (0MB)
[    0.000000] EFI: mem101: type=4, attr=0xf, range=[0x0000000001c0a000-0x0000000001c12000) (0MB)
[    0.000000] EFI: mem102: type=3, attr=0xf, range=[0x0000000001c12000-0x0000000001c21000) (0MB)
[    0.000000] EFI: mem103: type=4, attr=0xf, range=[0x0000000001c21000-0x0000000001c23000) (0MB)
[    0.000000] EFI: mem104: type=3, attr=0xf, range=[0x0000000001c23000-0x0000000001c25000) (0MB)
[    0.000000] EFI: mem105: type=4, attr=0xf, range=[0x0000000001c25000-0x0000000001c2f000) (0MB)
[    0.000000] EFI: mem106: type=3, attr=0xf, range=[0x0000000001c2f000-0x0000000001c34000) (0MB)
[    0.000000] EFI: mem107: type=4, attr=0xf, range=[0x0000000001c34000-0x0000000001c36000) (0MB)
[    0.000000] EFI: mem108: type=3, attr=0xf, range=[0x0000000001c36000-0x0000000001c38000) (0MB)
[    0.000000] EFI: mem109: type=4, attr=0xf, range=[0x0000000001c38000-0x0000000001c4f000) (0MB)
[    0.000000] EFI: mem110: type=3, attr=0xf, range=[0x0000000001c4f000-0x0000000001c52000) (0MB)
[    0.000000] EFI: mem111: type=4, attr=0xf, range=[0x0000000001c52000-0x0000000001c55000) (0MB)
[    0.000000] EFI: mem112: type=3, attr=0xf, range=[0x0000000001c55000-0x0000000001c58000) (0MB)
[    0.000000] EFI: mem113: type=4, attr=0xf, range=[0x0000000001c58000-0x0000000001c5b000) (0MB)
[    0.000000] EFI: mem114: type=3, attr=0xf, range=[0x0000000001c5b000-0x0000000001c6a000) (0MB)
[    0.000000] EFI: mem115: type=4, attr=0xf, range=[0x0000000001c6a000-0x0000000001ca0000) (0MB)
[    0.000000] EFI: mem116: type=7, attr=0xf, range=[0x0000000001ca0000-0x0000000001ca4000) (0MB)
[    0.000000] EFI: mem117: type=4, attr=0xf, range=[0x0000000001ca4000-0x0000000001cbf000) (0MB)
[    0.000000] EFI: mem118: type=7, attr=0xf, range=[0x0000000001cbf000-0x0000000001cc0000) (0MB)
[    0.000000] EFI: mem119: type=4, attr=0xf, range=[0x0000000001cc0000-0x0000000001d04000) (0MB)
[    0.000000] EFI: mem120: type=3, attr=0xf, range=[0x0000000001d04000-0x0000000001d07000) (0MB)
[    0.000000] EFI: mem121: type=4, attr=0xf, range=[0x0000000001d07000-0x0000000001d12000) (0MB)
[    0.000000] EFI: mem122: type=3, attr=0xf, range=[0x0000000001d12000-0x0000000001d14000) (0MB)
[    0.000000] EFI: mem123: type=4, attr=0xf, range=[0x0000000001d14000-0x0000000001d35000) (0MB)
[    0.000000] EFI: mem124: type=3, attr=0xf, range=[0x0000000001d35000-0x0000000001d4a000) (0MB)
[    0.000000] EFI: mem125: type=4, attr=0xf, range=[0x0000000001d4a000-0x0000000001d58000) (0MB)
[    0.000000] EFI: mem126: type=3, attr=0xf, range=[0x0000000001d58000-0x0000000002164000) (4MB)
[    0.000000] EFI: mem127: type=4, attr=0xf, range=[0x0000000002164000-0x00000000026cf000) (5MB)
[    0.000000] EFI: mem128: type=7, attr=0xf, range=[0x00000000026cf000-0x00000000026ee000) (0MB)
[    0.000000] EFI: mem129: type=4, attr=0xf, range=[0x00000000026ee000-0x000000000270b000) (0MB)
[    0.000000] EFI: mem130: type=7, attr=0xf, range=[0x000000000270b000-0x0000000002745000) (0MB)
[    0.000000] EFI: mem131: type=4, attr=0xf, range=[0x0000000002745000-0x0000000002a3b000) (2MB)
[    0.000000] EFI: mem132: type=7, attr=0xf, range=[0x0000000002a3b000-0x0000000002b67000) (1MB)
[    0.000000] EFI: mem133: type=4, attr=0xf, range=[0x0000000002b67000-0x0000000003b40000) (15MB)
[    0.000000] EFI: mem134: type=1, attr=0xf, range=[0x0000000003b40000-0x0000000003b60000) (0MB)
[    0.000000] EFI: mem135: type=7, attr=0xf, range=[0x0000000003b60000-0x0000000004443000) (8MB)
[    0.000000] EFI: mem136: type=4, attr=0xf, range=[0x0000000004443000-0x0000000004527000) (0MB)
[    0.000000] EFI: mem137: type=7, attr=0xf, range=[0x0000000004527000-0x0000000004c39000) (7MB)
[    0.000000] EFI: mem138: type=4, attr=0xf, range=[0x0000000004c39000-0x0000000004c3a000) (0MB)
[    0.000000] EFI: mem139: type=7, attr=0xf, range=[0x0000000004c3a000-0x00000000366e0000) (794MB)
[    0.000000] EFI: mem140: type=2, attr=0xf, range=[0x00000000366e0000-0x0000000037368000) (12MB)
[    0.000000] EFI: mem141: type=7, attr=0xf, range=[0x0000000037368000-0x000000008fefd000) (1419MB)
[    0.000000] EFI: mem142: type=2, attr=0xf, range=[0x000000008fefd000-0x00000000befbc000) (752MB)
[    0.000000] EFI: mem143: type=10, attr=0xf, range=[0x00000000befbc000-0x00000000bf010000) (0MB)
[    0.000000] EFI: mem144: type=6, attr=0x800000000000000f, range=[0x00000000bf010000-0x00000000bf35b000) (3MB)
[    0.000000] EFI: mem145: type=0, attr=0xf, range=[0x00000000bf35b000-0x00000000bf5a1000) (2MB)
[    0.000000] EFI: mem146: type=10, attr=0xf, range=[0x00000000bf5a1000-0x00000000bf5b2000) (0MB)
[    0.000000] EFI: mem147: type=0, attr=0xf, range=[0x00000000bf5b2000-0x00000000bf5b5000) (0MB)
[    0.000000] EFI: mem148: type=6, attr=0x800000000000000f, range=[0x00000000bf5b5000-0x00000000bf5c6000) (0MB)
[    0.000000] EFI: mem149: type=5, attr=0x800000000000000f, range=[0x00000000bf5c6000-0x00000000bf5c7000) (0MB)
[    0.000000] EFI: mem150: type=6, attr=0x800000000000000f, range=[0x00000000bf5c7000-0x00000000bf5c9000) (0MB)
[    0.000000] EFI: mem151: type=7, attr=0xf, range=[0x00000000bf5c9000-0x00000000bf5cb000) (0MB)
[    0.000000] EFI: mem152: type=10, attr=0xf, range=[0x00000000bf5cb000-0x00000000bf5cc000) (0MB)
[    0.000000] EFI: mem153: type=6, attr=0x800000000000000f, range=[0x00000000bf5cc000-0x00000000bf5cd000) (0MB)
[    0.000000] EFI: mem154: type=5, attr=0x800000000000000f, range=[0x00000000bf5cd000-0x00000000bf5d4000) (0MB)
[    0.000000] EFI: mem155: type=10, attr=0xf, range=[0x00000000bf5d4000-0x00000000bf5de000) (0MB)
[    0.000000] EFI: mem156: type=5, attr=0x800000000000000f, range=[0x00000000bf5de000-0x00000000bf5eb000) (0MB)
[    0.000000] EFI: mem157: type=6, attr=0x800000000000000f, range=[0x00000000bf5eb000-0x00000000bf62c000) (0MB)
[    0.000000] EFI: mem158: type=5, attr=0x800000000000000f, range=[0x00000000bf62c000-0x00000000bf637000) (0MB)
[    0.000000] EFI: mem159: type=6, attr=0x800000000000000f, range=[0x00000000bf637000-0x00000000bf63a000) (0MB)
[    0.000000] EFI: mem160: type=10, attr=0xf, range=[0x00000000bf63a000-0x00000000bf67d000) (0MB)
[    0.000000] EFI: mem161: type=3, attr=0xf, range=[0x00000000bf67d000-0x00000000bf7f4000) (1MB)
[    0.000000] EFI: mem162: type=4, attr=0xf, range=[0x00000000bf7f4000-0x00000000bf7f7000) (0MB)
[    0.000000] EFI: mem163: type=3, attr=0xf, range=[0x00000000bf7f7000-0x00000000bf800000) (0MB)
[    0.000000] EFI: mem164: type=7, attr=0xf, range=[0x0000000100000000-0x000000023f800000) (5112MB)
[    0.000000] EFI: mem165: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] EFI: mem166: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    1.626138] EFI Variables Facility v0.08 2004-May-17

```

Here is what I get from **sudo efibootmgr -v**
```

BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* ubuntu	HD(1,22,5f5e2,3567a134-959c-4658-b40c-1ce8dd125f3f)File(\EFI\ubuntu\grubx64.efi)
Boot0001* Hard Drive	BIOS(2,0,00)

```

Strangely enough, even though I get output from efibootmgr. **sudo lsmod | grep efi** always returns nothing.

**/boot/efi**, the mount point for /dev/sda1 (above) simply contains the following directory structure and single file:
/boot/efi**/EFI/ubuntu/grubx64.efi**

What am I missing?

Any help appreciated & advTHANKSance ;)

---

### Post by oldfred on 2011-10-10
Not too many here know UEFI including me. I do use gpt but with BIOS. But I have some links.

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

This is Arch but still discusses grub2.
Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

Someone posted this but they also booted windows and used refit. I think grub/Ubuntu has lots of other files in the ubuntu directory.

find /boot/efi -name "*efi"
```
/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/BOOT/refit.efi
/boot/efi/EFI/BOOT/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi
/boot/efi/EFI/grub/grub.efi
/boot/efi/EFI/BOOT-backup/bootx64.efi
/boot/efi/EFI/BOOT-backup/BOOT/refit/refit.efi
/boot/efi/EFI/BOOT-backup/BOOT/bootx64.efi
```

---

### Post by linthusiast on 2011-10-11
Thank you oldfred :)

From your post I think I've got most of that correct already in that I manually setup the partitions:
1) 200MB FAT16 (EFI, /boot/efi) a.k.a. /dev/sda1
2) 55GB approx (ex4, /) <-- my root partition a.k.a. /dev/sda2
3) 8GB approx (swap) a.k.a. /dev/sda3

Upon Ubuntu (11.04 x64) installation, I requested that the installer write the bootloader to /dev/sda1 (my 200MB EFI / FAT16 partition, as above). During the installation I didn't have to tell the installer to create an EFI record for "ubuntu". It did this automatically, as the new entry was immediately available as a UEFI boot option in my UEFI settings upon reboot.

At that time, the installer would have automatically installed grub-pc and not grub-efi. Once I got back in to the machine via USB live, I used Synaptic Package Manager to uninstall grub-pc and replace it with grub-efi-dummy, grub-efi-(the 64bit version) and efibootmgr.

Although **sudo lsmod | grep efi** returns nothing, **sudo efibootmgr -v** does give me a list of boot options. (See my last post)

Having a look at dmesg just there I have noticed the following amongst what seems to be a fairly normal log:
```

 4.827515] ------------[ cut here ]------------
[    4.827521] WARNING: at /build/buildd/linux-2.6.38/arch/x86/mm/ioremap.c:109 __ioremap_caller+0x3a4/0x3d0()
[    4.827522] Hardware name: System Product Name
[    4.827523] Modules linked in: parport_pc ppdev binfmt_misc snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec nls_iso8859_1 nls_cp437 vfat fat snd_hwdep psmouse snd_pcm snd_seq_midi snd_rawmidi b43 snd_seq_midi_event mac80211 snd_seq serio_raw snd_timer eeepc_wmi snd_seq_device cfg80211 joydev snd nvidia(P) soundcore usbhid hid sparse_keymap ath3k xhci_hcd snd_page_alloc lp parport ssb firewire_ohci r8169 firewire_core crc_itu_t ahci libahci
[    4.827542] Pid: 1123, comm: Xorg Tainted: P        W   2.6.38-8-generic #42-Ubuntu
[    4.827543] Call Trace:
[    4.827547]  [<ffffffff81065cef>] ? warn_slowpath_common+0x7f/0xc0
[    4.827549]  [<ffffffff81065d4a>] ? warn_slowpath_null+0x1a/0x20
[    4.827551]  [<ffffffff81040e04>] ? __ioremap_caller+0x3a4/0x3d0
[    4.827552]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
[    4.827653]  [<ffffffffa0612055>] ? os_map_kernel_space+0x85/0xe0 [nvidia]
[    4.827656]  [<ffffffff814b6b73>] ? pci_conf1_read+0xc3/0x120
[    4.827658]  [<ffffffff81040e87>] ? ioremap_nocache+0x17/0x20
[    4.827742]  [<ffffffffa0612055>] ? os_map_kernel_space+0x85/0xe0 [nvidia]
[    4.827824]  [<ffffffffa05e50ad>] ? _nv022990rm+0x55/0x71 [nvidia]
[    4.827876]  [<ffffffffa01105ef>] ? _nv025429rm+0x62/0x11a [nvidia]
[    4.827927]  [<ffffffffa0110740>] ? _nv022146rm+0x99/0xcb [nvidia]
[    4.827978]  [<ffffffffa0110bc3>] ? _nv022209rm+0x58/0x9e [nvidia]
[    4.828028]  [<ffffffffa010cd50>] ? _nv022166rm+0xe9/0x31b [nvidia]
[    4.828079]  [<ffffffffa010d02c>] ? _nv022216rm+0xaa/0x173 [nvidia]
[    4.828129]  [<ffffffffa010d145>] ? _nv022165rm+0x50/0x5d [nvidia]
[    4.828179]  [<ffffffffa0112a0f>] ? _nv022157rm+0x6e/0x78 [nvidia]
[    4.828260]  [<ffffffffa05e8e7a>] ? _nv018970rm+0x69/0x121 [nvidia]
[    4.828339]  [<ffffffffa05e8df8>] ? _nv018984rm+0xe8/0x101 [nvidia]
[    4.828395]  [<ffffffffa0132f41>] ? _nv004550rm+0x68/0x1f4 [nvidia]
[    4.828503]  [<ffffffffa040ea7c>] ? _nv014822rm+0x176/0x4c3 [nvidia]
[    4.828611]  [<ffffffffa040db93>] ? _nv015121rm+0xe9/0x165 [nvidia]
[    4.828658]  [<ffffffffa00e387c>] ? _nv015298rm+0xd/0x12 [nvidia]
[    4.828737]  [<ffffffffa05e8bbf>] ? _nv002400rm+0x19d/0x28a [nvidia]
[    4.828816]  [<ffffffffa05e9a0f>] ? _nv002394rm+0x4a7/0x685 [nvidia]
[    4.828895]  [<ffffffffa05ef51d>] ? rm_init_adapter+0x9d/0x111 [nvidia]
[    4.828973]  [<ffffffffa060b1a4>] ? nv_kern_open+0x494/0x6c0 [nvidia]
[    4.828977]  [<ffffffff81168f4a>] ? chrdev_open+0xda/0x1f0
[    4.828979]  [<ffffffff81168e70>] ? chrdev_open+0x0/0x1f0
[    4.828980]  [<ffffffff81162cee>] ? __dentry_open+0xce/0x2f0
[    4.828982]  [<ffffffff8116ef33>] ? generic_permission+0x23/0xc0
[    4.828985]  [<ffffffff812b083e>] ? devcgroup_inode_permission+0xe/0x110
[    4.828987]  [<ffffffff811641e1>] ? nameidata_to_filp+0x71/0x80
[    4.828989]  [<ffffffff811733c8>] ? finish_open+0xc8/0x1b0
[    4.828991]  [<ffffffff811725b7>] ? do_path_lookup+0x87/0x160
[    4.828992]  [<ffffffff81173b88>] ? do_filp_open+0x2c8/0x7c0
[    4.828995]  [<ffffffff81090cb9>] ? in_group_p+0x9/0x40
[    4.828998]  [<ffffffff815c0a29>] ? _cond_resched+0x9/0x40
[    4.829001]  [<ffffffff811809cd>] ? expand_files+0x1d/0x110
[    4.829002]  [<ffffffff81180ea7>] ? alloc_fd+0xf7/0x150
[    4.829004]  [<ffffffff8116425a>] ? do_sys_open+0x6a/0x150
[    4.829006]  [<ffffffff8116eff2>] ? path_put+0x22/0x30
[    4.829007]  [<ffffffff81164360>] ? sys_open+0x20/0x30
[    4.829009]  [<ffffffff8100c002>] ? system_call_fastpath+0x16/0x1b
[    4.829011] ---[ end trace a7919e7f17c0a727 ]---
[    4.829081] ioremap error for 0xbeffe000-0xbefff000, requested 0x10, got 0x0

```

Right now in my UEFI settings my boot order is as follows:
1) "ubuntu"
2) My SSD disk

If I had a USB memory stick connected, I would obviously have more options available, but when it's just the SSD, the above 2 options are all that is available.

Today when I booted for the first time, I was just left with the purple screen and no disk activity. So I rebooted. I pressed F8 on my motherboard splash screen which gives me a list of boot options. I selected "ubuntu" and I was then given the Grub listing. I selected the first option, which would normally just boot Ubuntu, and again I'm left at a purple screen with no further activity. So I reboot again and this time I access my UEFI settings. I leave the boot order alone, and simply select an immediate boot of "ubuntu", the Grub menu pops up again, I select the first option as before, and hep presto I'm at my Ubuntu login screen within about 6 - 7 seconds.

It's incredibly frustrating because of the 3 different approaches as described above to boot the machine as far as the Ubuntu login screen, it's simply a case of trial and error until one of the methods works. What I can't understand is that "ubuntu" is the boot option that is ultimately selected in every method described above, yet it doesn't always work.

From the links I noticed that some people are building grub 1.99 from source and copying it to their EFI partition. I have not done this because Grub 1.99 already comes with Ubuntu 11.04 x64 and I have read elsewhere that this version can manage EFI booting.

If it was a case that I could never boot in to Ubuntu I would chalk it up a solid misconfiguration, but the randomness of success is what is causing me such grief.

Also the partition table is definitely based on GPT because fdisk complains when I do a **sudo fdisk -l**
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
```

Apologies again for all the info, I genuinely appreciate any help I can get.

---

### Post by oldfred on 2011-10-11
In BIOS mode some start to boot but then have video or other parameter settings that are needed. So are you booting and have a video issue.

I think the grub 1.99 in Oneiric is more updated and current than the one in 11.04. 11.10 is due shortly.

---

### Post by linthusiast on 2011-10-11
I am not sure if I'm having a video issue, in that I can't tell. From the dmesg listing I provided in my last post, it certainly looks like an "nvidia" issue. I have an NVidia 8800 GTS 512MB card installed in the PCI-E socket. After first successful boot following the install, the system notified me that Nvidia drivers were available. The nvidia drivers are now installed, they were downloaded from the net during the driver installation and I can confirm that my card is up and running fine. I even have twin Full HD (1920x1080) screens connected via a digital interface and all is working perfectly. The dmesg listing I provided in my last post was obviously following a successful boot.

Actually when I look in the "Additional Drivers" utility is shows two NVIDIA accelerated graphics drivers.

1) NVIDIA accelerated graphics driver (version 173)
2) NVIDIA accelerated graphics driver (version current) [Recommended]

The first one has a grey ball to the left, and the second one has a green ball.

When I click on the second one, it says down the bottom of the window
"This driver is activated but not currently in use."

This is strange because before I installed the driver, I wouldn't have been able to access Unity, etc, but since the driver was installed, I can do all of that (Compiz, etc, etc).

Is there anything from the above that identifies a problem?

I am keeping my Natty install basic at the moment, because I intend to perform a clean install of Oneric x64 on Thursday when it becomes available. However if I'm doing something wrong at this stage and just bringing problems with me to Oneric then it would be seriously cool to find out what they are so I can fix them.

Also just to be clear, when my computer freezes during an unsuccessful boot, the screen is completely purple. There are no visual anomalies / scattered display / etc that would suggest rendering issues.

Is there a way that I can get some insight in to the boot process instead of looking at a purple screen?. At least that way I might get some clue as to where the boot process is failing in those cases.

---

### Post by linthusiast on 2011-10-11
OK, I powered down my machine about 2 hours ago, having worked with it fine for several hours and came back to boot it again about an hour ago. Despite numerous attempts I have consistently failed to boot the machine to the Ubuntu login screen. In my previous posts I stated that if I attempt to try each of 3 methods, I should be able to boot successfully using one of them. I can now confirm this is not the case.

I have tried everything, and I keep ending up in the same place. The first time I powered the machine on, it just gave me the purple screen and froze. I have noticed that during the Ubuntu boot sequence my keyboard and mouse turn off and back on again (which is quite normal) during all boot attempts. On occasion now I notice that either both or one of those USB devices doesn't turn back on before the boot sequence freezes. It could just be a timing thing. I have also tried different keyboards and mice (both PS/2 & USB). Makes no difference.

The next time I boot after a previous boot failure, I get to see the GRUB 1.99-rc1 menu (which is correct behavior), where again I select Ubuntu (first choice) and again it proceeds on to the exact same thing where the HD activity LED flickers a couple of times before everything just stops and I'm again left with a blank purple screen.

I'm at my wits end, my problem is that I don't know where the problem is. Is it hardware? Is it UEFI firmware? Is it GRUB? Is it a driver issue?

How can I diagnose further?

The only time I get access to status information is when the machine has actually booted successfully, when it doesn't all I can do is press hard reset and live in hope that one of the methods I have available to bring the machine up next time works. 

Anyone have any other ideas for things I could try?, I would really appreciate your help.

Surely if a UEFI boot of Ubuntu on my machine works even once, it means that everything configuration wise must be in order. From that it makes no sense how random all this is.

---

### Post by oldfred on 2011-10-11
I just installed Oneiric and it also installed both the nVidia 173 and current and seemed to be using 173 as the default. I uninstalled 173 and installed the current version as that was all it offered in older installs. I thought the 173 was for older versions of nVidia cards. I have a 9600GT.

This was a note I copied somewhat.
> Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.


I have so little knowledge of UEFI that I can be only a little help. I have seen several others post and a few seem to get it to work and others have issues. Some have just reverted to BIOS mode and even reinstalled to MBR partitioning. But I still like gpt partitioning even with BIOS mode. I do know their are more fixed to grub1.99 in Oneiric.  

Do you get to a grub menu? If so use e for edit and remove quiet splash. That will let you see the boot process like the dmeg or log files you have posted.

---

### Post by linthusiast on 2011-10-11
Thank you oldfred, I really appreciate your help.

Yes I get as far as the Grub menu. When I cold boot the machine I don't see a Grub menu because I only have one OS installed (Ubuntu). Then if the machine fails to boot and I do a reset, then I see the GRUB menu the next time (without countdown), which is correct Ubuntu behaviour in the event that a previous boot failed.

So anyway I press 'e' at the GRUB menu and I get an emacs type interface that lets me modify the record. I go to the line that loads my kernel and I remove the text "quiet splash", leaving everything else in place. My choices beyond that point are press ESC to just discard changes and go back to GRUB menu or press F10 to boot. When I press F10 to boot, I just get the blank purple screen like the changes I just made don't take effect.

Something else I have observed to consistently occur during every unsuccessful boot I've made since my last post is that just before it freezes on the purple screen (before where it should show the Ubuntu logo and loading dots) my mouse and keyboard turn off. The mouse turns back on and the keyboard never does. I have tried both a USB & PS/2 keyboard just in case it was the keyboard.

So I still can't see the boot messages to get more visibility. I am using the GRUB system incorrectly?

Oh yes I forgot to mention I re-install Natty once again using the same partition layout as before, and confirmed that the installer did not attempt to install grub-pc. It knew to use EFI. After the install completed. I rebooted the machine and it came up perfectly the next time. I noticed during the installation something about nvidia-current not installing with an ERROR. I looked this up and many people seemed to have this problem, but an apt-get install --reinstall nvidia-current seemed to sort it out. So I did that and it worked fine. The Additional Drivers utility however still said that the driver was not in use. So I decided then to get the latest drivers from NVidia themselves, released in the last few days. I installed those and confirmed via my Nvidia utility that they were installed and running.

I rebooted the machine and back I am again to the same old frozen purple screen.

---

### Post by oldfred on 2011-10-11
On a frozen screen use this to reboot:

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Another
sudo init 0

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

From an edited grub menu, it is control -x to use the edited commands to boot.

My BIOS has settings for USB mouse & keyboard. Until I changed those in BIOS they did not work correctly. Not sure if your UEFI has the same settings, but is has a BIOS mode and I would think it has many pages with options in UEFI.

See mine where I had to change to enabled.

---

### Post by linthusiast on 2011-10-11
When I hold Ctrl & press x while editing Grub after pressing 'e', it doesnt boot with the modified options. It just displays the 'x' character like I'm not holding Ctrl. The only way for me to boot is to press F10 & that looks like it completely ignores any changes I've made.

In the last few mins I managed to "Try Ubuntu" booted via UEFI USB. First attempt, crashed with what looked like a kernel panic, black screen, high res. The next reboot I selected the same boot option; UEFI USB. Again kernel panic, but looked like a different message, high res. Third time it just booted straight to desktop.

I'm starting to think this isn't an UEFI issue as I wouldn't be able to get to GRUB at all if it was. Does that sound plausible?

I'm wondering has this more to do with Grub config, kernel compatibility with my Sandybridge motherboard or a driver issue.

Strange thing though that started this whole process for me was about 2 weeks ago when this started happening. My computer, built by me in July with an ASRock P67 Pro3, i5 2500k and running nothing but natty was working flawlessly up until 2 weeks ago. When I first installed I didn't know anything about UEFI, so just performed the Natty install as normal. It worked and my machine booted. It continued to do that without fail for over 2 months. Then suddenly one day it just stopped. I thought it was a board failure because I tried everything except processor in another machine and components were fine. So I just got an Asus P8P67 to replace the motherboard. I performed a clean Natty install with that new board and I still face the same boot problems.

I cannot understand how I managed to work without problems for 2 months and then suddenly it's like Ubuntu just took a dislike to my new hardware.

From that I wonder is there new information that would assist in diagnosing the problem.

---

### Post by oldfred on 2011-10-11
Yes it sounds like you are rebooting so any changes to the grub menu are not kept. For permantent changes you have to edit /etc/default/grub and run sudo update grub. You have to do that after you have booted or chrooted into your install. You may be able to make changes to grub.cfg which it says not to edit, but I am not sure if those changes will help or not.

And it sounds like you are booting, but having other issues. I am surprised it worked before as even Phronix review site has several reviews of i5 & i7 where he discusses versions of kernels or other software required to make it work.
[http://www.phoronix.com/scan.php?page=article&item=intel_corei5_2400s&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_corei5_2400s&num=1)

---

### Post by linthusiast on 2011-10-12
Wuhoo after making the following changes, I have been rebooting and cold booting every time with success for the last dozen or so boot tests.

While toying around with my last install it got to the stage where I was dropped to BusyBox during boot and I started switching between tty's. I noticed on one of them I got some boot messages where it said was not able to get access to /dev/sda2 (my root partition). I looked up the problem and found that some people had success by modifying their grub.cfg and putting the following at the end of the line that loads the kernel

```
quiet splash vt.handoff=7 **rootdelay=90** reboot=a,w
```

The rootdelay instruction is what made the biggest difference. The reboot=a,w stopped my machine from hanging during reboot and shutdown.

So there you have it, I'm confident the rootdelay parameter is what made the difference, if not it was one of the following:

Fresh natty x64 install (manually created partitions during install, with EFI boot partion, root partition & swap partition, and specified to install loader to EFI partition) also with "download updates" selected during installation via a wired network interface. When install was complete, and I managed to get in to the OS, I updated the grub.cfg with the above. I also installed any updates that were available (I literally updated everything it suggested I update). I downloaded/installed the nvidia-current driver as this failed during the install and 173 was installed instead.

Thank you very much oldfred for your assistance & patience. I genuinely appreciate your contributions. Cheers buddy ;)

---

### Post by Basher101 on 2011-10-12
wow this will save me alooot of time and frustration, because next month i will get a build with UEFI too (MSI Z68A-GD65 (G3) with i7 2600k and the GTX 570 graphics card and a SSD for windows and ubuntu). 

*bookmarked*

---

### Post by oldfred on 2011-10-12
Glad it worked, not that I really suggested anything that did. :)

But I will also bookmark this for others that may have similar issues.

---

### Post by linthusiast on 2011-10-12
> **Basher101 said:**
> wow this will save me alooot of time and frustration, because next month i will get a build with UEFI too (MSI Z68A-GD65 (G3) with i7 2600k and the GTX 570 graphics card and a SSD for windows and ubuntu). 

*bookmarked*
Hey Basher101, Natty (11.04) managed UEFI fine. However when installing, make sure you manually create the partitions yourself. Create a 200MB EFI partition and from the drop down list for the partition type, select "EFI boot partition". Then create whatever other partitions you need along with your swap partition. Make sure you write the boot loader to the EFI partition  (again via another drop down to select the partition). What I've noticed after my several attempts is that if you do the above, the installer will not install grub-pc, but instead install the correct grub-efi, etc. So as far as Ubuntu is concerned it knows you are using UEFI and not MBR right off the bat.

The issues I was having seemed to have more to do with root partition access during the boot sequence, but I was lacking the visibility in to the boot sequence and **thanks to oldfred** I found my way past that problem.

When I last posted I still have just a single SSD connected up to my Asus P8P67 (SATA 6GB). In the mean time I tried to connect up two other SATA disks to the 3GB SATA interfaces on the board. When I tried to boot, I again got the purple screen of death. I popped open the case, disconnected the 2 extra drives and the machine boots again. I'm guessing I'll have to look in to that, but I'd say my solution is within the UEFI settings as opposed to Ubuntu. My board has the B3 revision which fixed SATA issues in earlier type 1155 Intel boards this year, so it shouldn't be a firmware issue.

It's great though having my machine back working again. My Asus board, i5 2500k, nvidia-current drivers, and my broadcom (b43) wireless card all running perfectly, even 5.1 audio ;)

Now I can get back to real work instead of crawling around on a 5 year old laptop.

---

### Post by csete on 2011-10-13
linthusiast: I attempted to do an install very similar to yours.  However, I keep landing on the GRUB rescue screen.  I can't seem to get my Ubuntu install to boot at all.  My thread is still open at [http://ubuntuforums.org/showthread.php?t=1857605](http://ubuntuforums.org/showthread.php?t=1857605) .  I tried to do what I believe you suggested in terms of the partitioning in the installer, but ended up at grub rescue prompt.  My dmesg output shows that I have American Megatrends as well, so it seems like I should have a similar setup.  Once difference is that I'm trying to allow for a Win 7 dual-boot in my partitioning.

Anyway, can you tell me what you did step-by-step to get to a working UEFI boot?   I'd really appreciate it as I feel like I'm about to lose my mind trying to get this working.  

Thanks so much,
Craig

---

### Post by alphaamanitin on 2011-10-13
ARG!!! I AM SO JEALOUS OF ALL OF YOU!!!  GRUB2 will not install on my machine.  I am trying to dual boot two SSDs, one with Windows 7 UEFI and one with Ubuntu UEFI.  Windows 7 install in UEFI mode fine, but I cannot get Ubuntu to install (though I admittedly have not tried since about two months after 11 was released).  I cannot even make it past the install.  It always crashes and burns while trying to install grub2.  This happens whether or not I set up the boot partitions manually.   I think when go home I will read through this thread and give it another shot.  Otherwise I am abandoning Ubuntu for Archlinux (puke, don't want to take the time to set up everything!) or some other distro.

AlphaA

---

### Post by linthusiast on 2011-10-13
Hey guys sorry I didn't spot this until now.

OK my mobo is an Asus P8P67 (rev 3.1, with B3 revision). I started up the machine from an Ubuntu (Natty, 11.04, x64) USB drive. My UEFI boot manager allowed me to start up the USB key in either UEFI or normal mode. I read elsewhere that you should start it up in UEFI mode if you want to do the install properly. I would get to the black Grub screen, which let me Try or Install. I selected "Try". It usually took about 3 tries to get the machine to start up in UEFI mode via USB, with kernel panics during the first few tries. I literally kept trying the same USB UEFI boot using whatever methods my motherboard allowed until it worked. Starting up in non UEFI mode is a waste of time.

So anyway, let's say you are now at the Ubuntu Live desktop. If you have a wired net connection available, make sure it's connected and eth0 is up and running. Do a quick browser check to make sure you're online. Run the installer (via desktop icon) and have it get any updates available during the install. One difference between my setup and what I think you want is that I didn't want to install Windows. I have a single SSD (& a few normal SATAs for storage). I wanted to just install Ubuntu on the SSD. So when the installer asked me what I wanted to do, I simply told it to Erase the entire SSD and install (from the 4 options available). I did this because I had already failed Ubuntu attempts previously installed and needed to wipe the disk anyway. So I cleared the partition table that currently existed and created a new one.

So for my 64GB SSD (/dev/sda) I did the following:
**First partition** at the front of the disk: 200MB, select EFI boot partition from drop down. 200MB should be plenty even if you plan on installing more than Ubuntu for the other .efi files.
**Second partition**: 55GB ex4 (journaled), which is my '/' (root) partition.
**Third partition**: the remaining ~8GB for swap

If you plan on installing Windows, leave yourself sufficient free space unlike what I did for the relevant NTFS partition(s).

Install, and keep an eye on the installer messages. Something I noticed months ago when I was first installing Natty was that the installer kept crapping out due to the ISO being compromised, so double check the MD5 checksum for the ISO you download. If I did that a few months back, I wouldn't have stupidly lost a few hours wondering WTF was wrong :roll:

On a compromised ISO I never got to Install Success, so if you do, that's obviously a good sign ;). Also before the installer ends, keep an eye out for the grub installation messages. You should clearly see grub-efi as opposed to grub-pc get installed.

OK, so that's the installation. Reboot. Bring up UEFI and make sure that you now have a new UEFI:"ubuntu" boot option available. Run it. You should get to the GRUB screen. Try and boot the first option. If the machine doesn't boot, try it a few different ways until you successfully start up UEFI:ubuntu. I eventually did get the machine to boot this way. Once it started up I installed all updates that were available and downloaded my nvidia-current drivers because the 173 driver wasn't nearly as good. If you never succeed in SSD booting, try and start up using the Live USB again. Whatever way you get to a desktop, (mount your root partition if coming in via USB) change /boot/grub/grub.cfg to include the
```
rootdelay=90
```
parameter towards the end of the line that attempts to load your kernel. Save it, and reboot the machine. When Grub comes up again when trying to boot your Ubuntu install on your SSD, press 'e' and just confirm that your grub.cfg change is now available in the config. Press F10 to continue with the boot.

At this stage my machine started to boot properly and has continued with success every time since.

A few tests that you can do to help diagnose problems with UEFI. You want the following:
```
sudo efibootmgr -v
```
Should give you a listing of boot options available.

```
sudo fdisk -l
```
Should complain that you are using GPT partitioning.

Synaptic package manager should not make reference to grub-pc being already installed. If it does, get rid of it. Make sure that grub-efi-dummy, grub-efi-(the 64bit version I assume you want) & efibootmgr.

Finally and I didn't do this myself, but I've heard that you should never try to install Windows first and then Ubuntu later in EFI mode as it will only wipe your EFI partition or at least render Windows unbootable. This is quite a change from all the years we have been installing Linux last and having Grub detect on the existing operating systems. I have not installed Windows in a long time, so however the kids are doing it these days see if there is any scope for you to write the Windows bootloader to your existing EFI partition. Remember the Ubuntu installer formatted the EFI partition as FAT so Windows will be able to work with it. However it is FAT16, and I'm not sure if this will cause problems. If it does, then perhaps manually create the partitions when installing Ubuntu, and create a FAT32 partition, but you will need to use efibootmgr or gparted later to set the boot flag or something. Not 100% on that, as I haven't done it yet, but I do know that setting it as a "EFI boot partition" causes the installer to format as FAT16 without ability to override.

To be honest I'm not a PC gamer (anymore), so when I need other OS's, I just virtualize in Ubuntu.

I hope this is of help to you & best of luck ;)

---

### Post by oldfred on 2011-10-14
Each of these has only one person posting the error, but which I regularly see the same errors in the forums. If you have any of these issues please login to Launchpad and add your name to those with the issue. They fix those issues that are more common.

Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

---

### Post by alphaamanitin on 2011-10-15
I tried launchpad, and I consider myself moderatly tech savvy, and couldn't figure it out.  The shame, I know.  I wish those were my problems, but I will add my own as well.  Thanks for the info oldfred.

AlphaA

---

