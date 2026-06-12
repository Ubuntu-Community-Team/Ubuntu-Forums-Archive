---
title: "Not able to install ubuntu on lenovo e490"
date: 2019-10-31
forum: Installation &amp; Upgrades
---

### Post by jasmeen3 on 2019-10-31
I am trying to install ubuntu-18.04.3-desktop-amd64 (LTS) on my laptop (lenovo e490) where windows 10 is pre-installed on SSD.
i am trying to install linux on other HDD.

it was an showing an error(the partition table format in use on your disks normally require you to create a separate partition for boot loader code. This partition should be marked for use as a "Reserved BIOS boot area" and should be at least 1 MB in size. note that this is not the same as a partition mounted on /boot.) 

so i created the partitions where i gave separate space to biosgrub as 5mb given in image2. it started installing normally but while installing grub it gave fatal error of grub.
then i pressed ok.
then it gave how would you like to proceed below options.

choose a different device to install the bootloader on
continue without a bootloader
cancel the installation.

after that it is getting stuck.

---

### Post by oldfred on 2019-10-31
If you have pre-installed Windows, then it is installed in UEFI boot mode.
And if installer is asking for the bios_grub 1MB partition, then you have a gpt partitioned drive, but are installing in the old BIOS boot mode.
While if on separate drives, you can install in different boot modes, you can then only boot from UEFI boot menu, not from grub menu.

How you boot install media, UEFI or BIOS is then how it installs. Your UEFI should offer two boot options for Ubuntu live installer. Once clearly UEFI:flash and other just flash where flash is name or label of your flash drive. My system calls them all PMAP.

Many systems, even if new, need UEFI update and SSD firmware update.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 
 More info & links in link below in my signature.

---

### Post by jasmeen3 on 2019-11-12
after completing all the steps. it showed installation finished, restart the computer. After restarting, again windows came.

while installing, i created 50mb reserved bios space. without this step i am not able to move forward in the installation step.

i selected both (UEFI and legacy). because if i am enabling only UEFI, then my usb is not getting detected. a screen will come where we need to select the boot option like usb, pci lan etc. there if i select my usb it is not going to the next step, it will come back to the same option.

---

### Post by oldfred on 2019-11-12
If Windows is UEFI, you really need to have Ubuntu in UEFI boot mode.
And if using bios_grub you are booting in BIOS boot mode, not UEFI.

Have you updated UEFI firmware?
How did you make flash drive installer. Some software may make it UEFI only or BIOS only. Check how you made it.
Ubuntu ISO is designed for either UEFI or BIOS boot, normally how you select in UEFI boot menu.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by jasmeen3 on 2019-11-13
[COLOR=#000000]Have you updated UEFI firmware?
ans : i bought my laptop last month. Kindly find below the version of uefi.

[/COLOR]wmic bios get smbiosbiosversion
SMBIOSBIOSVersion
R0YET27W (1.10 )

Can u explain more about below step?
[COLOR=#000000]How did you make flash drive installer. Some software may make it UEFI only or BIOS only. Check how you made it.[/COLOR]

---

### Post by oldfred on 2019-11-13
You need to compare your version with the most current version that vendor has. 

It depends on what software you used to create live install flash drive.


I saw this example that shows Rufus which many use. But the screenshot of Rufus is a BIOS install. It says MBR and UEFI/CSM. 
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

You just need to be sure if you have choices to select UEFI or UEFI only.

Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or 
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)
Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by jasmeen3 on 2019-11-14
Thanks a lot....
ubuntu installed successfully.
previously i used yumi to make usb bootable, but now i used rufus in which i selected gpt (uefi non csm). then i followed the steps.

---

### Post by ubfan1 on 2019-11-15
Did you update your BIOS/firmware?  Current is 1.20, not 1.10.   See [https://pcsupport.lenovo.com/us/en/downloads/ds506071](https://pcsupport.lenovo.com/us/en/downloads/ds506071)

---

