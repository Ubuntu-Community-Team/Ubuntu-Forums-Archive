---
title: "Installed Grub on a sperate drive now my Windows 10 only boots to startup repair"
date: 2024-05-04
forum: Installation &amp; Upgrades
---

### Post by bowiye on 2024-05-04
I installed Ubuntu and Grub onto a seperate SSD although this seems to have broken my Win 10 OS, was hoping for a dual boot

Installed Boot-repair as nothing i have read so far is working, please see the pastebin: [https://paste.ubuntu.com/p/63dwXbnM3T/](https://paste.ubuntu.com/p/63dwXbnM3T/)

I am quite noob with this so sorry if its easy fix, but also hope it is, would appreciate any help here :)

---

### Post by nicolasdentremont on 2024-05-04
I don't know if this will apply to you. When I installed Ubuntu, I had to disable RST in the BIOS settings and set it to AHCI in order to get the Ubuntu installer to boot. If I try to boot Windows without changing it back to RST It will say that the boot device is inaccessible and goes to automatic repair.

---

### Post by bowiye on 2024-05-04
I believe that is for intel only, i am running an AMD CPU, thanks but cant even see those 2 options within my UEFI

---

### Post by nicolasdentremont on 2024-05-04
> **bowiye said:**
> I believe that is for intel only, i am running an AMD CPU, thanks but cant even see those 2 options within my UEFI

Ahh yes RST is Intel.

---

### Post by yancek on 2024-05-04
So what actually happens when you boot?  Does Ubuntu boot?

> I installed Ubuntu and Grub onto a seperate SSD 

That does not seem to be the case from boot repair which shows you have windows on nvme1n1p2 (line 18 boot repair) a 465GB drive.  You have Ubuntu installed on sdc1 on a 232GB drive (Line 179) and both are EFI installs with the EFI files on sda1 shown beginning at line 26.  The grub.cfg file on this EFI partition shows it pointing to the actual grub.cfg file on the Ubuntu partition which is on sdc1.  Do you not see an entry for windows in the Grub boot menu?  Have you run sudo update-grub from Ubuntu and watched the output ot see if a windows entry appears?  If not, enable os-prober in Ubuntu by editing the /etc/default/grub file and adding the line:

> GRUB_DISABLE_OS_PROBER=false 

You need to make this change using a text editor with root privileges (sudo) and save the change and update-grub.

Since both Ubuntu and windows are installed in EFI mode, there should be no problem booting both from Grub, in fact since they are on separate drives it should not matter.

---

### Post by tea for one on 2024-05-04
> **bowiye said:**
> I installed Ubuntu and Grub onto a seperate SSD although this seems to have broken my Win 10 OS, was hoping for a dual boot
[COLOR="#0000FF"]Lines 93 > 95[/COLOR] - 1 OS detected OS#1:   The OS now in use - Ubuntu 20.04.6 LTS on sdc1
Unfortunately, Windows 10 is not visible to the boot-repair report

Your Windows 10 system is (probably) located on nvme1n1p2
This nvme1n1 disk does not have an ESP, therefore can you explain the history of your Windows OS?
For example, was this an upgrade from XP in Legacy mode?

The other puzzle is the nomenclature of disk nvme1n1.
Usually, the first nvme disk is nvme0n1
Can you shed some light on this?

Notwithstanding my observations, please first try the suggestions offered by yancek.

---

### Post by oldfred on 2024-05-04
You also now show UEFI Secure Boot on.
Sometimes a Windows update also updates UEFI firmware resetting to defaults which may turn Secure Boot back on.
You may want to turn it off, but not necessary, but grub may not boot Windows. You just always choose from UEFI boot menu.

You also then with Windows updates may have Windows fast start up turned on. You often have to turn it back off after updates in Windows.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)

Unless the fast startup is on which sets hibernation flag, is then hiding NVMe drive, it does not look like nvme0 is used?

Also the ESP - efi system partition is normally on the same drive as Windows with Windows installs.
Ubuntu normally uses the first drive, whatever first drive is seen by UEFI/BIOS.
Newer versions of Ubuntu now let you choose what drive to have an eSP on.

You also have  very old Windows BIOS boot installed to MBR of nvme1n1 and sdb. Those will never be used, but will not interfere with booting as long as you never choose the old BIOS mode to boot. Windows only boots in UEFI mode from gpt partitioned drives and only in old BIOS mode from MBR partitioned drives. Your sdd seems to have an old install of Windows in the BIOS/MBR configuration. With Secure boot on, that will never boot.

