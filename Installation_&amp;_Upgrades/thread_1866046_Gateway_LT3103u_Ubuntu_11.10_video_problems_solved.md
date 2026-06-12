---
title: "Gateway LT3103u Ubuntu 11.10 video problems solved"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by JoeJoe33 on 2011-10-20
[B]
Scrambled graphics/display on Gateway LT3103u running Ubuntu 11.10 with X1200 video adapter/card:
[/B]

lspci | grep  Radeon
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
[B]

How I fixed it:[/B]

ctl-alt-f1 to console and log in

sudo service lightdm stop

sudo X -configure

This Output is fine:
Configuration failed.
ddxSigGiveUp: Closing log

ls -ltr to show new file xorg.conf.new
 

Edit xorg.conf.new with "sudo vi xorg.conf.new" or "sudo nano xorg.conf.new" and change the line:

Driver "radeon"
to
Driver "vesa"


Copy new file to /etc/X11 minus the .new suffix
sudo cp xorg.conf.new /etc/X11/xorg.conf

verify new /etc/X11/xorg.conf file is in place
ls -ltr /etc/X11/xorg.conf

Reboot with:
sudo init 6


Graphic should be good now. no 3d though, just unity 2d, fine for me

---

### Post by rodspi on 2012-02-11
Change the driver in xorg.conf file to vesa does work, but it signficantly compromises performance. I just fixed my LT3103u last week.

I follow these links to fix the issue using the ati/radeon driver with kms (kernel mode setting) enabled. KMS is what causes the crazy graphics.  The true cause is the bios for the device is partial locked down/restricted.  You have to flash the bios to unlock and change settings that ati/radeon driver is having problems with. Once you flash the bios with the custom bios, you need to go to the new north bridge settings and change the setting "UMA+sideport" to "UMA". Once you do the ati/radeon drivers work with the ati hardware.

**Caution you can brick device on a bad flash. Before you flash read in the notebookreview.com forum about "crisis disk recovery"

This is link that I found the solution
[http://ubuntuforums.org/showthread.php?t=1471701&page=6).]("http://ubuntuforums.org/showthread.php?t=1471701&page=6).")

This is the link for the custom bios
[http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-102.html]("http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-102.html")

This is the link for making a bootable dos usb stick
[http://www.sevenforums.com/tutorials/46707-ms-dos-bootable-flash-drive-create.html]("http://www.sevenforums.com/tutorials/46707-ms-dos-bootable-flash-drive-create.html")

Once you make a bootable dos usb stick copy the custom bios file, phlash16.exe, and the extracted dos boot file to the stick, except emm386.sys and himem.sys to the usb stick.  phlash16.exe will not work if emm386.sys and himem.sys are present.  Reboot to dos.  at c: prompt issue type "phlash16.exe".  On successful flash, reboot, go into bios setting and make above changes.  You will have to reconfigure you xorg.conf file have the ati/radeon driver to access hardware properly. 

I had a some rendering problems with some programs that used opengl after flashing. I tried complete removal and reinstalling the programs but rendering issues still happened.  I backed up data files and key program config files/folder and did a reinstall.  My netbook works like a charm now.  Definate speed improvement.

---

