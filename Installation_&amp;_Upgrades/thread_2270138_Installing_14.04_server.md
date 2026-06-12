---
title: "Installing 14.04 server"
date: 2015-03-20
forum: Installation &amp; Upgrades
---

### Post by l-wolf69 on 2015-03-20
I just formatted by drive with gparted then created a dvd with k3b of the 14.04 .iso.  I have the boot disk as the cd.  When I put the dvd in the other machine I get...
"error: no such partition.
grub rescue>"

What do I need to do to get the installation to start? Also, I have a usb drive that originally keeps bombing out because of some * in the installation files.

Thanks in advance.

K

---

### Post by nerdtron on 2015-03-20
You may try creating a bootable USB drive using startup disk creator. Be sure to format the USB stick as fat32.
follow this: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

If you are on Kubuntu, I think the tool you need is the usb-creator-kde.
```
 sudo apt-get install usb-creator-kde
```
Then use the KDE startup disk creator.

---

### Post by l-wolf69 on 2015-03-20
i have 2 of those and neither work, plus they are finalized and basically trash.  I had server 10 on the drive but havent used it in yrs and forget the login/passwords. I tried reformatting over but the install from the usb failed b/c (according to research) there are files in the server live usb that have * in them where the usb drive is and bomb out at those points.  I have 7 dvds left and just want to run with 1 of those. 

Back to the original question...why is the dvd I burned not working?

Thanks for the idea though.

---

### Post by nerdtron on 2015-03-20
I haven't burned a CD in ages but here are some points for initial checking.
Did you check the md5sum of the iso file?
Did you burned the image as Image file?
Did you burn it on a slow speed? (Just to make sure to reduce errors)
Try to boot it on another computer and see if you have the same error. (Just to isolate the the CD is indeed the problem).

> 
"error: no such partition.
grub rescue>"

Finally, this error, I believe happens when you reformatted the drive previously Ubuntu is installed on. Meaning your server did not even tried to boot from CD. Possibly It can't find any boot image on the CD. Please try to burn the CD again and make sure it is bootable.

---

### Post by l-wolf69 on 2015-03-20
I tried booting with a windows drive in there and it just boots into windows. So burning the disks did not work.  Suggestions?

---

### Post by l-wolf69 on 2015-03-20
I think the problem might be that I am buring dvds and the other machine is actually a cd-rom.  I will swap it out with a dvd tomorrow.

---

### Post by l-wolf69 on 2015-03-21
I swapped a dvd for the cd and of course that fixed the issue.  Thanks for the help!

K

---

### Post by l-wolf69 on 2015-03-21
Although I have the server running I am trying to connect via webmin.  I understand this maybe a different forum topic now but I was wondering if you knew why I am getting this issue...

I connect using [https://127.0.0.1:10000](https://127.0.0.1:10000) plus my pw but it always tells me 
[h=3]Login failed. Please try again.[/h]
I know that the ip is correct and so is the un/pw.  So why am I getting this?

Thanks,
K

---

### Post by nerdtron on 2015-03-21
no idea. I don't use webmin.

---

