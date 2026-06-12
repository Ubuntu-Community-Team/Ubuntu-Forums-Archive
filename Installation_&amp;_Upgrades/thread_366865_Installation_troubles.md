---
title: "Installation troubles"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by dignick on 2007-02-21
Trying to install Ubuntu, I've run into two main difficulties.  The first is I use a matrox p650 graphics card, so I've had to download the alternate installer.  The next main problem is the sata controller drivers.  I've tried 6.06, 6.10 and 7.04 herd 4.  6.06 is the only version that works, the other two do not have the driver my hardware needs, which is disappointing.

My motherboard is a [GIGA-BYTE GA-8IPE1000]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1647").  6.06 detects the hard drive as scsi.

I'd like to get 7.04 or even 6.10 working, but it isn't vital.

Also, upgrading the distribution after installing breaks both the controller driver and the graphics driver (I think), as neither work with the new kernel and it just stops at some drive-related stuff, but I can get to a terminal with the old kernel and recovery mode.

Thanks.

---

### Post by logos34 on 2007-02-21
You must reinstall the graphics driver after a kernel update.  

You have a sata or pata/ide drive?  If it's sata it should show up as /dev/sda. (used for sata and scsi disks)

If you could post the output from this command:
> lspci -n

---

### Post by dignick on 2007-02-21
What command can I use to reinstall the driver?

A windows ntfs partition is mounted in /mount/sda1.  The drive is SATA.

Output:
```
nick@Lounge:~$ lspci -n
0000:00:00.0 0600: 8086:2570 (rev 02)
0000:00:01.0 0604: 8086:2571 (rev 02)
0000:00:03.0 0604: 8086:2573 (rev 02)
0000:00:1d.0 0c03: 8086:24d2 (rev 02)
0000:00:1d.1 0c03: 8086:24d4 (rev 02)
0000:00:1d.2 0c03: 8086:24d7 (rev 02)
0000:00:1d.3 0c03: 8086:24de (rev 02)
0000:00:1d.7 0c03: 8086:24dd (rev 02)
0000:00:1e.0 0604: 8086:244e (rev c2)
0000:00:1f.0 0601: 8086:24d0 (rev 02)
0000:00:1f.2 0101: 8086:24d1 (rev 02)
0000:00:1f.3 0c05: 8086:24d3 (rev 02)
0000:00:1f.5 0401: 8086:24d5 (rev 02)
0000:01:00.0 0300: 102b:2537 (rev 02)
0000:02:01.0 0200: 8086:1019
0000:03:03.0 0480: 11bd:0040
0000:03:03.1 0480: 11bd:0041
0000:03:03.2 0480: 11bd:0042
0000:03:05.0 0c00: 104c:8024
```

Cheers.

---

### Post by logos34 on 2007-02-21
The Debian GNI linux driver check page is showing that sata works ('Yes') with ata_piix module/driver:

808624d1	Yes	Intel Corporation	82801EB (ICH5) SATA Controller	**ata_piix**

Does it show up in
> lsmod
?

If so try loading it and add it to the modules list:
> modprobe ata_piix

> gksudo gedit /etc/modules

Add 
**ata_piix **
to the end.
Save and close.

Ctl+Att+Backspace to restart.


Edit: link to driver page
**[http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)**

---

### Post by dignick on 2007-02-22
The current situation is the computer has 6.06 installed and working fine.  I did lsmod and ata_piix was in the list, however it is not in the list of available drivers on the 7.04 herd 4 and presumably 6.10 install cds.

When at the driver selection stage, if I enter the console and run lsmod I can see ata_piix is loaded which seems very odd.

I've had a look in the bios but there are no relevant options to change.  The hard drive is on the 2nd port (for some reason it seems to work faster).

A couple of pages I've come across with similar problems:

[Link]("http://ubuntuforums.org/showthread.php?t=291343")

[Link]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/19749")

The second link may not be relevant.

---

### Post by dignick on 2007-02-23
Any ideas?  Don't know what to try now.

---

### Post by dignick on 2007-02-24
Anybody have any ideas?  I would quite like to get this working and if it's a bug which it presumably is then it needs reporting.

---

