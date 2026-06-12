---
title: "Windows 8.1 boots but no MBR for Unbutu 14.04 install"
date: 2015-07-02
forum: Installation &amp; Upgrades
---

### Post by paf2 on 2015-07-02
I just installed Ubuntu 14.04 and I don't seem to have a MBR. My Windows 8.1 boots just fine and it even asks me what OS I want but the Ubuntu option get a error. Booth OS are one the same drive and I have a swap partition, /, and /home.


Here is a copy of the boot repair info

[http://paste.ubuntu.com/11809795/](http://paste.ubuntu.com/11809795/)


FYI, I am just getting into Linux so dumb it down for me please.


Thanks for any help

---

### Post by oldfred on 2015-07-02
UEFI systems do not use MBR, so that is correct.

It looks like you originally installed wubi. Is that the ubuntu entry you are seening. It will not work.
       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)
Best to totally remove wubi to avoid confusion.
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

You should be able to boot Ubuntu from UEFI boot menu or one time boot key, often f10 or f12.

Are you getting errors from directly booting Ubuntu, also?

Some Toshiba's need grub or shim copied into the /EFI/Boot folder in the ESP - efi system partition. And then renamed to bootx64.efi. Then you can boot hard drive entry, your UEFI: Samsung SSD 840 EVO entry shown by:
sudo efibootmgr -v

 Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)

---

### Post by paf2 on 2015-07-03
I tried to uninstall  WUBI but it says it cant find it. Here is what happens when I boot.

1. On the UEFI screen I click the Ubuntu option.
2. Computer restarts on it's own.
3. After Bios splash screen I get a error.
4. It reads like this

Windows boot manager

Windows failed to start. A recent hardware or software change might be the 
cause. To fix the problem:

1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer
manufacturer for assistance.

File: \Ubuntu\winboot\wubildr.mbr

Status: 0xc0000225

Info: The application or operating system couldn't be loaded because a
required file is missing or contains errors.


I can't find the file in the location they are talking about.

---

### Post by oldfred on 2015-07-03
That error is from Windows and from its BCD.
Wubi adds a boot entry to Windows BCD. The uninstall should remove it, but since wubi does not fully work with Windows 8 and gpt partitioning, you may have to remove it yourself.

You cannot use Linux tools to edit BCD. Best to use your Windows repair flash drive that you made when Windows said to on first boot.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)


 BCDboot Command-Line Options Windows Vista/7/8 recreates boot files.
[http://technet.microsoft.com/en-GB/library/hh824874.aspx](http://technet.microsoft.com/en-GB/library/hh824874.aspx)

 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)

---

### Post by paf2 on 2015-07-03
Just a update, I got Ubuntu and windows to boot but......I have to change the BIOS if I want to switch. CSM Boot= Linux auto boot. UEFI Boot= Windows 8.1 auto boot. After I tried to get rid of the Wubi from your first post, I then reinstalled without it and that's what happened. Is there a way around that? The good news is that I can use both OS but it is a funny way around.

---

### Post by oldfred on 2015-07-04
UEFI & BIOS are not really compatible. You cannot dual boot from grub menu as once you start booting in one mode, you cannot switch to the other.
You can only dual boot as you have found out from UEFI menu or one time boot key.

Best to have Ubuntu installed in UEFI mode to match Windows. You can easily convert Ubuntu install to UEFI with Boot-Repair and its advance mode. Be sure to boot Boot-Repair in UEFI mode and do a total uninstall reinstall of grub, so you get grub-efi-amd64(UEFI) instead of grub-pc(CSM/BIOS).

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do not reinstall Ubuntu unless you use Something Else. Any auto install option may overwrite entire hard drive. See caution in link in my signature below.

---

