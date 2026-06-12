---
title: "USB live boot prompt"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by Capt_Scribble on 2010-09-04
I just made a live USB of 10.04 Lucid using the Startup Disk Creator; but when I boot it gives the "boot:" prompt. Typing anything in like "help" or hitting enter just gives an error that it can't find the kernel image. Any ideas? Thanks!

---

### Post by ajgreeny on 2010-09-04
Check your iso file against the md5sum listing at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes), and if it's OK remake your USB startup drive again.  If the md5sum is not a match, download again and start from scratch.

---

### Post by Capt_Scribble on 2010-09-04
I've tested and used this ISO before on a DVD; it installed fine on the laptop. I need it on a USB stick now because my other computer doesn't have a DVD drive. I'm now downloading the 10.04.1 to see if it makes a difference.

---

### Post by Capt_Scribble on 2010-09-04
Using 10.04.1 didn't change anything. I still get the "Could not find kernel image: linux" error. The md5sum was ok too.

---

### Post by -kg- on 2010-09-04
My suggestion would be to install the .iso you've downloaded to USB using [Unetbootin]("http://unetbootin.sourceforge.net/").  If you're attempting to make the USB drive from Ubuntu, install Unetbootin from the Repos and if you're making it from Windows, download the Windows installer from the link above.

When creating the bootable Flash drive (you ***are*** using a Flash drive and not a USB hard drive, right?), select the second radio button from the Unetbootin screen (marked "Diskimage"), then using the button to the far right, navigate to your downloaded (and MD5 checksummed) .iso file and select it.  Click "OK" and after a few minutes you should have a bootable USB Flash device.

This has worked for me every time I have tried it.  One thing...I suggested using the second radio button because I have had issues with the first (default) method...I think due to corrupted downloads.  The second method down has worked for me every time.

---

### Post by utnubuuser on 2010-09-04
+1 -kg-

The only way I've ever been able to get a working liveUSB-flash is through Unetbootin on Windows.  Seems to work flawlessly.  There are all kinds of how-tos floating around to fix the casper files for usb's created in linux...

---

### Post by Capt_Scribble on 2010-09-04
Thanks! Unetbootin worked just fine. BTW I'm using a flash drive in Ubuntu, not windows. Anyway, I'll mark this as solved (if we consider Unetbootin a solution for the Startup Disk Creator...)

---

