---
title: "Unable to boot from USB"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by mu:te on 2008-11-24
So there I just realized that my cd-rom isn't working properly so I decided to put the installation of Ubuntu on my USB pen. The pen is 8GB and I used UNetbootin to install the iso on the pen.

When I restarted and entered BIOS to "Enable USB Boot" I couldn't find it. After long search it seems as I cannot boot from my USB.

First Boot Options are
- Hard Disk
- CD - ROM
- Lan Legacy
- USB-FDD
- USB-Zip/USB-LS
- USB-CDROM

Now, how can I boot from my USB key? Tested all of those 3 options, non works.:(

-- Note
 The USB pen is formatted as FAT32, is that okey or does it have to be formatted as NTFS?

---

### Post by snowpine on 2008-11-24
On some computers, the USB drive is mounted as just another hard drive... see if you can find a "hard drive" option that allows you to set the boot order of the different hard drives, then move the USB drive to the top. (This is the method I use on my eee pc.)

---

### Post by decard_pain on 2008-11-24
it can also be detected as a floppy drive (yes it's true)
but some pc's just can't boot from usb.in these cases where you have no cd and can't boot from usb .
you have 2 options
a floppy boot(not sure how you do this)

secend one needs windows to download unetbootin and do a net install
hope this helps

edit also try look for usb legacy support in chipset options

---

### Post by mu:te on 2008-11-24
> **decard_pain said:**
> it can also be detected as a floppy drive (yes it's true)
but some pc's just can't boot from usb.in these cases where you have no cd and can't boot from usb .
you have 2 options
a floppy boot(not sure how you do this)

secend one needs windows to download unetbootin and do a net install
hope this helps

edit also try look for usb legacy support in chipset options

Yea I went a little bit deeper in my BIOS and noticed something like "Read USB Boot as FDD or HDD" Floppy Disk or Hard Drive. It was on Auto Detect and I canged it manually and tried to Boot both options, neither worked. :/

---

### Post by mu:te on 2008-11-24
Nwm people, thanks for the help, found a solution, just threw the disk in my computer, and decided to wait. After seeing the same error message over and over again for at least 6 minutes it got "fixed" or something, dont know, dont care, I got linux again.. :guitar:

---

### Post by w2vy on 2009-03-18
> **decard_pain said:**
> 
secend one needs windows to download unetbootin and do a net install hope this helps


I tried unetbotin aiming for Net Install and it seemed to still want to write to the floppy (which I can't BOOT from)

Any suggestions on how to make a NET Boot CD?

Unless of course I can load windows and then launch something off the USB to start a NET or USB installer...

tom

---

