---
title: "Grub install failed. Legacy BIOS was &quot;substituted&quot; by UEFI (boot-repair summary)"
date: 2022-11-02
forum: Installation &amp; Upgrades
---

### Post by iatzak on 2022-11-02
Hello,

I have a computer that ran on Windows 10 and I wanted to install Ubuntu alongside it (dual boot). The computer has Legacy BIOS and MBR partitioning. I checked this info on Windows before installing Ubuntu.

When installing Ubuntu, the error
*Executing 'grub-install /dev/nvme0n1' failed.*
occurred.

After this, I restarted the computer and it entered straight to the GRUB terminal in command line mode. I didn't manage to boot Windows from there. I restarted it again and entered the BIOS. Choosing my HD just brings me back to the GRUB terminal.

I am totally new to this topic and wanted to have Ubuntu alongside Windows to begin my studies. If anyone is willing to take a look, I ran boot-repair (after booting Ubuntu from the USB) and put the output here:
[URL="https://pastebin.ubuntu.com/p/gRyj5nJD3t/"]https://pastebin.ubuntu.com/p/gRyj5nJD3t/
[/URL]In line 340, it says my boot is in EFI mode. Indeed, I ran *efibootmgr* on the terminal and it outputs the usual for a computer with EFI. As I mentioned before, I checked on Windows' System Information and the BIOS Mode was set to Legacy before the installation.

Also, I have checked that now my HD has a new partition with "type" efi. It definitely did not exist before the installation.

According to [https://askubuntu.com/a/1134955](https://askubuntu.com/a/1134955) , I booted from the USB in UEFI mode, since I can see the UEFI Firmware option when booting with the USB: [https://i.stack.imgur.com/wNvaj.png](https://i.stack.imgur.com/wNvaj.png) .

Given this, should I take the advice at line 340 of the boot-repair summary, *retry after changing it to BIOS-compatibility/CSM/Legacy mode*, (I don't know how to change this) or go on and do the Recommended repair in boot-repair?

Thank you in advance!

---

### Post by tea for one on 2022-11-02
It may be worth trying to repair Grub by booting the USB in Legacy mode and running boot-repair.

However, as your PC is EFI compatible, I would give serious thought to installing both Windows 10 and Ubuntu 22.04 in UEFI mode.
More work but you will have a more robust system for the future.

---

### Post by oldfred on 2022-11-02
While grub can normally boot Windows, Windows updates may turn fast start up or change other settings and then grub will not boot Windows.
If UEFI, you just choose Windows in UEFI boot menu and repair or correct settings.

But with BIOS you only have one MBR for booting. 
So you have to temporarily restore the Windows BIOS boot loader to MBR, repair Windows, and restore grub.
You need to always have a  Windows repair flash drive and Ubuntu live installer to make those boot loader changes.

You cannot have both UEFI boot and BIOS boot on same drive.
Windows requires boot flag on its BIOS boot partition, your sda1. You do need to use gparted or Windows tools to move boot flag back to sda1.
The ESP - efi system partition also uses boot flag so cannot be on same drive as Windows in BIOS boot.

Also suggest UEFI install of Windows.
But Windows only installs in UEFI boot mode to gpt partitioned drives. And that conversion totally erases entire drive, all partitions. So good backups required.
Microsoft has required vendors to install in UEFI/gpt mode since 2012. And new systems starting in 2021 are now UEFI only.

---

### Post by iatzak on 2022-11-02
Thank you very much for your advices!

I followed tea for one's first suggestion and now at least I have access to Windows again.

I'll try to convert from MBR to GPT and use UEFI, and then install Ubuntu. I'll mark this thread as solved and open a new one if something goes wrong.

Thank you again!

---

### Post by tea for one on 2022-11-02
Please remember to backup your data (both Windows and Ubuntu) before attempting any major partition changes.

---

