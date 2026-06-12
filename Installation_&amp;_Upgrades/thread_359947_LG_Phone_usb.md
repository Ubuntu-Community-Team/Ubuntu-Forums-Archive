---
title: "LG Phone usb"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by philmccaffrey on 2007-02-12
Hi,

I have recently moved from Suse 10.0 to kubuntu edgy and everything is working well except for one problem. 

I have an LG chocolate phone which i used to be able to just plugin using a usb cable and it came up as a removable usb stoage device in Suse. However, in ubuntu i get nothing. The usb mount is working fine as i can plug my usb memory stick in and it works fine!

I tried a dmesg command which gave the following output:

[17183364.156000] usb 1-10: new full speed USB device using ohci_hcd and address 20
[17183364.564000] usb 1-10: device not accepting address 20, error -110

I just want to be able to transfer mp3s so need to be able to mount the phone as a removable usb device.

If anyone has any ideas please let me know...

Thank you for your time,

Phil

---

### Post by MaddMatt on 2007-02-12
Try BitPim at bitpim.org - they have specific linux instructions for hooking up phones. In Ubuntu, the phones need to be manually added to the Hotplug directory:

From the BitPim helpfile:

By default Linux configures USB devices so that they are owned by root. You should be running BitPim as yourself, not root. Most recent Linux distributions use hotplug, and these instructions show you how to configure it.
  
1. 
Edit /etc/hotplug/usb.usermap 
Add a line to the bottom.
usbcell 0x0003 VID PID 0 0 0 0 0 0 0 0 0 
You need to replace VID and PID with the relevant vendor and product ids. The VID and PID can also be obtained from the Comm Port Settings dialog. 
Note For more recent versions of hotplug, it is considered better form to create the file /etc/hotplug/usb/usbcell.usermap.
  
2. 
Create /etc/hotplug/usb/usbcell 
This script is executed whenever the device is inserted. Here is a simple example that makes the device be owned by root, group owned by cellusers and readable/writable by root and the members of cellusers. 
#!/bin/bash 
if [ "${ACTION}" = "add" ] && [ -f "${DEVICE}" ] 
then 
        chown root "${DEVICE}" 
        chgrp cellusers "${DEVICE}" 
        chmod 660 "${DEVICE}" 
fi 

You can adjust that script as you see fit. Don't forget to make it executable. On many versions of Linux, there is a script named usbcam in the same directory that changes the device to be owned by the same person who is logged into the console. If you prefer that behavior, then copy usbcam to usbcell 


My computer doesn't see my phone as a USB drive, but BitPim is great for uploading music, backing up contacts, etc.

My only issue is that my phone is only detected if I have it plugged in on boot. 
-matt

---

### Post by philmccaffrey on 2007-02-13
Thanks i'll give it a go

---