---

### Post by bowiye on 2024-05-04
I have run this before and my Windows OS does appear in the output, rerun for example:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-105-generic
Found initrd image: /boot/initrd.img-5.15.0-105-generic
Found linux image: /boot/vmlinuz-5.4.0-42-generic
Found initrd image: /boot/initrd.img-5.4.0-42-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
done

Ubuntu boots fine, Grub loader seems to work fine, Windows selection is within the Grub loader although selecting it brings up the Windows Startup Repair and it is unable to fix a thing....classic startup repair

---

### Post by bowiye on 2024-05-04
> Have you run sudo update-grub from Ubuntu and watched the output ot see if a windows entry appears?
I have run this before and my Windows OS does appear in the output, rerun for example:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-105-generic
Found initrd image: /boot/initrd.img-5.15.0-105-generic
Found linux image: /boot/vmlinuz-5.4.0-42-generic
Found initrd image: /boot/initrd.img-5.4.0-42-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
done

Ubuntu boots fine, Grub loader seems to work fine, Windows selection is within the Grub loader although selecting it brings up the Windows Startup Repair and it is unable to fix a thing....classic startup repair

> This nvme1n1 disk does not have an ESP, therefore can you explain the history of your Windows OS?
Windows OS was a clean install when the machine was built, many other older drives from the PC before though, Win OS is a Samsung 980 512GB NVME, Ubuntu is a seperate 256GB Sata SSD, cant remember what type, is just an old drive from the cupboard

> For example, was this an upgrade from XP in Legacy mode?
This machine has never had XP on it, no idea where that came from im afraid.

> The other puzzle is the nomenclature of disk nvme1n1.
Usually, the first nvme disk is nvme0n1\
Best guess is the 512GB ssd is in the 2nd NVME slot on the MOBO and i have a seperate NVME in slot 1, this is only a guess though, cant think of any other reason for this.

---

### Post by oldfred on 2024-05-04
Does Windows boot directly from UEFI boot menu, not from grub.
If so then it is UEFI Secure boot, or if not a Windows issue.

---

### Post by bowiye on 2024-05-04
Windows boots from UEFI but still just into startup repair, this only began when i installed ubuntu, could it have broken my bootloader, is there a way to fix it?
I have read elsewhere of Windows having the startup repair on a different petitiion to the main OS and the boot loader just pointing to the wrong pettition although i couldnt see a way to check this myself, does this sound like a possibility and any idea how to check for this error?

I am yet to run boot-repair, if this is a tool you have worked with before or understand the options for, can you let me know if there is a fix here that i can easily utilise?

---

### Post by tea for one on 2024-05-05
Before attempting any repair, ensure that you have _backups_.
> **bowiye said:**
> Windows boots from UEFI but still just into startup repair 
Boot-repair is not designed to fix Windows boot problems.
You'll need a Windows ISO on a USB - it has various repair facilities and there are many helpful internet resources available.
> **bowiye said:**
> this only began when i installed ubuntu, could it have broken my bootloader, is there a way to fix it?
Did you try any repairs offered by boot-repair?
If you only allowed it to produce a report, then it would not "break" anything.
> Windows OS was a clean install when the machine was built
Therefore, disk nvme1n1 would contain an ESP, but your ESP is on another disk?
Assuming Windows 10 is located on nvme1n1p2, you should not have the following line:-
[COLOR="#0000FF"]Line 6[/COLOR] - Windows is installed in the MBR of /dev/nvme1n1
The efi files for Windows are on sda1 (see lines 35 and 36)

It's worth the effort to try and repair Windows 10 with Microsoft tools.
Hopefully, it is successful.
Again, please don't do anything without backups.

---

### Post by yancek on 2024-05-05
I would also suggest you use windows tools to repair whatever problem you have with booting windows.  There are some strange things with your setup, particularly having the EFI partition on a separate hard drive, very unusual.  Boot repair usually shows the boot file on the primary windows system partition, your output does not.  If your windows boot files located on the system partition are corrupted or missing, there is no way for boot repair to help with that as generally all it does is create an entry in the boot menu to chainload the windows boot files.

---

### Post by oldfred on 2024-05-05
Boot-Repair report almost always shows this:
sudo efibootmgr -v

You should have at least two entries one for Windows & one for Ubuntu that use partUUID of ESP - efi system patition.
Your line 212 in report shows partuuid of ESP.
Or to see partuuid & other partition info:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

---

