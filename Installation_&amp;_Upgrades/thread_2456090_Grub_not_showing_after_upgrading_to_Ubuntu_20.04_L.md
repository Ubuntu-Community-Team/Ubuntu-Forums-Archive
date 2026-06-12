---
title: "Grub not showing after upgrading to Ubuntu 20.04 LTS with Windows 10 dualboot"
date: 2021-01-04
forum: Installation &amp; Upgrades
---

### Post by pcba-dev on 2021-01-04
I recently upgraded from Ubuntu 18.04 LTS to 20.04 LTS which is installed alongside with Windows 10. After the upgrade Grub menu is not displayed on the laptop screen, although I am able to move and select the different entries with the arrow key during the time-out.

I have tried boot-repair without success, with the following report:
paste.ubuntu.com/p/KvDhsjV8q3/

Note: I previously had Manjaro which I replaced by Ubuntu, however it seems I did not remove correctly during the installation process since in the boot-repair report it is still showing.

---

### Post by oldfred on 2021-01-04
Boot-Repair shows it reinstalled grub without error & grub has Windows entry.
Grub only boots working Windows.
So if Windows update turned fast start up back on, then you have to turn it off again.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

With UEFI, you have to manually remove UEFI entries that are not valid anymore.
You can use efibootmgr. See:
man efibootmgr

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B

Report did not show another folder in /EFI, but if you have one that is /EFI/Manjaro, you can remove it also. Some distributions use /EFI/grub, all Ubuntu official flavors and many others based on Ubuntu use /EFI/ubuntu as folder & UEFI boot entry.

---

### Post by tea for one on 2021-01-04
If it is only a matter of the grub menu not visible when you power on the PC, you can edit the configuration:-

```
sudo nano /etc/default/grub
```

Change GRUB_TIMEOUT_STYLE from [COLOR="#FF0000"]hidden[/COLOR] to [COLOR="#0000FF"]menu[/COLOR]

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Ctrl O to save and Ctrl X to exit.

```
sudo update-grub
```

Reboot - any joy?

---

### Post by pcba-dev on 2021-01-04
> **oldfred said:**
> Boot-Repair shows it reinstalled grub without error & grub has Windows entry.
Grub only boots working Windows.
So if Windows update turned fast start up back on, then you have to turn it off again.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

With UEFI, you have to manually remove UEFI entries that are not valid anymore.
You can use efibootmgr. See:
man efibootmgr

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B

Report did not show another folder in /EFI, but if you have one that is /EFI/Manjaro, you can remove it also. Some distributions use /EFI/grub, all Ubuntu official flavors and many others based on Ubuntu use /EFI/ubuntu as folder & UEFI boot entry.

Indeed Windows had turned back on the [COLOR=#000000]Fast Start up, setting it to NORMAL (off) did the trick. [/COLOR][COLOR=#000000]I also deleted the Manjaro entry with [/COLOR][COLOR=#000000]efibootmgr as you suggested.

[/COLOR][COLOR=#000000]T[/COLOR]hank you very much for the fast responses and your help[COLOR=#000000]!


[/COLOR]

---

