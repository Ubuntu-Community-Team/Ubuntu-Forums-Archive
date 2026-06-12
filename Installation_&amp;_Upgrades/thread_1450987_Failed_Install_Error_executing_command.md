---
title: "Failed Install Error executing command"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by fireball961 on 2010-04-09
hay all! 
I have been really wanting to install Ubuntu on to my Notebook. but i have come up with this error. see attached jpg.
I am installing it on a clean Partitioned drive (B:\) with 5 Gb of space. the format is NTFS. i have tried it without formating it, i have tried leaving it unallocated. still no joy.
I'm am running Windows 7 32bit, and trying to install Ubuntu 32bit.
I'm using a dell Inspiron 1525.

If anyone can help out this will be much appreciated.
also log file is also attached it was to large to insert as a standard txt file so i zip it.
Thank-you so much in advance.
DPG 2010

---

### Post by kaustubhaj on 2010-12-24
im having the same error....someone plz help

---

### Post by Frogs Hair on 2010-12-24
Check the first link for instructions on 32 bit installation . If you want the 10.10 version of Wubi use the second link and scroll to the bottom of the page to download the Wubi installer.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

---

### Post by kaustubhaj on 2010-12-25
i downloaded wubi.....what am i supposed to do after that???
and im using a usb to install ubuntu and i wanted to install ubuntu inside winddows. i have a lot of partitions and i have to hdds 320 each when i boot from the usb drive it does not show me my partitions. I have made a separate partition for ubuntu which is 14.7 gigs the name of the partition is "L:\" when i use wubi i get the error which is shown above....i even tried burning to a different cds(6 to be precise) i even formatted my pc once and i also tried installing ubuntu 10.04 but no sucess...the same error again..and when i booted from the cd i selected u alongside another operating system its only showing me options to erase all my data on the hdd and install ubuntu..plz man help me!! :cry:

---

### Post by bcbc on 2010-12-25
Most likely it's a dynamic drive. You can't install ubuntu (with or without wubi) on those. (That's why those partitions don't show up, because they're not in the partition table - only windows knows about them).

---

### Post by kaustubhaj on 2010-12-25
then what do u suppose i should do?????:confused:

---

### Post by bcbc on 2010-12-26
> **kaustubhaj said:**
> then what do u suppose i should do?????:confused:

That's something I can't answer for you. 

If you want to try out ubuntu you can use your USB to boot in 'live USB' mode - it's not as fast but it's pretty decent. Or you can install Ubuntu to an external USB drive and ensure the grub bootloader stays on that drive - then just select to boot from USB when your want to boot Ubuntu.

If you have to have it on one of your internal drives, then I imagine you'll have to switch from dynamic partitions to logical partitions - 1 extended, multiple logical. I'm not really sure what the benefit of dynamic partitions are, unless your drive already came with 4 primary partitions and you can't delete one of these.

---

### Post by kaustubhaj on 2010-12-26
what if i install ubuntu on an external hdd?
will it run fast like that??i have a usb but its slow and i cant install my graphic card drivers on it coz of the lack of space....so i thought maybe i can use an external hdd

---

### Post by bcbc on 2010-12-27
Yes it will run fast on an decent external drive. Make sure you install the grub bootloader only on the external drive and then when you want Ubuntu to boot you just override at boot time - whatever your boot options key is.

I haven't used the new ubiquity installer that came with 10.10 - apparently there are some issues with it So you might want to read up on that first. This thread talks about installing on a second hard drive but is relevant and has some interesting links with more info as well: [http://ubuntuforums.org/showthread.php?t=1647379](http://ubuntuforums.org/showthread.php?t=1647379)

---

### Post by kaustubhaj on 2011-01-01
i tried to install ubuntu on an external hdd it didn't work....:-(

---

### Post by mizkewl on 2012-07-28
Hello everybody,
I have the solution for you. Your problem is, that wubi needs to access the Boot Configuration Data which is located on the hidden SYSTEM partition that Windows 7 and Vista create. But wubi cannot access the BCD because this partition is hidden. I had the same problem, but here is the solution.
1. Download Partition Wizard 7 [http://www.partitionwizard.com/download.html](http://www.partitionwizard.com/download.html)
2. Assign the hidden partition a letter
3. Run wubi
4. Be happy :)

I hope this helped.

p.s This was wrote from Ubuntu :)

---

