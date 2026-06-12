---
title: "Printer and Internet connection problems"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by henwyn on 2008-09-29
I have Ibex 64bit installed on my new box. After the latest upgrade, a couple of days ago, I lost my ethernet connection to the Internet. I had been running a minimal install successfully and this was after getting brave and installing all the software that would be part of a normal Kubuntu installation. I'm not sure where to start looking for the culprit or a cure. It is not a hardware problem; I can connect from Hardy or WinXP which are both installed on the same drive.

On my old box (32bit) I upgraded to Ibex and had lots of problems through the various Alpha releases. Most things are working now but my Samsung ML 2510 series printer gives the error "cups-missing-filter" and refuses to print. This is one that lots of people are having problems with but I haven't seen a solution posted. Oddly enough the printer works in the 64bit Ibex installation. (Edit added) This problem was solved by downloading Samsung's Linux driver package, deleting the printer, and then reinstalling it. Someone on another forum attributed this behavior with his printer to AppArmor in the kernel preventing an outside driver from being used. We'll see if my fix will stick after rebooting, since I am now using Samsung's driver.


Suggestions on either of these problems would be welcome.

---

### Post by muzincs on 2008-09-30
I installed Intrepid Alpha-6 and lost my internet connection.  I have a static IP address.  This is a known bug.  The current workaround is to remove, in synaptic, the four packages that appear as installed when you search on "network manager".  After rebooting, the system will revert to the previous settings and you'll get your internet connection back.  Hope this applies to your situation.  Oh, you will have to do it again every time an upgrade re-installs network manager.

---

