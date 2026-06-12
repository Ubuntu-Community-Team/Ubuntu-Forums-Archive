---
title: "New Install Won't Boot Unless Drive is in USB Enclosure"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by mootpoint on 2012-06-04
Hello,

I've installed Linux Mint 13 (AKA Ubuntu 12.04) on my SSD several times. No matter how I've tried it (from DVD, from USB key, inside Virtualbox), the machine refuses to boot from the drive when it's connected internally, but boots fine if the drive is connected in a USB external enclosure. Below is the link to the boot-repair output. 

[http://paste.ubuntu.com/1023879/](http://paste.ubuntu.com/1023879/)

The one thing that catches my eye is, " => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looks for (,msdos1)/boot/grub on this drive." Should it be looking for (hd0,msdos1)/boot/grub? If not, can someone help me get this resolved? 

Thanks in Advance,
m00t

---

### Post by ajgreeny on 2012-06-04
[FONT=Arial]When you installed, how was the disk connected?  Whichever way it was then is the only way that it will boot now as otherwise you will have a different mount point, and the entry in grub.cfg for [/FONT][FONT=Arial]```
set root='(hd0,msdos1)'
```may then be incorrect, [/FONT]etc etc and the grub bootloader will be totally confused if the disk is in the wrong place.
[FONT=Arial]
If you run the boot-repair with the disk in each position and compare the output from each it may give you more clue as to what is going on.[/FONT]

---

### Post by mootpoint on 2012-06-04
The disk was /dev/sda in a vm while connected via USB to the physical box. I did do a plain vanilla DVD disk install with the drive in the machine; it did't work. I'll try your suggestions above and post back. 

m00t

---

### Post by mootpoint on 2012-06-04
Well, this is a new SSD, as I mentioned ... and it *almost* works with the BIOS set to AHCI. It *does* work with the BIOS set to IDE. 

*sigh* So many hours ... NOTHING is worse than something that "almost" works! :-|

m00t

---

