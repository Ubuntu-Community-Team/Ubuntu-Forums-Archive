---
title: "Brother install Ubuntu 14.04 MFC-J6910DW"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by dion6 on 2014-11-23
I followed many pages and none of them worked, eventually I got it to work.



1 Using the browser download the driver install tool from [http://support.brother.com/g/b/downloadtop.aspx?c=au&lang=en&prod=mfcj6910dw_all](http://support.brother.com/g/b/downloadtop.aspx?c=au&lang=en&prod=mfcj6910dw_all)
2 ctrl alt T to bring up the terminal.
3 sudo su and enter your password, gives you root access which you need to install this driver.
**4  gunzip** linux-brprinter-installer-2.0.0-1.gz. 
5 **bash** linux-brprinter-installer-2.0.0-1 MFC-J6910DW
6 **The message "**Will you specify the Device URI? [Y/n] ->" Yes if it is connected by network, no if connected via usb
7 If yes, was selected, you will be asked for an IP address, this can be found in the router table.
8 If you were successful a test page will be printed.

---

