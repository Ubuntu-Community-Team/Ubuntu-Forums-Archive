---
title: "SSD not detected by Gparted or Ubuntu Live, Nokia Booklet"
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by dsapoki on 2012-06-16
Hey all, 
The problem: Ubuntu 12.04 usb install does not recognize my SSD.
Hardware: Nokia Booklet 3g with new OCZ Vertex2 90GB SSD.
Story: I had Ubuntu 12.04 on this booklet running on Toshiba HDD. I have replaced the HDD with the SSD. When I boot from USB, there is not even a trace of this SSD in Gparted, fdisk -l or during the install. The SSD is recognized by BIOS, there is Win 7 installed on it and I can boot it. 

I am looking for single boot install of Ubuntu on this SSD. Any advice regarding changing the BIOS configuration between IDE/AHCI/ etc is not applicable as those options are not present in BIOS.

I have tried to run 

sudo dmraid -r -E /dev/sda

this is the output

ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104
no raid disks and with names: "/dev/sda"

Any ideas?

---

### Post by dsapoki on 2012-06-19
Anybody?

---

### Post by pakito15191 on 2012-06-19
It's probably the same problem that many people has suffered with the OCZ ssd drives, try to update it's firmware (with care as you can kill it) as specified in OCZ website and/or update the BIOS. It's not related to Gparted, nor to Ubuntu being Live, it's due to the sdd itself. There's plenty of people with the same problem out there, just google for more info.

---

### Post by oldfred on 2012-06-19
Some links:

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

