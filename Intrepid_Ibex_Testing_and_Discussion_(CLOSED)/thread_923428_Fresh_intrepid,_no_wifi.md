---
title: "Fresh intrepid, no wifi"
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by daggerx on 2008-09-18
installed intrepid fresh this morning - have no wifi - its on a dell 1525 - I do have a wireless setup at home. When I click the icon on the top right, the wireless functions are faded out. When I connect the eth, I can get the web and stuff. Any suggestions? please post as many as you can, I wont get to the machine until 6.30p EST. Please help and thanks...

---

### Post by LowSky on 2008-09-18
use heron, intreped is not an official release yet.

---

### Post by anotherdisciple on 2008-09-18
Did you enable the restricted drivers? They can be enabled by going to (System > Administration > Hardware Drivers) or it may be under (System > Administration > Restricted Drivers Manager)

---

### Post by daggerx on 2008-09-18
I believe they are enabled if you are referring to the little green circuit board that pops up on the top-right...

---

### Post by mb_webguy on 2008-09-18
While many wireless cards are now supported by Linux, not all are.  You may possibly need to use ndiswrapper and the Windows driver for your wireless card.

In the terminal, type "sudo apt-get install ndisgtk".  Now go to the Dell website and download the driver for your wireless card.  This will most likely be in an exe, but the exe is most likely a self-extracting archive which you can open with Archive Manager.  Extract the exe to a convenient location.

Now go to System->Administration->Windows Wireless Drivers.  Click the "Install New Driver" button, then locate the driver you just downloaded.  You're looking for the inf file.  Select it, then click "Install".  At this point, you may need to logout of the session or reboot before the driver installation will take effect.  You should now be able to connect to wireless networks using the Network Manager applet.

---

### Post by daggerx on 2008-09-18
i will try that, and i will do it with hardy...thanks

---

### Post by -Zeus- on 2008-09-18
... hence the reason intrepid is still an alpha and not for production use.  I would recommend you install Hardy

---

