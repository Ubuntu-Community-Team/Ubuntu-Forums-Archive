---
title: "Black Screen After Installing Ubuntu 12.04LTS.."
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by tikusjamban on 2012-04-27
i got the black screen on my hard drive...but there is one weird thing..i need to boot trough USB than i can get into my desktop..so i cant re-install my ubuntu how can i solve this problem..help me

---

### Post by IWantFroyo on 2012-04-27
I don't see why you can't reinstall if you have a live image on a USB drive. There should be a big "Install To Hard Drive" button.

As for how the screen is black, did you tinker with anything?

---

### Post by tikusjamban on 2012-04-27
its not like that...the desktop is just like i have installed it on my hard-drive...but my laptop cant boot up without USB hub...how can i solve this?..need to boot up with USB than after i can ejject my usb...its like the startup using usb n the desktop is in the hardisk...

---

### Post by Murphy1138 on 2012-04-27
hit CTRL+ALT + F2, should bring you up with a terminal prompt from which you can login to your account
I end up with the same issue because Im using Nvidia Suppled drivers.
if you have a Nvidia card and are using nvidia supplied drivers I have to reinstall the driver every time the Kernel gets updated.

from the Terminal you just re run the Nvidia installer and let it re-install and then reboot and it will be fine. 

Im not saying this is your issue , but if you hit CTRL+Alt+F2 and you get a login prompt your linux system is running and its the X config that has the issue.

---

### Post by jdeca57 on 2012-04-27
Murphy1138, did you actually try that out on Ubuntu 12.04? I did it and got a... black screen. Of course, I knew that Ctrl-Alt-F7 brings you back to the GUI... ;-)

---

### Post by tikusjamban on 2012-04-27
i think i just sort that out...my bad to install grum on my UBS thumb drive meanwhile my os is on my hardrive....hahahahaha....so iv install grump on the drive n its works like a charm now....thanks for the reply guys...

---

### Post by Murphy1138 on 2012-04-29
> **jdeca57 said:**
> Murphy1138, did you actually try that out on Ubuntu 12.04? I did it and got a... black screen. Of course, I knew that Ctrl-Alt-F7 brings you back to the GUI... ;-)

Not yet on 12.04 but on 11.10 each time the system updated the kernel then yes I have. :)

---

