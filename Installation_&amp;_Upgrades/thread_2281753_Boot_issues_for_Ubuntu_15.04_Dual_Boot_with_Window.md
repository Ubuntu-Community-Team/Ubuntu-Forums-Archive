---
title: "Boot issues for Ubuntu 15.04 Dual Boot with Windows 7 on a two hard drive system"
date: 2015-06-09
forum: Installation &amp; Upgrades
---

### Post by Nordmannnick on 2015-06-09
Hi there,

I have a two disk, Windows Ubuntu Dual boot that I have tried to setup. Windows has been installed since it was assembled. Currently, I keep having to intervene with recovery CDs to boot into a particular OS since GRUB2 (which resides on my 2TB HDD) does not seem to acknowledge Windows (which is booted from my much smaller SSD).

My installation process consisted of a poor attempt at a minimal .iso installation which I then promptly overwrote with a fresh LiveCD installation.

To modify my setup to allow Windows booting I have used the Windows 7 created recovery CD and these commands:

```
bootrec.exe /fixboot
```

```
bootrec.exe /fixmbr
```

(as suggested here: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader))

A bootable USB drive with boot-repair works to restore Ubuntu with stanadard options output at: [http://paste.ubuntu.com/11670246/](http://paste.ubuntu.com/11670246/)

I tried an option to force the recognition of Windows (or similar) and got output of: [http://paste.ubuntu.com/11670328/](http://paste.ubuntu.com/11670328/)

Grub customizer and Gparted confirm that the swap is functioning and bootable, and that the Windows System Reserved partition is functioning and flagged as booting. However, irrespective of the Bios preferences chosen, each attempted fix seems to mearly overwrite the other OS. Any help is appreciated.

Regards,

Nordmann

---

### Post by oldfred on 2015-06-09
Boot-Repair defaults to installing grub to all MBR. With two drive systems that usually is not what you want. Use advanced mode and install a Windows (like) or use your Windows repair CD or flash drive to restore the Windows boot loader to sda.
But then go into UEFI/BIOS and set sdb drive as default. You must be in BIOS or CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You seem to have a newer system with UEFI as Boot-Repair says it is running in UEFI mode. Always boot in CSM mode since both Windows & Ubuntu are in BIOS boot mode on MBR partitioned drives.
You should see two boot options for Ubuntu live installer. One clearly will say UEFI - and name/label of flash drive and the other just the name of the flash drive. The second one with just the name is the one you need to use.
You may only see description, from UEFI boot menu that Boot-Repair posted:
      
```
 Boot0005* [COLOR=#ff0000]UEFI: [/COLOR][COLOR=#0000ff]USB Flash Drive[/COLOR][COLOR=#ff0000][/COLOR] PMAP    ACPI(a0341d0,0)PCI(14,0)USB(b,0)AMBO
Boot0006* [COLOR=#0000ff]USB Flash Drive[/COLOR] PMAP    [COLOR=#ff0000]BIOS[/COLOR](1,0,00)AMBO


```    
This also shows the first screen you see, either purple BIOS or grub menu.
      
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
    
Once booted in Ubuntu from MBR of sdb in BIOS mode try this.
sudo update-grub

I am assuming when in UEFI mode it is not finding a Windows UEFI boot to add to grub menu and may the work when in BIOS mode. Otherwise we can manually add a boot stanza for Windows like we did before os-prober worked well.

Since you have a newer UEFI system, you may want to think about converting new drives or any drive you totally reformat to gpt partitioning with an efi partition at beginning. If you still want BIOS boot you need a bios_grub. Windows only boots from gpt partitioned drives with UEFI. And Windows 7 can be installed in UEFI mode, but requires flash drive installer to be modified slightly to work with UEFI. Ubuntu will boot in BIOS or UEFI boot modes from gpt.

Advantages are not huge, but more for future compatiblity. I started using gpt with 10.10 in BIOS mode with Windows XP on another MBR drive. And all new drives and larger flash drives are now gpt.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by Nordmannnick on 2015-06-10
Thank you very much. Setting boot mode to "Legacy" and setting sdb as above sda in the boot order, in the BIOS settings, booting into Ubuntu and then running

```
sudo update-grub
```

sorted everything out. I now have two Windows entries (one from each drive), but either one seems to work. Your help made the process of sorting it out very painless.

---

### Post by oldfred on 2015-06-10
Glad it worked. :)

Boot-Repair started copying the boot files from Windows boot partition because so many users just deleted the 100MB Windows boot partition. Windows does not show it and then newer users do not think they need it and deleted it. If they did not have backups then very difficult to repair.
Then grub finds boot sets of Windows boot files and offers both.

---

