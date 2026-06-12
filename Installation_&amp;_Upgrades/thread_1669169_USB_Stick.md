---
title: "USB Stick"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by rickhaden on 2011-01-17
OK...although there are a number of threads dealing with USB installation (installing ubuntu server on a windows box), I can't find anyone with the same error message. I have installed the software on the stick using the software from penstick and rebooted the machine. It reads the stick and I get a message saying 'Attempting to boot from USB device'. It then stops and says can't start windows because ntkernel is missing or corrupt. What am I doing wrong?

Rick

---

### Post by sandy8925 on 2011-01-17
um i don't know what penstick is, but try using universal usb installer in windows - you can get that here: [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.8.2.4.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.8.2.4.exe)


on second thoughts, can your computer actually boot from usb? i recommend checking that first

---

### Post by ronparent on 2011-01-17
It sounds more like a windows error message - resulting from trying to boot a linux system from a windows boot loader? Are you sure you have installed a grub boot loader to the stick?

---

### Post by sandy8925 on 2011-01-17
um i don't know what penstick is, but try using universal usb installer in windows - you can get that here: [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.8.2.4.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.8.2.4.exe)


on second thoughts, can your computer actually boot from usb? i recommend checking that first

---

### Post by coffeecat on 2011-01-17
@OP, I can't answer your question, but do you really want your email address as your forum username? That's not a good idea. If you want to change it, you can post a request in the forum Resolution Centre, where an admin can deal with it.

[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by rickhaden on 2011-01-17
I did use the [http://www.pendrivelinux.com/downloa...er-1.8.2.4.exe]("http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.8.2.4.exe") installer and the message I get is that it is attempting to boot from the stick, so I presume that it is able. It appears that it is still looking for the windows bootup? Could the installation on the stick have gone wrong? WOuldn't I have had some error message?

Best regards to you all

Rick

---

### Post by C.S.Cameron on 2011-01-17
Sometimes Universal fails and UNetbootin and/or usb-creator work.

---

### Post by rickhaden on 2011-01-18
Have now tried Netbootin and have got the same error...Windows could not start because ntokrnl is corrupt or missing

Rick

---

### Post by rickhaden on 2011-01-18
OK...Managed to start it from the USB stick...but now I get to the point in the installation where it wants to mount a cd...there doesn't appear to be anywhere to change that to the usb or anything else and I haven't got a cd...

Rick

---

