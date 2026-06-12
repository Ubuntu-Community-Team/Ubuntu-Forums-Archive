---
title: "Dual booting Windows 10 with Ubuntu 16.10, GRUB screen not showing"
date: 2017-03-24
forum: Installation &amp; Upgrades
---

### Post by noobz3 on 2017-03-24
I've recently bought a laptop (Lenovo Ideapad 110-14AST) post-installed with Windows 10. Then I attempted to dual-boot with Ubuntu 16.10, everything worked perfectly (except that the graphics was all messy). After the installation, it wanted me to restart the PC. After I restarted the pc, usually the GRUB screen showed up, but it didn't. Instead Windows 10 automatically boots up, no GRUB screen.

I installed Ubuntu in four separate partition. One for files (\home), one for swap (\swap), i also set one for \ , and one for GRUB reserved space (\bootgrub or something like that)

I've searched fixes in other forums, and all of them have something to do with UEFI boot order. So I opened UEFI settings, and in the boot order, i don't see the GRUB config. This is the current boot order :
1. HDD Drive
2. Windows Boot manager
3. USB HDD
4. USB FDD
5. Realtek
6. USB CD

I've tried everything in the UEFI config, turning off and on this and that, nothing happens. At this point, i don't know what to do now. And i need answers as SOON as possible (school's exam reasons)

(and NO, i don't want to reset my PC)

---

### Post by oldfred on 2017-03-27
With UEFI you should not have a bios_grub as that is only used for Legacy/CSM/BIOS boot.

Both Windows need to be installed in same boot mode, both UEFI or both BIOS.
Boot-Repair can convert a BIOS install to UEFI, just by reinstalling the correct version of grub.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

