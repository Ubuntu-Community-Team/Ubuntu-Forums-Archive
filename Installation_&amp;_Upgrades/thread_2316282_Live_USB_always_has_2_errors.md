---
title: "Live USB always has 2 errors"
date: 2016-03-06
forum: Installation &amp; Upgrades
---

### Post by Rip_bLadez_Ash on 2016-03-06
After having lots of problems and crashes such as random restarting, I thought that the install could have been broken, so I got my live usb and checked the drive for errors and it always says that 2 files had errors. I've checked the md5 file and it matched I've formatted and burned lots of times and on a different USBs and It still shows 2 error files. Am I getting getting the crashes and problems because the iso I used had those 2 error files? I've used h2testw to check the health of the USB and it told me the usb was fine to use. Should I use something else to test the usb sectors?

---

### Post by Rip_bLadez_Ash on 2016-03-07
UPDATE: I bought a brand new flash drive and it still had 2 error files

---

### Post by sudodus on 2016-03-07
Please tell us which version of Xubuntu you are using! If you don't know you can tell us the name of the iso file, that you downloaded.

Did you check the iso file with md5sum, if it matches the value listed at this link: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Usually, if a USB pendrive is damaged, it will not work (at all). It is not common with bad sectors in a working drive (bad memory cells should be replaced with spare cells by a built in system in the pendrive).

What tool did you use to flash the iso file into the pendrive?

---

### Post by Rip_bLadez_Ash on 2016-03-07
> **sudodus said:**
> Please tell us which version of Xubuntu you are using! If you don't know you can tell us the name of the iso file, that you downloaded.

Did you check the iso file with md5sum, if it matches the value listed at this link: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Usually, if a USB pendrive is damaged, it will not work (at all). It is not common with bad sectors in a working drive (bad memory cells should be replaced with spare cells by a built in system in the pendrive).

What tool did you use to flash the iso file into the pendrive?

I'm trying to install Xubuntu 15.10 Wily fox and I flashed the iso using universal-USB-installer

The md5sums match

---

### Post by sudodus on 2016-03-07
The iso file is good :-)

You can try other tools to flash the iso file into the pendrive. I suggest that you try a method, that ***clones*** the exact content of the iso file to the pendrive (when you make a standard live-only pendrive). This method is very reliable, and should work also in your case. Use one of the following links:

[Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) in Windows or [mkusb](https://help.ubuntu.com/community/mkusb) in linux.

---

