---
title: "dpkg: failed to open package info file"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by jonny_bowes on 2010-12-12
He all!

Full error dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: Input/output error

Runing 10.10 on USB.All was fine until a week ago then when trying to update I get that error.

Ive followed instructions in many threads to no avail. Heres what ive done and  the result.

sudo apt-get update

No error,all download fine

sudo apt-get upgrade

Preconfiguring packages ...
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

sudo apt-get install -f

dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

sudo dpkg --clear-avail && sudo apt-get update
dpkg: failed to link '/var/lib/dpkg/available' to '/var/lib/dpkg/available-old' for backup of available database: Input/output error

sudo rm /var/lib/dpkg/available
rm: cannot remove `/var/lib/dpkg/available': Input/output error

sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
cp: accessing `/var/lib/dpkg/available': Input/output error

Any help would be great!!

---

### Post by drs305 on 2010-12-12
It may generate the same error message, but there is a specific command to remove the file. Try:

```
sudo dpkg --clear-avail
```

---

### Post by jonny_bowes on 2010-12-12
sudo dpkg --clear-avail
dpkg: failed to link '/var/lib/dpkg/available' to '/var/lib/dpkg/available-old' for backup of available database: Input/output error

---

### Post by matt_symes on 2010-12-13
Hi

What happens if you type 

cat /var/lib/dpkg/available

Can you see the contents of the file?

Kind regards

---

### Post by jonny_bowes on 2010-12-13
Hi Matt,

ubuntu@ubuntu:~$ cat /var/lib/dpkg/available
 cat: /var/lib/dpkg/available: Input/output error

booooo

---

### Post by matt_symes on 2010-12-13
Hi

From a USB pen drive? Hmmmm. 

I am beginning to think it's a hardware issue. Pen drives are not great for OS's as the cells have a life time.

From (if you trust wiki) <someone will pick me up on this if it is no longer revelent>

[http://en.wikipedia.org/wiki/Flash_memory#Memory_wear](http://en.wikipedia.org/wiki/Flash_memory#Memory_wear)

> Another limitation is that flash memory has a finite number of  program-erase cycles (typically written as P/E cycles). Most  commercially available flash products are guaranteed to withstand around  100,000 P/E cycles, before the wear begins to deteriorate the integrity  of the storage.[[7]]("http://en.wikipedia.org/wiki/Flash_memory#cite_note-6") [Micron Technology]("http://en.wikipedia.org/wiki/Micron_Technology") and [Sun Microsystems]("http://en.wikipedia.org/wiki/Sun_Microsystems") announced an SLC flash memory chip rated for 1,000,000 P/E cycles on December 17, 2008.[[8]]("http://en.wikipedia.org/wiki/Flash_memory#cite_note-7")


Kind regards

---

### Post by jonny_bowes on 2010-12-13
Hi Matt,

thanks for input.This pendrive is about  2 months old,max.I only boot from it a few times a week.
I'll fdisk it anyway to see.

---

### Post by matt_symes on 2010-12-13
Hi

I have edited this post a couple of times because i did not want to give incorrect information.

I assume you have installed Ubuntu to the pen drive and it is not a LiveUSB?

If this is so then check the filing system by opening a terminal and typing

sudo touch /forcefsck

This will force a filing system check the next time the pen drive is booted.

Also, i would try to get some software to validate the pen drive itself to check for hardware problems.

Kind regards

---

### Post by AllGamer on 2011-05-18
i've got exactly the same issue

so far i got all the same feedback from the OP, and nothing seems to be working.

at the moment trying to fix it from another machine via live CD

-- Update 1 --

found the problem...
I ran **testdisk** and it gave me this:
**Warning: Bad starting sector (CHS and LBA don't match)**

seems like a simple repartitioning with **Gparted** using match to **Cylinder** instead of **Mib** should solve the problem




-- Update 2 ---

**SOLVED!**

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 32 GB / 30 GiB - CHS 3948 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT32 LBA                0   0 33  1973 254 63   31712278 [LINUX-USB]

Bad relative sector.
 2 P Linux                 1974   0  1  3947 254 63   31712310 [casper-rw]

```

after it booted back into the OS, it no longer had i/o errors

---

### Post by AllGamer on 2011-05-18
just an additional note, it also helps to mark all the bad sectors if any on the USB stick

sudo e2fsck -c -k -C 0 /dev/sdb2 (replace with your usb device location)

---

