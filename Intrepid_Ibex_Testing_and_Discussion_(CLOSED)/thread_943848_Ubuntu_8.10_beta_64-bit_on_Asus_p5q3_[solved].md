---
title: "Ubuntu 8.10 beta 64-bit on Asus p5q3 [solved]"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by berman56 on 2008-10-10
Well, it was a long ride but I finally got Intrepid Beta installed on my Asus p5Q3 Deluxe/Wifi-AP.  The following is how I did it.  I played with many things and unfortunately didn't do it systematically.  So some of the steps may not be necessary.  With that said:

1) I have a dual boot with Vista.  First, in Vista I switched the registry from SATA - IDE to AHCI according to this:

[http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)

2) Reboot, and in the BIOS.  Configure SATA from IDE to AHCI.  Under advanced USB, change BIOS EHCI Hand-off to disabled.  Also, change ACPI 2.0 to enable.

3) Boot Hardy 8.04 64-bit LiveCD.

4) Choose F6 and add acpi=off at the end of the text.

5) Install Ubuntu.

6) sudo update-manager -d in a terminal.

7) upgrade to 8.10

8) Some error messages came up during installation regarding the networking manager, disregard.

9) Boot into 8.10.  Networking doesn't work.  Network manager says device is unmanaged.  Open a terminal.

10)  sudo gedit /etc/NetworkManager/nm-system-settings.conf

11) under [ifupdown], change managed=true

12) reboot, it worked for me!!

If you have any trouble let me know, I may not be able to help but you will get lots of sympathy.  If I dedicated half the amount of time I wasted getting this working to doing actual work ....

---

### Post by berman56 on 2008-10-12
Also, see this thread for some others who have been successful.

[http://ubuntuforums.org/showthread.php?t=915165](http://ubuntuforums.org/showthread.php?t=915165)

---

