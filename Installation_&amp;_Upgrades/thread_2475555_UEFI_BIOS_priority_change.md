---
title: "UEFI BIOS priority change"
date: 2022-05-31
forum: Installation &amp; Upgrades
---

### Post by megahertz2 on 2022-05-31
I have set Win 7 as may priority boot OS in my UEFI BIOS.
I launch Lubuntu using the boot menu (F12) during POST
Every time I do an update or run update-grub the BIOS priority boot OS is changed to Lubuntu.
How to prevent this to happen?

---

### Post by ubfan1 on 2022-05-31
Check your UEFI settings, and see if you can "lock" the boot priority order.

---

### Post by adfhnapo on 2022-06-01
You may need to tell grub not to set Ubuntu as the default.

---

### Post by megahertz2 on 2022-06-01
> **parcelistsupport said:**
> You may need to tell grub not to set Ubuntu as the default.Do you know how to do it?

---

### Post by VMC on 2022-06-02
What does ```
efibootmgr
```show?

---

### Post by tea for one on 2022-06-02
Changing Grub configuration can be a bit daunting, especially when you end up with a non-booting PC.
Therefore, you should always back up your existing working Grub and know how to restore it.

This is my configuration from /etc/default/grub
```
GRUB_DEFAULT=0 [COLOR="#0000FF"]Grub counts menu entries from 0 (zero) [/COLOR]
GRUB_TIMEOUT_STYLE=menu [COLOR="#0000FF"]I always want to see grub[/COLOR]
GRUB_TIMEOUT=10 [COLOR="#0000FF"]I like a lot of time to decide[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=true [COLOR="#0000FF"]I have already probed therefore no need to change[/COLOR] true [COLOR="#0000FF"]to[/COLOR] false
```

When Grub appears on my PC, my menu entries are:-

Ubuntu
Advanced options for Ubuntu
UEFI Firmware Settings
Windows Boot Manager (on /dev/sda1)
Xubuntu 22.04 (on /dev/sda2)
Advanced options for Xubuntu 22.04 (on dev/sda2)

Windows Boot Manager is listed entry no. 4, but, remember that Grub starts counting from 0 so for Grub it becomes no. 3.
To make this a default in Grub
```
GRUB_DEFAULT=3 [COLOR="#0000FF"]Grub counts menu entries from 0 (zero) [/COLOR]
```

Don’t forget to run [COLOR="#0000FF"]sudo update-grub[/COLOR] after editing the file.

---

### Post by megahertz2 on 2022-06-04
> **tea for one said:**
> Changing Grub configuration can be a bit daunting, especially when you end up with a non-booting PC. Therefore, you should always back up your existing working Grub and know how to restore it.  This is my configuration from /etc/default/grub ```
GRUB_DEFAULT=0 [COLOR="#0000FF"]Grub counts menu entries from 0 (zero) [/COLOR] GRUB_TIMEOUT_STYLE=menu [COLOR="#0000FF"]I always want to see grub[/COLOR] GRUB_TIMEOUT=10 [COLOR="#0000FF"]I like a lot of time to decide[/COLOR] GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX="" GRUB_DISABLE_OS_PROBER=true [COLOR="#0000FF"]I have already probed therefore no need to change[/COLOR] true [COLOR="#0000FF"]to[/COLOR] false
```  When Grub appears on my PC, my menu entries are:-  Ubuntu Advanced options for Ubuntu UEFI Firmware Settings Windows Boot Manager (on /dev/sda1) Xubuntu 22.04 (on /dev/sda2) Advanced options for Xubuntu 22.04 (on dev/sda2)  Windows Boot Manager is listed entry no. 4, but, remember that Grub starts counting from 0 so for Grub it becomes no. 3. To make this a default in Grub ```
GRUB_DEFAULT=3 [COLOR="#0000FF"]Grub counts menu entries from 0 (zero) [/COLOR]
```  Don’t forget to run [COLOR="#0000FF"]sudo update-grub[/COLOR] after editing the file.  I have my boot loaders independent (On same EFI partition) Windows boot loader doesn't have Lubuntu option and Grub doesn't have Windows option (I nave moved  30_os-prober and 30_uefi-firmware from /etc/grub.d to /etc/grub.d/Orig so /boot/grub/grub.cfg does not have UEFI Firmware Settings or Windows Boot Manager )  What I want to know is how  to prevent update-grub  from changing BIOS boot priority to Lubuntu

---

### Post by megahertz2 on 2022-06-04
> **VMC said:**
> What does ```
efibootmgr
```show?  BootCurrent: 0003 Timeout: 2 seconds BootOrder: 0000,0004,0003,0006,0005,0001 Boot0000* Windows Boot Manager Boot0001* Windows Boot Manager Boot0003* ubuntu Boot0004* Windows Boot Manager Boot0005  Hard Drive Boot0006  CD/DVD Drive  Boot0000 must be Win 7 on M.2 drive Boot0001 must be Win 7 on SSD drive Boot0003 is  Lubuntu  All other boot options are disabled

---

### Post by tea for one on 2022-06-04
> **megahertz2 said:**
> I have my boot loaders independent (On same EFI partition) Windows boot loader doesn't have Lubuntu option and Grub doesn't have Windows option (I nave moved  30_os-prober and 30_uefi-firmware from /etc/grub.d to /etc/grub.d/Orig so /boot/grub/grub.cfg does not have UEFI Firmware Settings or Windows Boot Manager )  What I want to know is how  to prevent update-grub  from changing BIOS boot priority to Lubuntu

Do you have two operating systems on one disk?

---

### Post by megahertz2 on 2022-06-05
Yes, I have Win 7 and Lubuntu on a M.2 drive and Win 11 on a 2.5" SSD. As I said completely independent.

And yes, I have already cleaned old kernels

---

### Post by tea for one on 2022-06-06
Now that you have 2 disks, there is more than one solution:-

Remove Lubuntu from the M.2 drive.
Install Lubuntu on the 2.5" SSD with Windows 11.
You may have to repair the Windows boot manager on the M.2 disk.
Set the M.2 disk containing only Windows 7 as first boot priority via UEFI settings.

Alternatively, leave all systems in place.
Set the M.2 disk as boot priority.
Configure Grub to boot Windows 7 as default.

I suspect that your UEFI firmware will allow you to prioritise the disk but not the OS if more than one OS is on the same disk.
Hence, you use the boot loader to control the priority i.e.Grub.
Grub allows you to boot Windows but the Windows boot manager can not boot Linux systems.

You are aware that, since January 2020, Windows 7 is now unsupported.
I hope that you are not using it to connect to the internet.

---

