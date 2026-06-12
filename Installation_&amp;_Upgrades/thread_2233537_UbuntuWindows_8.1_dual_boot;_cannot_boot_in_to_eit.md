---
title: "Ubuntu/Windows 8.1 dual boot; cannot boot in to either OS"
date: 2014-07-09
forum: Installation &amp; Upgrades
---

### Post by keri3 on 2014-07-09
So, I've been wanting to dual boot my laptop for a while now.. decided I could do it with the help of a couple very specific tutorials, but I was wrong :p
By the way, I am using a Dell inspiron 15r which has UEFI as opposed to BIOS

My problem is that at this point in time, my laptop can not boot in to either ubuntu or Windows. When I power up, I get something like:
Searching media: [fail]

So first I partitioned off 100gb, backed up my stuff and load ubuntu 14.04 onto ausb stick. I then rebooted, disabled secure boot, and went straight to the ubuntu install. Contrary to my tutorial, I did not choose to manually choose partitions.. I let ubuntu take care of that (unintentionally). It seemed to install correctly. I rebooted, and could not boot into either os. I plugged my usb back in and ran the install option again. This time I chose the custom partition option. I noticed that ubuntu had been installed on some mysteriously acquired 30gb, on disk /dev/sdb, where as Windows, and my 100gb were on disk /dev/sda. I reformed the partition table in /dev/sdb, and built the partitions according to my tutorial: /boot, /, /home, swap. The same result happened after installing. This time, from the usb, I chose the run but don't install ubuntu option. From the terminal, I installed and ran boot repair. It couldn't find a partition with the boot-grub flag or something, so I assigned the flash to /boot using gparted. I then followed the instructions from boot repair, uninstalling and reinstalling grub. 
Here is my report: [http://paste.ubuntu.com/7769283/](http://paste.ubuntu.com/7769283/)
Predictably, my machine still cannot find a drive to boot from.

Any help will be appreciated! Though I would like to prioritize regaining access to Windows. Please let me know if I need took be more specific about anything.

Thanks in advance,

---

### Post by mastablasta on 2014-07-09
what happens if oyu set the computer to boot form second hard disk as it is there that you installed grub right now.

it says in the end of script:

> Please do not forget to make your BIOS boot on sdb (32.0GB) disk!

since you are using UEFI i take it you also use the 64bit OS.

what is this 32GB disk? is this an SSD disk? was Windows 8 installed on this disk? is the whole disk some hybrid disk? 

dis you want to install on sda3 ? you gave wrong instructions for install then. install doesn't do anything on it's own.

edit: correction i just saw this in script:

```
Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
```

you installed grub all over the place it seems...

---

### Post by keri3 on 2014-07-09
Ok, so I am by no means an expert on this but as I understand it, the 32gb is a built in ssd, used by Windows, which I accidentally installed ubuntu on. Now I need to fix Windows, by resetting whatever was in the ssd, then install ubuntu properly.. :)

---

### Post by oldfred on 2014-07-09
You show Windows in stalled in BIOS boot mode on sda, as there is no efi partition and it has the standard 100MB boot partition.

Use Boot-Repair's advanced option and choose Windows and drive sda to reinstall a Windows boot loader to sda.
In your UEFI/BIOS choose legacy/BIOS/CSM mode as both Ubuntu & Windows are BIOS based. Do not boot in UEFI mode.
You may also have to mode boot flag from sda1 to sda2. If it only boots recovery mode from sda1, then you want to boot from sda2 which is main install. It just depends on how BCD is configured which we cannot parse from Linux.

---

