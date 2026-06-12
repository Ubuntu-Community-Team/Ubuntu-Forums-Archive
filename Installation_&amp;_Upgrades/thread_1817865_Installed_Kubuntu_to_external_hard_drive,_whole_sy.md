---
title: "Installed Kubuntu to external hard drive, whole system is very slow"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by Darkness Des on 2011-08-03
My father installed Kubuntu to his external hard drive to try it out, however, it is running extremely slowly. It takes a good minute and a half to boot to the Plasma desktop and it even seems to run faster off of the LiveCD.

His system easily meets the specifications to run Kubuntu (4 gigs of RAM, decent NVIDIA graphics card) yet it slows to a crawl immediately upon booting. Does anyone know how to fix this? The hard drive is a Western Digital MyBook, 475GB model.

Any help is appreciated.

---

### Post by ankspo71 on 2011-08-04
Hi,
It could be that the external drive is limited by speed of the connection to the computer (USB?). This link can explain it better than I can: [http://www.streamreader.org/askubuntu/questions/21741/performance-cost-of-running-ubuntu-from-external-hard-drive](http://www.streamreader.org/askubuntu/questions/21741/performance-cost-of-running-ubuntu-from-external-hard-drive)
(be sure to read the replies)

As for the Live CD being faster than the External drive... I'm pretty sure an internal cdrom drive has a much better connection to the mainboard, but cdroms are also limited in speed because of the RPM of the CD (in comparison to the RPM of an internal hard drive). 

It is possible that the speed is not restricted by the connection from the external drive to the computer though, so I would open the terminal and paste the following commands to be sure it isn't something else:

```
free -m
```

This command can check to see if any memory is being dumped into swap memory. Memory in swap runs very slow compared to RAM. Even a small amount of swap usage can seriously effect overall computer performance.

```
top
```

This command will let you monitor some processes running in the background. With this command you will be able to pinpoint which processes are consuming too much memory or too much CPU percentage. 

PS. You can see swap usage in 'top' too, but 'free' gives a little more detail on memory and swap.

Hope this helps.

---

### Post by ankspo71 on 2011-08-04
Hi,
Here is a comparison of speed for USB connections...

Serial Bus Transfer Rate (USB 3.0)	5 Gb/s (Max)
Serial Bus Transfer Rate (USB 2.0)	480 Mb/s (Max)

Source: My Book Essential Edition 1 TB Hard Drives ( WDBACW0010HBK) 
[http://www.wdc.com/global/products/specs/?driveID=886&language=1](http://www.wdc.com/global/products/specs/?driveID=886&language=1)

---

### Post by tommpogg on 2011-08-04
Definitively an external hard drive is much slower than an internal one

---

### Post by Darkness Des on 2011-08-04
Ah, okay. I continue to tell him that but he insists the no, "it HAS to work." I'll put in another internal drive or use a virtual machine. Thank you very much.

---

