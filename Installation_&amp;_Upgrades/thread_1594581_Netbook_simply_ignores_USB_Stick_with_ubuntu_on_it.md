---
title: "Netbook simply ignores USB Stick with ubuntu on it"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Prysewhert on 2010-10-12
Hello guys,

I did everything according to [this]("http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/") instruction. I went into the BIOS of my Eee 1018, set the usb drive as the first one in the priority list and restarted the system.

it simply **ignores **the stick and continues to boot windows. 

besides, i can rarely access the bios. most of the time when i hit F2 it shows me options to launch windows 7 in a variety of ways, but thats not what i want. 


please help me

---

### Post by Hakunka-Matata on 2010-10-12
I would make sure the USB Drive formatting and it's install file are good.  Look at it with a disk partition tool, try it on another computer to see, if it's not right, BIOS will simply skip it and go to the next boot device.

Is it a FAT32 partition?  for example

---

### Post by Prysewhert on 2010-10-12
> **Hakunka-Matata said:**
> I would make sure the USB Drive formatting and it's install file are good.  Look at it with a disk partition tool, try it on another computer to see, if it's not right, BIOS will simply skip it and go to the next boot device.

Is it a FAT32 partition?  for example

yes, the program i did that with formatted the usb drive to fat32.

stick looks good, otherwise. no problems.

---

### Post by Skaperen on 2010-10-12
If you are making the USB memory sticks under Linux, you could use my special hybrid image and just use dd to record it.  The hybrid image, instructions, are here:

```
slashusr.net/ubuntu/10.10/ubuntu-10.10-netbook-i386.iso.img
slashusr.net/ubuntu/10.10/README.txt
```Put http:// in front to make the URL (it's not ready for spiders to find it, yet).  Checksums are:

```
8efb610586f0e01789801b8ebea1e047 *ubuntu-10.10-netbook-i386.iso.img
e9a5b3a422012685190c309be2055461  README.txt
```This image format is called hybrid because it also still works as an ISO.  You can dd it to a flash drive or cdrecord it to a CDr/DVDr.  The Ubuntu and Kubuntu desktops in amd64 and i386 are also in that web directory. I have found this image format works in many places where a unetbootin created image fails to.

---

### Post by Prysewhert on 2010-10-12
it suddenly worked. after the 15th restart, the ubuntu menu appeared. dont know why. 

now i installed that thing, entered my name and my password. in the background the software was installed, but i cant click the "next" button. it just isnt active. but i cant find anything that might be missing. 

:-/

/solved, the name i entered musnt containt capital letters.

weird.

//marked as solved.

---

### Post by mörgæs on 2010-10-12
Good, please mark the thread 'solved'.

---

