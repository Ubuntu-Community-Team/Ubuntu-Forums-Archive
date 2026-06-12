---
title: "windows grub boot-repair"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by rafal311eng on 2012-06-01
Hello all, 
I updated my ubuntu to 12.4 from 10.10 and now I'm not able to select my windows system during the system start :(

Below the report from boot-repair:
[http://paste.ubuntu.com/1018335/](http://paste.ubuntu.com/1018335/)

Any assumptions what is gona wrong? 

Thanks in advance for any hints
Raf

---

### Post by ajgreeny on 2012-06-01
> **rafal311eng said:**
> Hello all, 
I updated my ubuntu to 12.4 from 10.10 and now I'm not able to select my windows system during the system start :(

Below the report from boot-repair:
[http://paste.ubuntu.com/1018335/](http://paste.ubuntu.com/1018335/)

Any assumptions what is gona wrong? 

Thanks in advance for any hints
Raf
The obvious problem is that the windows installation does not appear in the /boot/grub/grub.cfg file in sda3.  That, however, does not help much as we now need to know why it was not seen and added to the grub menu.

Can you run the command ```
ls -l /etc/grub.d
``` and post the output back here please.  That will show if the file **30_os-prober** which should find and add all other OSs to the menu, is present and executable.

---

### Post by TheKingOfComputers on 2012-06-01
Good ridden! Trust me Windows is no good.

---

### Post by rafal311eng on 2012-06-01
here the output:

rafal@rafal-laptop:~$ ls -l /etc/grub.d
razem 56
-rwxr-xr-x 1 root root 6715 kwi 17 20:20 00_header
-rwxr-xr-x 1 root root 5522 kwi 21  2011 05_debian_theme
-rwxr-xr-x 1 root root 7399 kwi 17 20:20 10_linux
-rwxr-xr-x 1 root root 6335 kwi 17 20:20 20_linux_xen
-rwxr-xr-x 1 root root 1588 pa&#378; 22  2010 20_memtest86+
-rwxr-xr-x 1 root root 7603 kwi 17 20:20 30_os-prober
-rwxr-xr-x 1 root root  214 kwi 21  2011 40_custom
-rwxr-xr-x 1 root root   95 kwi 21  2011 41_custom
-rw-r--r-- 1 root root  483 kwi 21  2011 README

the file is there and seems to be also executable

---

### Post by oldfred on 2012-06-01
XP has three boot files and your sda1 only has 2, your are missing boot.ini.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM

If sda1 is your main Windows install you need to create the boot.ini file.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

You can use your XP install disk's repair console and run this command.

BOOTCFG  /rebuild  # rebuilds boot.ini

And you can review anyone who has posted a boot info script with XP and copy from that report the boot.ini as it is just a text file.

---

