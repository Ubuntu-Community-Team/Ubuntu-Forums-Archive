---
title: "intrepid takes FOREVER to shut down - freezes at &quot;shutting down alsa&quot;"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by harty83 on 2008-10-05
Just upgraded to Intrepid Beta.  It takes FOREVER to shut down freezing at "shutting down alsa" for several minutes.

Any clue on what could be the culprit?  What info is needed?

Thanks,
Alan

---

### Post by solitaire on 2008-10-06
This is happening with me too.

It takes 5 mins or so for ALSA to time out and for my laptop to shutdown / Restart.

It was shutting down fine over the weekend but something happened when i ran the updates and ALSA has to time out again.

---

### Post by alienexplorers on 2008-10-06
If you are running an older computer did you try to add acpi=force to the end of your kernel line in mrnr.lst
> ## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=266d9ded-7e5d-4c36-8a44-9e92c63661f9 ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=266d9ded-7e5d-4c36-8a44-9e92c63661f9 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd1,5)
kernel		/boot/last-good-boot/vmlinuz root=UUID=266d9ded-7e5d-4c36-8a44-9e92c63661f9 ro quiet splash vga=795  last-good-boot
initrd		/boot/last-good-boot/initrd.img
quiet

title		Ubuntu intrepid (development branch), memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=11e5a808-45f5-41fb-8b43-5f2a8af9016d ro quiet splash vga=795 acpi=force 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=11e5a808-45f5-41fb-8b43-5f2a8af9016d ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

terminator@terminator-desktop:~$ 



---

### Post by solitaire on 2008-10-06
> **alienexplorers said:**
> If you are running an older computer did you try to add acpi=force to the end of your kernel line in mrnr.lst

This made no diffrence to my shutdown.

Still having to wait for ALSA to time out.

---

### Post by MJWitter on 2008-10-06
Same thing here on a 1 year old laptop and a 3 month old desktop..

---

### Post by harty83 on 2008-10-06
Mine is a one year old desktop.  

Has anyone made a bug report yet?

---

### Post by TenPlus1 on 2008-10-06
Make sure the Power Management service is enabled, this cause some funny shutdown issues on my laptop/desktop also...

---

### Post by solitaire on 2008-10-06
Power management service is running and has been working fine on my laptop.

Bug report :
[https://bugs.launchpad.net/ubuntu/+bug/274995](https://bugs.launchpad.net/ubuntu/+bug/274995)

---

### Post by karlatsaic on 2008-10-17
Same problem for me on compaq presario 2100 (circa 2003)

span.jajahWrapper { font-size:1em; color:#B11196; text-decoration:underline; } a.jajahLink { color:#000000; text-decoration:none; } span.jajahInLink:hover { background-color:#B11196; }

---

### Post by jackhynes on 2008-10-27
Same for me; freezes at shutting down ALSA, using a VAIO FJ series.

---

### Post by solitaire on 2008-10-27
Try the temp fix in this Bug log:
[https://bugs.launchpad.net/ubuntu/+bug/274995](https://bugs.launchpad.net/ubuntu/+bug/274995)

it works for me.

---

### Post by nanog on 2008-10-27
This occurs on del e520 i just upgraded. The fix referenced in the bug report above worked.

---

