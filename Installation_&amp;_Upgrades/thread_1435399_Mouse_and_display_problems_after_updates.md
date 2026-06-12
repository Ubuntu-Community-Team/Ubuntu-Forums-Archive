---
title: "Mouse and display problems after updates"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by 61811 on 2010-03-21
Went through a regular software update that Ubuntu publishes. However, this was the first update after an issue I had with GRUB and XORG.CONF a couple of weeks ago (due to WinXP disk crash, and new monitor). This update needed a **_reboot_**.

**_Kernel:_** 2.6.24-27-generic
This kernel has been running fine for a long time. My menu.lst was not updated after the software update. Not sure if that is the issue.

**_Symptom:_** System (dual-boot) boots up fine with GRUB. Choose Ubuntu 2.6.24-27-generic (the only Ubuntu option in my GRUB) and able to get past login. Desktop appears with two problems:
1) Mouse cursor is invisible (things get highlighted when mouse is moved, but cannot see the cursor; hence, have to go by the "feel" as to where the cursor may be)
2) Display size has shrunk.
3) Third problem is not with desktop. When trying to restart system, it hangs with distorted display. Have to power cycle the machine.

**_Questions:_**
* What could have gone wrong with the update? What should I check and correct?
* Or, is there a way to restore to previous state before the last update? (I do have a LiveCD).

Thank you.
(Working off my WinXP right now).

---

### Post by 61811 on 2010-03-21
(1) Used tip from LinuxMint forum:
Remove, install and reconfigure XORG.
[I]sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg[/I]

(2) Then, uninstalled ATI display driver from /usr/share/ati.
*sh ./fglrx-uninstall.sh*
Reboot

(3) Reinstall ATI driver.
*sh ./ati-driver-installer-10-2-x86.x86_64.run*

(4) Configure the ATI driver (xorg.conf file will be modified).
*/usr/bin/aticonfig --initial*
Reboot

(5) Specific to my display monitor (Acer H235H), but may help someone else:
The display does not expand to the full extent of the monitor's capability though the resolution was correctly set at 1920x1080.
Open ATI's Catalyst Control Center under System > Preferences and go to DTV under Display Manager. Click on Adjustments tab, and under Scaling Options drag the scroll bar to max. (i.e. Overscan .. 0%). The display will simultaneously expand to the full extent of the monitor.

---

