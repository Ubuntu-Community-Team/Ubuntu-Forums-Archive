---
title: "Error when starting up"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by tommyss4l on 2010-11-14
I am trying to do a live run of UNR 10.10 out of curiosity and I am getting a strange message during the boot load sequence

SYSLINUX 3.63 Debian-2008-07-15 EBIOS Copyright (C) 1994-2008 H. Peter Anvin
Unknown keyword in configuration file.
boot:

From there it just sits there. I've tried on two different sticks and gotten the same result. 
I don't get any errors when installing the image onto my stick, the start up disk creator runs just fine. 

Thanks

---

### Post by sikander3786 on 2010-11-14
How was the USB prepared?

Open up your USB using file explorer and look for a folder names isolinux. If it is there, rename it to syslinux and furthermore, two files under it named isolinux.bin and isolinux.cfg to syslinux.bin and syslinux.cfg respectively and try USB boot.

If it doesn't help, consider using unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by tommyss4l on 2010-11-14
Ok, I checked the files and fixed them, It's still giving me the same error message

I'm installing UNetbootin now, hopefully that will work

---

### Post by tommyss4l on 2010-11-14
Ok, just tried UNetbootin, didn't work, I got the same error message

---

### Post by sikander3786 on 2010-11-14
Check the integrity of downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you need to re-download, it'd be better to use a torrent as it does that hash check automatically.

---

### Post by tommyss4l on 2010-11-14
The hash checks out on my latest redownload, I also went into the usb drive after running the Start up disk creator and made sure everything was syslinux instead of isolinux.

---

### Post by diggiewiggie on 2011-02-01
i have the exact problem here, already spent my day trying to figure out what is wrong, but can't find the answer to this trouble.

---

