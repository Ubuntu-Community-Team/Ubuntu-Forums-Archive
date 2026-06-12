---
title: "After installing 13.04 alongside Windows and running Boot Repair, PC will not boot"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by tusseyd on 2013-07-10
Followed install instructions for Ubuntu 13.04 alongside Windows 8.   Afterwards, PC would only boot into Windows 8.  Followed instructions to run Boot Repair.  ([http://paste.ubuntu.com/5863268/](http://paste.ubuntu.com/5863268/)) At the end, Boot Repair said to "Disable Secure Boot".  Unfortunately, now when I restart the PC, neither Windows 8 or Ubuntu will boot.  PC just freezes with a black screen.  Appears to be unable to get into WIndows 8 to disable Secure Boot.  When the PC boots, the black screen shows only ">>start PXE over IPv4."  Computer is a new Dell XPS 8500 with Windows 8 pre-install with UEFI.

Perhaps there is a way with Boot Repair to re-enable boot to Windows 8 and from there access UEFI to disable Secure Boot?  Thanks. Appreciate the help.

---

### Post by SBJ95 on 2013-07-10
You might be able to use [Super Grub Disk]("http://www.supergrubdisk.org/") to get into your Windows install.  If that doesn't work, you may need to use your Win8 install disk and do a startup repair from there, disable Secure Boot, then run Ubuntu Boot Repair to restore grub et. all.

---

### Post by tusseyd on 2013-07-10
> **SBJ95 said:**
> You might be able to use [Super Grub Disk]("http://www.supergrubdisk.org/") to get into your Windows install.  If that doesn't work, you may need to use your Win8 install disk and do a startup repair from there, disable Secure Boot, then run Ubuntu Boot Repair to restore grub et. all.

I tried using my Windows 8 Rescue Disk, but the PC will not boot off of that.  I just get ">>Start PXE over IPv.4" at the top of the screen.  The rest of the screen is black.

---

### Post by SBJ95 on 2013-07-10
Sounds like it's trying to PXE (network) boot.  Can you make sure your boot order in BIOS is set to boot off CD?

---

### Post by tusseyd on 2013-07-10
Unfortunately, it's not possible to get to the UEFI (...no BIOS with Windows 8) without gaining access to Windows 8.  If I could change the boot order in UEFI, I could disable the Secure Boot, but unfortunately I cannot get Windows 8 to load to do that.  Thanks for your help.

---

### Post by tusseyd on 2013-07-10
I should point out that I can boot into "Try Ubuntu" and run from there.  Specifically I can run Boot Repair, but have been hesitant to attempt using the "Advanced" options, as advised on the Ubuntu.com website install instruction.

---

### Post by SuperFreak on 2013-07-10
How are you trying to access UEFI? On my machine it is by pressing the DEL or F2 key before the OS comes on (I tap the DELETE key repeatedly while booting up)

---

### Post by tusseyd on 2013-07-10
I never get to UEFI...that's the problem.  The PC does not appear to go through any boot sequence at all...or else it goes through the boot process so quickly, that nothing appears at all.  I will try your suggestions however.

---

### Post by tusseyd on 2013-07-10
This part of the [http://paste.ubuntu.com/5863268/](http://paste.ubuntu.com/5863268/) sort of bothers me, because I believe the default Ubuntu install tries to boot off of /dev/sda.  I have both a traditional hard drive, and an SSD.  Could that be /dev/sdb?  


=> No boot loader is installed in the MBR of /dev/sda.  => Windows 7/8/2012 is installed in the MBR of /dev/sdb.  => No boot loader is installed in the MBR of /dev/sdc.

Is there a way to "undo" the Ubuntu install and just get back to a standard Windows 8 config?  Thanks to all for your help.  Sorry this is such a pain.

---

### Post by tusseyd on 2013-07-10
CORRECTION: I can get to the BIOS by pressing "F2" during the boot process.  I have disabled "Secure Boot".  When I boot now, the error is "PXE-E53: No boot filename received.  PXE-M0F: Exiting PXE ROM.  Reboot and Select proper Boot device or Insert Boot Media in selected Boot Device and press a key."

I can then insert the Super Grub dvd and boot to that, but I am unsure of what to do then.  There are many, many options listed.   

Thanks again.

---

### Post by tusseyd on 2013-07-10
Some progress.  I can boot off the Super Grub dvd, and bring up "grub2".  From there I can do a boot to Ubuntu, but the Windows options are both EFI, and give a signature error (Secure Boot is currently disabled, but will try to enable that and retry).

---

### Post by tusseyd on 2013-07-11
[COLOR=#008000]**SOLVED**[/COLOR]:  After resetting the BIOS to "Enable EFI", but leaving "Secure Boot" off, and after first doing a manual boot from dvd for the Super Grub program (and then selecting "Find Grub2"), it now appears that the PC boots to Grub2 menu and either Windows 8 or Ubuntu can be selected.  Victory.  Thanks to all for the help. Combination of several steps yielded success.  Greatly appreciated.

---

