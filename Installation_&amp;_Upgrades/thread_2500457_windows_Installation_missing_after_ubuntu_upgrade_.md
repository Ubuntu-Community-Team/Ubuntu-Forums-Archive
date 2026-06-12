---
title: "windows Installation missing after ubuntu upgrade on a dual boot setup"
date: 2024-09-02
forum: Installation &amp; Upgrades
---

### Post by dileepkushwaha on 2024-09-02
I recemtly upgraded ubuntu 22.04.4 to 22.04.1 and after that Windows is missing. 
I came across thi spost and i am following the steps recommened on it.
The bott repir iformation is available at [https://paste.ubuntu.com/p/YKPTzvb9J7/](https://paste.ubuntu.com/p/YKPTzvb9J7/)

Let me know if i can go ahead with the boot repair to recover my Windows partition. or do i need to do something else?
NOTE: I need windows 11 and no other windows installtion the tool is detecting. 

Thanks.

---

### Post by yancek on 2024-09-02
Go to the file /etc/default/grub and check to see if you have the line below in that file.  If it is not there put it there by using a text editor with root/sudo.  Then run sudo update-grub.  If you have that line in the file, post back. 

```
 GRUB_DISABLE_OS_PROBER=false
```

Reinstalling Grub as recommended in boot repair will likely not do anything as you already have Grub in the MBR pointing to the correct Grub files on your Ubuntu partition.
Ubuntu recently changed this from having os-prober enabled by default on install to having it disabled.

---

### Post by oldfred on 2024-09-03
Line 225 shows a Windows entry.

Grub only boots working Windows, or Windows that has fast startup off, bitlocker off, and does not need chkdsk.
You then have to boot Windows directly. You do show Windows boot entries in MBR of sda & sdb. 
Or boot a Windows repair/recovery flash drive to turn off settings. Windows updates often turns those settings back on.

You have the very old BIOS/MBR configuration last used by Windows 7. Since Windows 8 Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives. And it requires old MBR(msdos) for BIOS boot or gpt for UEFI boot.

Best to plan conversion to UEFI with gpt. But most tools that convert from MBR to gpt totally erase drive, so good backups required.
With Ubuntu/Linux you can boot from gpt partitioned drives with UEFI or BIOS, if you have correct partitions. BIOS requires a bios_grub partition and UEFI requires an ESP - efi system partition. When first converting from BIOS to UEFI, I added both bios_grub & ESP to new or totally reformatted drives.

---

### Post by tea for one on 2024-09-03
> **oldfred said:**
> Best to plan conversion to UEFI with gpt. But most tools that convert from MBR to gpt totally erase drive, so good backups required.
Yes, this is the way forward - more robust in the future.
Also, you have three disks, therefore, you have the choice of installing Windows 11 and Ubuntu 24.04 on separate disks.
Each disk in UEFI mode with GPT and a separate EFI System partition for each OS.
Use the PC boot menu to choose which disk to boot.

---

