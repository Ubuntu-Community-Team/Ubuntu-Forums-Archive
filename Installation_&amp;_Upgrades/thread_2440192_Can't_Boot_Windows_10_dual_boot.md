---
title: "Can't Boot Windows 10 dual boot"
date: 2020-04-07
forum: Installation &amp; Upgrades
---

### Post by aryannc on 2020-04-07
This thread is related to this [one]("https://ubuntuforums.org/showthread.php?t=2440121").
Windows not booting up in another PC(asus vivobook 15 x505za), (to solve the issue encountered in the linked thread), the following issue occurred:
[ATTACH=CONFIG]285444[/ATTACH]
**efibootmgr -v returns:**
```

aryannc@aryannc-asus-X505ZA:~$ efibootmgr -v
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0001,0000,0002,0003,0004
Boot0000* Windows Boot Manager    HD(1,GPT,06c6ee64-ad70-4db5-9170-ba2ff2b99b55,0x800,0x82000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    HD(1,GPT,e6002c7a-98c1-42f8-8129-5f0fa3a1e72a,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* UEFI:CD/DVD Drive    BBS(129,,0x0)
Boot0003* UEFI:Removable Device    BBS(130,,0x0)
Boot0004* UEFI:Network Device    BBS(131,,0x0)
```[COLOR=#888888]
[/COLOR]**Grub (asus):**
[ATTACH=CONFIG]285445[/ATTACH]
Thank you for your help.

---

### Post by CelticWarrior on 2020-04-07
What is the point of this new thread? 

You already told us > Windows **does not boot directly successfully,** as it goes over to either recovery options or the Automatic Repair loop.

This means it needs repairs, at best, or very likely needs to be reinstalled. **This is exclusively a Windows problem for which you need to boot Windows media.** This has NOTHING to do with Ubuntu or Grub.
Please make a Windows bootable USB by following instructions at Microsoft's and preferably from another Windows computer (just plug in any 8GB or larger USB stick and the Microsoft's download page, in Windows, will do everything for you), boot from it and either follow recovery instructions or reinstall Windows. That's all. If you need additional help for Windows then please ask in a Windows forum.

---

### Post by slickymaster on 2020-04-07
Closed.

Please don't start duplicate threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

