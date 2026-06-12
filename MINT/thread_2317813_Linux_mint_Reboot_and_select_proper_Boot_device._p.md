---
title: "Linux mint: Reboot and select proper Boot device. pls help"
date: 2016-03-20
forum: MINT
---

### Post by tash3 on 2016-03-20
I've attempted to completely replace windows 10 with linux, mint being the linux distro of choice through a usb install (I dont have a cd drive) However when i restart the computer after installation i get a black screen with the following message 'Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key'. I've tried using boot info script but when i write "sudo bash ~/Downloads/boot_info_script*.sh" i get "/home/mint/Downloads/boot_info_script*.sh: No such file or directory" any help is much appreciated. :(

---

### Post by coffeecat on 2016-03-20
*Thread moved to the **MINT** sub-forum.*

If you are getting a "no such file or directory" message, than the system is telling you what the problem is. Where did you download the boot script file from, and where did you find the instructions for the boot script? Did you extract it from the downloaded tar.gz file? What is the filename of the extracted script file?

If you follow the directions on this page: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) - you'll see that the filename of the extracted script file from there is bootinfoscript, so if you try to run something that corresponds with "/boot_info_script*.sh" you will indeed get an error - if you downloaded from there. I've downloaded the tar.gz from the link on that page, and I can confirm that the extracted file is bootinfoscript.

---

