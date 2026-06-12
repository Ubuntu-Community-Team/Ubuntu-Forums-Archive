---
title: "Windows 10 dual boot with Ubuntu 18.10 does not recognize Windows 10 partition"
date: 2018-10-29
forum: Installation &amp; Upgrades
---

### Post by seebol on 2018-10-29
I had a working partition of Windows 10. I then installed Linux Lite 4.0 on a separate disk (using the standard installation image on a usb), and I could select either Linux Lite or Windows 10 upon booting up. I then overwrote the entire disk containing Linux Lite with a fresh installation of Ubuntu 18.10. Now, upon bootup, there was no option to choose Windows 10. Going into BIOS and forcing an attempt to boot up the drive containing Windows 10 gave an error about address not recognized, and a grub command line was shown.

To fix this issue, I reinstalled Linux Lite 4.0 over Ubuntu 18.10. Now I'm back to the original dualboot situation, where everything works.

Does anyone know why Ubuntu 18.10 could not allow dualboot? I came across some forums saying I have to disable hiberation in Windows 10, but it seems like that option is already disabled.

Thank you!

---

### Post by oldfred on 2018-10-29
Really need to see this from Ubuntu, but post current for now.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
How you boot install media UEFI or BIOS is how it installs. And you have to match boot mode of Windows.
If Windows was preinstalled, then it will be UEFI.

---

### Post by seebol on 2018-10-30
Hi oldfred,

Thanks for the reply. I installed Boot-Repair on the working Linux Lite partition and ran it. The results are pasted here: [http://paste.ubuntu.com/p/x5B7v5MyMk/](http://paste.ubuntu.com/p/x5B7v5MyMk/)

---

### Post by oldfred on 2018-10-30
Do not run Boot-Repair's auto fix. It installs grub to every drive.
You want a Windows BIOS boot loader in MBR of sda. Boot-Repair's advanced mode can do that if you select Windows and sda. But Windows cannot be hibernated nor need chkdsk.

But you have mixed boot modes. 
Your sda is Windows in BIOS boot mode. And Windows only boots in BIOS mode from MBR partitioned drives.
Your sdb drive is gpt but you have both a bios_grub partition for BIOS boot and an ESP for UEFI boot. 
Ubuntu's grub really only wants to install in UEFI mode to an ESP on sda, which you do not have.

Generally with new UEFI hardware, you want to install systems in UEFI boot mode using gpt partitioning. 
The BIOS boot mode with MBR goes back to the original PC in mid 1080's and has many fixes to make it still work.

But Also best to have all systems installed in same boot mode. You do not have to, but then can only dual boot from UEFI boot menu, not from grub.
And since difficult to impossible to convert Windows from BIOS/MBR without total reinstall, you may, for now, want to keep sdb as BIOS boot but also as gpt for future use. As long as you have bios_grub partition on sdb, you can boot sdb in BIOS mode.

How you boot install media, UEFI or BIOS, is then how it installs,  so boot Ubuntu live installer in BIOS boot mode, use Advanced options and on partitioning screen be sure to specify grub install to sdb. Also then set UEFI/BIOS to boot sdb. Grub will boot working Windows, but if needs fixes and grub does not boot it, you can directly boot sda, if you have installed the Windows boot loader into sda. Still better to also have a Windows repair flash drive for current version of Windows you have installed. And keep Ubuntu live installer for any Linux repairs.

---

### Post by seebol on 2018-10-30
Thank you for the super informative post oldfred!

---

