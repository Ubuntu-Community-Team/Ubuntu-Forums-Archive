---
title: "USB startup disk creator"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-02-15
I've been trying to create a boot flash drive with bt4 on it using the USB startup disk creator. The image is 1.3Gb, and it won't show up when I select the iso. I also tried with Sabayon which is 1.7Gb in size, and it doesn't show up either. Is there a limit to the size of the iso using this utility?

---

### Post by GeorgeVita on 2010-02-15
Hi ** cariboo907**,
I think that USB startup creator needs a 'valid' (Ubuntu) .iso

EDIT: just tried pup-431.iso approx. 105MBytes (puppylinux) and cannot be used.
From file properties I found the same definition: 'raw CD image (application/x-cd-image)' 

Regards,
George

---

### Post by VMC on 2010-02-15
After trying this myself using another non-ubuntu ISO, I thought I found out that indeed it would only use Ubuntu qualified ISO's.

Then I removed ~/.usbcreator.log, and retired using Clonzilla ISO.
It showed up. But there may be similarities in the file structure.

Here my ".usbcreator.log" showing Clonezilla and then I cancelled it.

```
usb-creator 2010-02-15 14:08:39,058 (DEBUG) backend.py:16: UDisksBackend
usb-creator 2010-02-15 14:08:39,359 (DEBUG) backend.py:36: detect_devices
usb-creator 2010-02-15 14:08:39,370 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda1
usb-creator 2010-02-15 14:08:39,380 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda2
usb-creator 2010-02-15 14:08:39,391 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda5
usb-creator 2010-02-15 14:08:39,400 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda10
usb-creator 2010-02-15 14:08:39,411 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda11
usb-creator 2010-02-15 14:08:39,421 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda12
usb-creator 2010-02-15 14:08:39,431 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda6
usb-creator 2010-02-15 14:08:39,441 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sr0
usb-creator 2010-02-15 14:08:39,455 (DEBUG) backend.py:172: disk added: /org/freedesktop/UDisks/devices/sr0
usb-creator 2010-02-15 14:08:39,465 (DEBUG) backend.py:191: not adding device: 0 byte disk.
usb-creator 2010-02-15 14:08:39,466 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda8
usb-creator 2010-02-15 14:08:39,476 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda9
usb-creator 2010-02-15 14:08:39,486 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda
usb-creator 2010-02-15 14:08:39,496 (DEBUG) backend.py:67: device_added: /org/freedesktop/UDisks/devices/sda7
usb-creator 2010-02-15 14:08:49,376 (DEBUG) backend.py:22: Backend told to add: /media/DOWNLOADS/clonezilla-live-20091230-karmic.iso
usb-creator 2010-02-15 14:08:49,377 (DEBUG) misc.py:127: ['isoinfo', '-J', '-i', '/media/DOWNLOADS/clonezilla-live-20091230-karmic.iso', '-x', '/.disk/info']
usb-creator 2010-02-15 14:08:49,436 (DEBUG) frontend.py:195: add_source: /media/DOWNLOADS/clonezilla-live-20091230-karmic.iso
usb-creator 2010-02-15 14:09:54,881 (DEBUG) backend.py:174: cancel_install
```

Edit: Now that I looked at Clonezilla ISO, it shows karmic at the end.
BTW-I don't know it I have an ISO that big to try.

---

### Post by mdurham on 2010-02-15
Use UNetbootin

---

### Post by cariboo on 2010-02-15
That's what I ended up doing. I have a Karmic dvd iso on the same system, I didn't bother trying it today, but I will try it when I get back to the office tomorrow.


**Edit:** I see from the documentation [here]("https://help.ubuntu.com/9.10/usb-creator/C/requirements.html"), that it is Ubuntu only, so size shouldn't make a difference.

---

