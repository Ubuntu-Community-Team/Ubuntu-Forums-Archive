---
title: "Installing Xerox PE220 under ubuntu"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by newxdesign on 2007-01-15
Hello,

I'm triing to install a Xerox Workcenter pe220 under my ubuntu, i have downloaded the latest drivers from xerox suport page and when i install the mpf drivers it gives a lot of errors, but it adds a new printer to my system. when i try to print a test page it wont print.

some one can help me?

sorry about my english

---

### Post by halitech on 2007-03-03
how do you have the machine hooked up? are you using USB or ethernet?

---

### Post by newxdesign on 2007-03-03
hi!

i have conected via USB, i buyed one lexmark printer and then solved my problem :D

thanks anyway

---

### Post by lingyew on 2007-09-09
Does anybody know the solution of how to install the Xerox PE220 aside from buying a new printer? I have Ubuntu 7.04 installed on a pc while the Xerox PE220 connected to my Windows machine via USB as a shared printer. I have managed to install the drivers onto my iMAC and got it to print via network. The only problem I have is with the Linux drivers. Any solution? 

Please help cause the people from Xerox are telling me that their Linux drivers only support Redhat, Suse, Turbo Linux, Caldera and Slackware. Any advice would be appreciated. Thank you.

---

### Post by mxm2 on 2007-09-30
Try to use driver for Samsung SCX-4521F ([http://www.samsung.com/au/support/productsupport/download/FileView.aspx?cttfileid=801111&type=Printer%2c+Fax&typecode=&subtype=Printer%2c+Fax&subtypecode=&cmssubtypecode=&model=SCX-4521F&filetype=DR&language=&LSSI=/au/module/ssi/left/lmenu_printerfaxcopysolutions_printerfaxcopysolutions.sec&RSSI=/au/module/ssi/right/rmenu_printerfaxcopysolutions.sec](http://www.samsung.com/au/support/productsupport/download/FileView.aspx?cttfileid=801111&type=Printer%2c+Fax&typecode=&subtype=Printer%2c+Fax&subtypecode=&cmssubtypecode=&model=SCX-4521F&filetype=DR&language=&LSSI=/au/module/ssi/left/lmenu_printerfaxcopysolutions_printerfaxcopysolutions.sec&RSSI=/au/module/ssi/right/rmenu_printerfaxcopysolutions.sec))

or to use instruction:
[http://www.vyvy.org/main/node/146](http://www.vyvy.org/main/node/146)

after installation check rights for directory /, /etc, /usr, and probably you'll have to set them into 755

---

### Post by halitech on 2007-11-21
the drivers are generic PPD files so they should work in most *nix systems. Are you able to browse the network and see the printer?

---

### Post by dodan on 2008-07-24
I have Kubuntu 8.4.1 (migration from Debian 4.0) and Xerox PE220 and this is my solution how to install this printer :

1) download driver from :
   [http://www.samsung.com/ph/support/download/supportDown.do?group=printermultifunctionfax&type=printermultifunctionfax&subtype=monomultifunction&model_nm=SCX-4521F&disp_nm=SCX-4521F&language=&cate_type=all&dType=D&mType=DR&vType=R&prd_ia_cd=06010300](http://www.samsung.com/ph/support/download/supportDown.do?group=printermultifunctionfax&type=printermultifunctionfax&subtype=monomultifunction&model_nm=SCX-4521F&disp_nm=SCX-4521F&language=&cate_type=all&dType=D&mType=DR&vType=R&prd_ia_cd=06010300)

2) as root run install script : [path]/cdroot/autorun

3) uncomment this 4 lines in /etc/init.d/mountdevsubfs.sh :

   #mkdir -p /dev/bus/usb/.usbfs
   #domount usbfs "" /dev/bus/usb/.usbfs-    obusmode=0700,devmode=0600,listmode=0644
   #ln -s .usbfs/devices /dev/bus/usb/devices
   #mount --rbind /dev/bus/usb /proc/bus/usb

4) run : /etc/init.d/mountdevsubfs.sh start

Now you can see on desktop Samsung Unified Driver utility ... use it and try to print test-page, I had success so maybe you'll have too.


~
Dodan

---

