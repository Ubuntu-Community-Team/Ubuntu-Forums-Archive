---
title: "Windows 7 won't boot after installing Ubuntu 14.04 LTS"
date: 2014-08-29
forum: Installation &amp; Upgrades
---

### Post by Rene_Rasmussen on 2014-08-29
Hi there,

I can't boot Windows after having installed Ubuntu - I have tried using Boot Repair - the GRUB menu now shows but Windows is not there...

Details: [http://paste.ubuntu.com/8178215/](http://paste.ubuntu.com/8178215/)

---

### Post by christopher9 on 2014-08-29
What install option did you use ?  Does Ubuntu boot ?

---

### Post by Rene_Rasmussen on 2014-08-29
I installed Ubuntu in its own partition and, yes, Ubuntu is booting.

I wasn't given the option of installing along Windows 7 - so I chose "Something else" and selected a partition for Ubuntu.

---

### Post by yancek on 2014-08-29
The boot repair output for the parted and fdisk commands shows windows systems on sda1 (boot partition) and sda2 (system partition).  If you look at the menu file for Grub (grub.cfg) you will see that there is no entry for windows so it can't be booted.  Another curious thing at the top of the script is that it shows sda1 and sda2 as filesystem unknown.  It usually will show ntfs for windows.  Did you do a full shut down of windows 7 before installing Ubuntu?  You might have a problem with the windows filesystem but I really don't know.  You could try booting Ubuntu and running:  sudo os-prober, watch the output to see if any windows is detected and if so run:  sudo update-grub.  If that doesn't work you probably need to use your windows installation or recovery medium to do a repair.

---

