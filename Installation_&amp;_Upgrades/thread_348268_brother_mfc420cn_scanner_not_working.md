---
title: "brother mfc420cn scanner not working"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by sanny2k7 on 2007-01-28
HI, this is my first post to a forums ever and im been using linux for a couple of years.

thanks to all the dedicated who make up the linux world, you guys rock

Well i switched to ubuntu (very nice) and I have managed all the rest of my distro except I can not get xsane to work or kooka for that matter with my brother mfc420cn scanner 

I have it loaded brscanconfig2 sees it 

its detected by usb and everything but when i open xsane which sees the scanner I get an error after I pick my scanner to use

I get failed to open device brother2 net1 dev0 invalid argument

just wondering if anyone has this working im using 6.10 i386 

thanks for any help

---

### Post by sanny2k7 on 2007-02-01
FIY

wwot!!!!

I got it to work 

thanks to [http://www.ubuntuforums.org/showthread.php?t=302960&highlight=brother](http://www.ubuntuforums.org/showthread.php?t=302960&highlight=brother)

The reason for this is that the scanner MFC-215C is quite new and not yet present in the Kubuntu Dapper config files and you can just add these two lines. To fix this go to /etc/udev/rules.d/45-libsane.rules and find the 2 lines starting with #Brother MFC-210C , copy these lines below and change the model number to 215 and the product id to 0193 and reboot. Kooka should now run as ordinary user from the menu. This probably is more Dapper related. To lsusb in the terminal can give you the scanner details as well


# Brother|MFC 210C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner"
# Brother|MFC 215C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0193", MODE="664", GROUP="scanner"

I added 
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0162", MODE="664", GROUP="scanner"

this was determined by lsusb

Note: 

this was still not working, I fiqured out why see about it says GROUP="scanner" well I added my user to this group and i was scanning both under xsane and kooka 

im not sure what parts fixed it so i added all .. 

I noted saned was in the groups i fiqured it may be the same.

to add to groups (system->administrayion->user/groups .. user settings --> manage groups and add group scanner and check box for user 

thanks to all who posted a reply to this forum (lol.) 
im just kidding 

again thanks to all who posted in the forums. and all who helped with ubuntu, linux 

regards

sanny

---

