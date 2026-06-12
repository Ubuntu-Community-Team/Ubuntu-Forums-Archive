---
title: "&quot;8.10&quot; upgrade, no mouse in X, cannot log in to GDM"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by nmltom on 2008-11-12
I have looked at other threads and tried various fixes, but nothing seems to help.

I upgraded 6.06 to 8.04 to 8.10 following the instructions on the Ubuntu site and everything seemed to go fine. However, when I finished, the Gnome login screen comes up but is frozen. I cannot type in my login info and the mouse does not move at all.

Any help getting X working again would be appreciated.

Attached are my hardware and dmesg files.  Thank you.

---

### Post by Crafty Kisses on 2008-11-12
Try booting into recovery mode from the GRUB menu and at the prompt, reconfigure your X server.
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now

```
Once it's rebooted and you are able to login once again, look in System ---> Administration ---> Hardware Drivers to see if your graphics card is on the list. Look for the proper driver for your graphics card. Don't forget to go into the BIOS to turn off the onboard graphic card controller first before you boot into the recovery mode from GRUB menu.

---

### Post by alinaqvi on 2008-11-12
I am not sure if the problem stated above and mine are the same. I upgraded from 8.04 to 8.10, all went well, until the computer restarted and I tried to login, the mouse and key board does not work at the graphical interface. 

Any help is appreciated. 

regards

Ali

---

### Post by nmltom on 2008-11-12
Here is what I have done so far:
I rebooted system
From the first menu of options selected generic kernel "recovery mode"
At the recovery menu, selected resume normal boot
That took me to the frozen Gnome login screen
Alt/Ctl F1 to get to command line in terminal
Ran command "sudo kpkg-configure -phigh xserver-org" and here is the standard error output from running that command:
quote

Gtk-WARNING **: cannot open display:  at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 54.
debconf: Unable to initialise frontend: Gnome
debconf: (DISPLAY problem?)
debconf: falling back to frontend: Dialog
Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed.

end quote

I did not go into the BIOS and of course I cannot get into Gnome which is where (I think) you were suggesting I look for the hardware drivers.

What should I try next?  Thx.

> **Codename said:**
> Try booting into recovery mode from the GRUB menu and at the prompt, reconfigure your X server.
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now

```
Once it's rebooted and you are able to login once again, look in System ---> Administration ---> Hardware Drivers to see if your graphics card is on the list. Look for the proper driver for your graphics card. Don't forget to go into the BIOS to turn off the onboard graphic card controller first before you boot into the recovery mode from GRUB menu.

---

### Post by cameronp on 2009-01-22
I followed the 6.06 to 8.04 to 8.10 upgrade path and have the same problem. Mouse and keyboard don't work in X. The keyboard works fine on any of the TTYs.

I have already tried a dpkg-reconfigure and it didn't improve the situation.

---

### Post by windex on 2009-01-28
Not a permanent fix, but may lead to a solution to the problem:

At Xlogin press "Print Scrn" button.  X reloads and the mouse and keyboard start working again.

Dell Lattitude D820; built-in keyboard, and USB mouse.

---

### Post by dave6779 on 2009-02-13
Hey i think i have solution to your problem. I just had exactly the same problem, reinstall ubuntu and format the old / or root partition, if you only have one partition then you will have to format it all otherwise some of your old settings interfere with the new install. You DO NOT have to format your /home partition, should you have one. If you don't have one i suggest you search for ubuntu 8.10 good partitioning or the like to understand how to do it so you can avoid future data loss.

Hope this helps.

Kind regards,

David Swindells

---

