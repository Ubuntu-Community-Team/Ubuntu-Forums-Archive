---
title: "Making a bootable USB to install Lubuntu on HP Mini"
date: 2014-11-18
forum: Installation &amp; Upgrades
---

### Post by AussieGuy on 2014-11-18
Problem: install Lubuntu on HP Mini 210

I'm not sure where the problem is.... I had used "dd if=lubuntu.iso of=/dev/sdb1" to write to the USB disk, and I then attempted to boot from it on the HP Mini.  The boot sequence was set to use the USB drive first, but it wouldnt recognize Lubuntu; just sat there with a blinking light doing nothing.  I checked the disk, and all the Lubuntu files seemed to be there, so the 'dd' command appears to have worked.  But the HP Mini didn't recognize the disk as a bootable medium.

So I decided to start from scratch, reformat the USB disk, and write the iso image to it again.  But nothing works!  When using Startup Disk Creator I obtain a slew of error messages.  On another forum somebody recommended using gparted to format the disk first.  But gparted also gave an error.  I'm using an old Verbatim "Store and go" 2GB disk... maybe it's the disk itself?  In which case, is there a disk brand/size which is known to be particularly robust?  And where might I find an exact sequence of commands for formatting a USB disk and making it bootable?  I prefer to use the command line if possible.

Thanks, folks!

---

### Post by sudodus on 2014-11-18
That command line is only almost correct. You should copy/clone/flash the iso file to the drive, not a partition so

```
sudo dd if=lubuntu.iso of=/dev/sdx
```

would work better (where x is the drive letter). *sudo* and *no partition number*! But dd is risky, it is nick-named 'disk destroyer' and it deserves it, because there is no safety checks, and you can easily overwrite valuable data.

If you want to use the dd method, I suggest that you wrap the ***mkusb*** shell-script around it, which makes it much safer. See this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by sudodus on 2014-11-18
If you have problems also after that, check the md5sum of the iso file, and try different methods to make the computer boot from USB. See this link (and links from it)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by AussieGuy on 2014-11-19
Thanks folks - it turned out to be the old disk which couldn't be made bootable.  I used mkusb and a newer disk, and it worked like a charm.  Thanks again!

-A.

---

### Post by sudodus on 2014-11-19
Congratulations :KS

Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

---

