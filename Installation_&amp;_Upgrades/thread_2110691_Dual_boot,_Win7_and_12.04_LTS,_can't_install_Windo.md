---
title: "Dual boot, Win7 and 12.04 LTS, can't install Windows 7 SP1"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by oregonbob on 2013-01-30
I have a dual boot system with Windows 7 on the first disk (sda) and Ubuntu 12.04 LTS on a second drive (sdb). I have upgraded/moved Ubuntu a couple of times, but Win7 has always been on the first disk. I have Ubuntu on the second disk and BIOS set to boot from the second disk (sdb). Grub installed on the second disk allows me to select Ubuntu or Windows at boot up just fine. But now I cannot install Windows Service Pack 1. It gives the error that it can find the boot record. If I could boot from the first disk containing Windows it wouldn't have that problem, but I have some old unused grub on the first disk, so when I try to boot it I get error, "Error: no such device..... Entering rescue mode." and it sits at a grub rescue prompt. I assume that at some previous time I installed grub on the first disk that contains Windows.

So I think what I need to do is remove grub from the first disk so it just boots Windows. Or maybe I should rewrite the Win MBR to the first disk that has Windows. Is there an easy/best way to do this?

---

### Post by oldfred on 2013-01-31
I think Windows also know which drive in BIOS is boot drive. Change BIOS to boot Windows directly and boot Windows from that. Then you should be able to run your updates.
Windows may be looking on sdb for Windows boot files as that is the BIOS boot drive.

---

### Post by oregonbob on 2013-01-31
Yes, I know Windows is looking on SDB. I already tried changing the boot drive in BIOS to the Windows disk (sda), but there is an old, unused grub on that disk too. That's why I want/need to either remove that grub on the Windows disk or just rewrite the MBR on that disk. I'm not sure the best way to approach it. Booting from the second drive (with grub) works just fine and I don't want to screw up either Windows or Ubuntu when I fix the Windows disk.

---

### Post by oldfred on 2013-01-31
Install a Windows boot loader to the MBR of the Windows drive. You can use Windows and fixMBR or load any of the many boot loaders that work just like Windows in the MBR. Then you can directly boot Windows.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by LinGNUbie on 2013-02-01
Dualboot Win7+Ubuntu 12.04 on same HD, separate EFI partition.

Just had the same kind of errors, booted into Ubuntu, set boot flag on EFI partition with GParted, boot into windows and retried, success. However there is also an update just before SP1 that I had to do the same with the msftres partition, then after that success, I tried the EFI for SP1 update.

More thorough instructions [here]("http://ubuntuforums.org/showthread.php?t=2111400").

---

### Post by oldfred on 2013-02-01
Only a few Windows 7 were UEFI, most were BIOS/MBR based. So that does make a difference. 

If not sure run the boot info report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by LinGNUbie on 2013-02-01
Evidently there is some updates that are related to the msftres partition, and it may be that setting that flag is necessary for Win7 to "see" that partition in order to update. Of course I had good results from changing this regardless of what the MS tech forums said about using Win7 to use diskpart to make it active. (Which I did NOT do.)

---

