---
title: "Bootable LIVE USB weird , please help :)"
date: 2016-02-10
forum: Installation &amp; Upgrades
---

### Post by sam170 on 2016-02-10
Hi,

I have been trying to make a bookable live USB with more than 4gb + of persistence , I tried many methods googled a lot none seemed to work so please help, these are the methods I tried:

Method 1 =  [http://ubuntu-usb-large-persistent-storage.blogspot.ae/](http://ubuntu-usb-large-persistent-storage.blogspot.ae/)   , 

Problem = I followed it exactly made casper-rw as ext 4 partition manually followed exact words exact way but in the end when I try to boot it would just bring me to a black screen with a blinking underscore key. I tired allign with mib and cylinder both didn't work.

Method 2 = I used my 8gb usb which had ubuntu without persistence to install ubuntu on my 64gb sandisk extreme , I partitioned the USB with 1 being for ubuntu as ext4 and the other being for normal use as ntfs.

Problem = This worked fine I booted the first time it seemed to work perfect I was unsure about persistence so I rebooted after an automatic update that updated packages and my usb wasn't listed in boot options anymore. UEFI never         worked the one that did work was normal legacy one but that option disappeared.

Method 3 = I tried Installing again this time with 4 partitions , 1 as NTFS for normal use , 2nd as / root partition , 3rd as home partition , 4th as swap partition.

Problem = This time it says please insert boot able device and reboot and press enter

What am I doing wrong? If these methods are wrong what's the right method?

---

### Post by sudodus on 2016-02-10
Welcome to the Ubuntu Forums :-)

I suggest that you try with the tool ***mkusb***. See the following links

[mkusb](https://help.ubuntu.com/community/mkusb)
[Persistent live systems](https://help.ubuntu.com/community/mkusb/persistent)

***mkusb*** will help you create a partition for persistence automatically, and you can use the whole USB drive.

---

### Post by Bucky Ball on 2016-02-10
*Thread moved to **Installations & Upgrades**.*

Welcome. Default font for future reference thanks. I have edited your post. Please only change defaults to highlight something here and there, not whole sentences and paragraphs.

Good luck. :)

---

### Post by sam170 on 2016-02-10
Thanks guys
And sorry I posted on wrong section I will try again

---

### Post by sam170 on 2016-02-10
I will try mkusb now and see if it works

---

### Post by C.S.Cameron on 2016-02-14
Persistent partitions are not working with Ubuntu 64bit, 14.04 and later, using SDC / UNetbootin or Universal, 32bit should work ok.
For a 64bit persistent partition install, a grub2/iso install as Sudodus suggests should work.
I prefer a four partition Full install myself, 1st as NTFS or FAT32 for normal use, 2nd as ext4 / root partition, 3rd as ext2 /home partition, 4th as swap partition.
Not sure why yours stopped working after update, perhaps try it again.

---

