---
title: "Persistent USB isn't persistent"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by josephst18 on 2009-03-29
I have downloaded the 9.04 Beta, and burned it to a CD. Due to my reluctance to do stuff to my hard drive, I chose to install Ubuntu to my 8GB Patriot XPorter USB Drive. It was completely clean (just formatted as FAT32), and I started up the USB Startup Disk Creator. In order to make the install persistent, I gave Ubuntu 7 GB of space on the drive. After the process completed with no errors, I rebooted from the USB drive, and Ubuntu was there (Yes. I did take the CD out first). In order to test my new Ubuntu disk, I right clicked on the desktop, created a new file, and named it  **test.txt**. I then opened this file, wrote the word *test*, saved it, and rebooted. However, when my desktop opened again, the file was gone. Did I do anything wrong, is there a bug, or something else? I really want to get this new beta working, since it looks amazing.

---

### Post by jruss on 2009-03-31
I am having the same problem. I create a persistent usb using the jaunty 9.04 beta DVD and usb-creator. But the usb isn't persistent. Everything is reset after reboot. I think it this happens when you try to use more than 4 GB in usb-creator. The problem is that FAT32 can't have a file larger than 4GB. I have this in my ~/.usb-creator.log:

['dd', 'if=/dev/zero', 'bs=5378073556', 'of=/media/DIESEL/casper-rw', 'count=1']
dd: invalid number `5378073556'

The usb-creator program exited without any errors and the usb would boot up just fine. It seems like usb-creator should give a warning or limit the size when doing this on a FAT32 usb stick.

---

### Post by zanani on 2009-04-01
I used a SanDisk 4GB for Ubuntu 8.10 and got it working without problem (having failed a number of other distributions and solutions). Then I did the same with 9.04 and I had the same problems as you. Otherwise the boot-time improvement was significant for 9.04.

What is the proper procedure to report this problem to developers?

And can I direct the creation procedure to use less memory or use something else than FAT32 and get it working?

/z

---

### Post by andrewabc on 2009-04-01
Persistent USB worked fine for me on 2gb kingston, and 4gb oczrally2.

It remembered firefox plugin, different wallpaper etc.

---

### Post by zanani on 2009-04-01
I tried with a no-name 1GB stick. I booted with 8.10 on 4GB stick. Then I tried using the put Ubuntu on a stick utility from there but pointing to an ISO of XUbuntu 9.04 on the harddisk. I got an XUbuntu 9.04 which boots quickly and is persistent. Now I don't know if it is due to using 8.10 for installing, for XUbuntu instead of Ubuntu 9.04 or if it is because the stick is less than 4GB. Anyway I will try the same with another 4GB stick.

/z

---

### Post by andrewabc on 2009-04-01
I installed to usb from ubuntu 8.10

---

