---
title: "dpkg-scanpackages is scanning ~/.wine/dosdevices (ie other drives)?"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2007-06-30
dpkg-scanpackages . /dev/null >Packages

I've run that many times before, but now it is taking AGES, and I noticed it is scanning the links to drives I've set up in Wine's "dosdevices" folder. I'm used to it scanning folders I've added to sources.list but this is something new, and I've had Wine for a while (though perhaps I haven't run the scan since I set up the dosdevices drives). It's doing normal stuff like finding packages and telling me that they're being ignored coz I already have them, but also weird stuff like looking through my Windows drive and complaining about not being able to find folders (due to long file names, like can'\t find "Documents" coz it is looking for "Documents & Settings"). Also, a great deal of the hits are coming up with "find: Symbolic link" followed by the wine folder path and the file on the other drive. Any ideas on whether this is normal?

EDIT: Since it just seems to loop forever on the "find: Symbolic link" I'd thought I'd post a sample. Also, restarted it to see what happens and it is all the usual added this, couldn't add that, didn't need to add this, etc, till it gets to this point. However, here and there during the initial "successful" part I saw it looking in Wine's folder. I have made sure nothing is out of the ordinary in sources.list, and that this isn't being caused by acciedentally pulling shortcuts instead of packages over to the actual archives folder and/or my local repository folder in my /home folder.

find: Symbolic link `./.wine/dosdevices/z:/sys/block/fd0/device/bus/drivers/pcspkr/pcspkr/input:event3/subsystem/event4/device/bus/drivers/ehci_hcd/0000:02:0b.2/usb8/usb_device:usbdev8.1/subsystem/usbdev2.3/device/2-1:1.0/usb_endpoint:usbdev2.3_ep81/subsystem/usbdev7.1_ep00/device/7-1/driver/usb4/subsystem/devices/3-0:1.0/driver/8-0:1.0/ep_81/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `./.wine/dosdevices/z:/sys/block/fd0/device/bus/drivers/pcspkr/pcspkr/input:event3/subsystem/event4/device/bus/drivers/ehci_hcd/0000:02:0b.2/usb8/usb_device:usbdev8.1/subsystem/usbdev2.3/device/2-1:1.0/usb_endpoint:usbdev2.3_ep81/subsystem/usbdev7.1_ep00/device/7-1/driver/usb4/subsystem/devices/3-0:1.0/driver/8-0:1.0/usb_endpoint:usbdev8.1_ep81/device' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `./.wine/dosdevices/z:/sys/block/fd0/device/bus/drivers/pcspkr/pcspkr/input:event3/subsystem/event4/device/bus/drivers/ehci_hcd/0000:02:0b.2/usb8/usb_device:usbdev8.1/subsystem/usbdev2.3/device/2-1:1.0/usb_endpoint:usbdev2.3_ep81/subsystem/usbdev7.1_ep00/device/7-1/driver/usb4/subsystem/devices/3-0:1.0/driver/8-0:1.0/usb_endpoint:usbdev8.1_ep81/subsystem' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `./.wine/dosdevices/z:/sys/block/fd0/device/bus/drivers/pcspkr/pcspkr/input:event3/subsystem/event4/device/bus/drivers/ehci_hcd/0000:02:0b.2/usb8/usb_device:usbdev8.1/subsystem/usbdev2.3/device/2-1:1.0/usb_endpoint:usbdev2.3_ep81/subsystem/usbdev7.1_ep00/device/7-1/driver/usb4/subsystem/devices/3-0:1.0/driver/8-0:1.0/driver' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.

You get the idea. Just multiply that by 17.37 zillion. Oh, and that Wine z: drive is my Ubuntu drive, not another... seems the searching on other drives just finds duplicates, but they aren't involved in this weird loop thingy.

---

