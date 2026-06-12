---
title: "&quot;Persisitent&quot; live USB Unix- want to save changes"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by Jeff_Pass on 2015-01-13
Have since given up all hope of accessing my upgraded Ubuntu in a dual-boot situation after the upgrade allowed Windows 8 to take over the bootloader.    Nothing to fix the situation has worked.
However I can still run Ubuntu via a live USB install "Try Ubuntu without installing", by hitting F12 right after boot and selecting the USB drive.    This allows me to access all the old files on my hard drive and I can function.   The only problem is any changes I make to the system, such as loading software or saving Bookmarks in Firefox, for instance, are wiped out every time I reboot the system.

Is it possible to set a Live USB or 'Persistent' USB copy of Ubuntu so it really is persistent, so say I load something off the Software Center it will still be loaded after I reboot the machine?    Has this been done?
Thanks for any assistance!

---

### Post by ian-weisser on 2015-01-13
Persistence is an option you have during the install of the image onto the USB.
You cannot add persistence later - you must reinstall the image onto the USB again.

---

### Post by yancek on 2015-01-13
Yes you can do that.  The link below provides some information on how.  You can do it with unetbootin while creating the bootable flash drive initially also, the option is there.

[http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb](http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb)

The official Ubuntu wiki at the link below: 

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

---

### Post by sudodus on 2015-01-13
Yes, see for example these links

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

A persistent USB install of *buntu, usable with both Legacy and UEFI systems is described in the following [post at the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2108487&page=2&p=12656460#post12656460")

See also this [tutorial about One pendrive for all (Intel/AMD) PC computers]("http://ubuntuforums.org/showthread.php?t=2259682") and the following links

[Choosing between Live USB and Full USB Installation]("http://ubuntuforums.org/showthread.php?t=2130234&p=12578569&viewfull=1#post12578569") 
[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by ubfan1 on 2015-01-13
The live usb startup disk creator will no longer offer a persistence file on a 2G USB stick, since the minimum size is set to 1024K, and there isn't 
that much room left.  Edit the MIN_PERSISTENCE line in the
/usr/lib/python3/dist-packages/usbcreator/misc.py file.
Setting it to 800K will allow the persistence to be set.

---

### Post by kansasnoob on 2015-01-13
You should not give up on getting grub straightened out, your [other thread]("http://ubuntuforums.org/showthread.php?t=2260531") now has new replies. Patience is required here, we're all just volunteers that try to help when and if we can ;)

---

### Post by Jeff_Pass on 2015-01-13
I've got it... set the Persistent disk space when I recreated the bootable USB, and its working.
However the USB mounted filesystem is extremely slow..........bogs down when more than one window is open.

Insofar as the other issue.... not that I'm not patient, I simply have no choice but to find a workaround as I can't find any solution.   Must go on somehow!  I need an OS to access the Internet and Windows is so bogged with adware its useless.
    but its my fault for upgrading.....

---

### Post by ubfan1 on 2015-01-13
A full install to a USB stick will have better performance.  Add some of the optimizations you can find here and in the questions (C.S.Cameron wrote up some tips) and you might be happier.  You could try adding "toram" to the grub boot line, to put things on the install stick into ram -- haven't tried that myself, and don't know if it conflicts with persistent, but quick to try.

---

### Post by ian-weisser on 2015-01-13
Depends also on the USB stck and port. USB 2.0 stick and USB 2.0 port should be quite fast, but if either is USB 1.1, then IO may indeed be a bit slow.

---

### Post by sudodus on 2015-01-14
Persistence with USB 1.1 is extremely slow.
 Persistence with USB 2.0 very slow while a live system can be quite fast.
Persistence with a fast USB 3 pendrive in a USB 2 port is slow but much better.
Persistence with a fast USB 3 pendrive in a USB 3 port is fairly fast, but still limited by the writing speed of the flash memory.

See these links and links from them

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

### Post by C.S.Cameron on 2015-01-14
+1

Sounds to me like a good solution is a USB 3 stick in a USB 3 port with a Full install.
If for day to day use, a USB 3 external hard drive is even better.
If money is no object, (ha ha), try an external SSD.
But wait, if using a desktop, you could install a second internal  HDD for Ubuntu and have it's grub boot windows.

---

