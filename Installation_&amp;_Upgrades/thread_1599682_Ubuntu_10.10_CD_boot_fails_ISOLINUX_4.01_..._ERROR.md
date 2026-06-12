---
title: "Ubuntu 10.10 CD boot fails ISOLINUX 4.01 ... ERROR no configuration file found"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Johntai on 2010-10-18
I have downloaded the 10.10 installation image and burnt it to CD.  Once before reading the instructions too carefully and then again at very slow speed.  When trying to boot the CD on an old Compaq DeskPro I get two lines on the screen and am unable to proceed any further.

ISOLINUX 4.01 debian-20100714 ETCD ...
ERROR: no configuration file found

The CDs boot up okay in a newish HP laptop and I am able to boot up a Knoppix CD that I have kicking around so it seems to be the combination of the CD and the machine that is causing the problem.  

The PC doesn't seem to support booting from USB, if the BIOS options are anything to go by so I don't think I have any other options but to install from CD.

Thanks in advance

Postscript: I am able to boot the 10.04 CD so I will try installing that and then upgrading to 10.10.

---

### Post by bandicochi on 2010-12-23
Hello there...same problem here with a laptop Compaq presario 2100.
Mine doesn't even read the image burned on the CD but cd drive does read data as pics and music.( not even error messages when booting inserted CD)
Same results with USB, no option to boot from it (surely as you, i am pretty confident we are saving into the USB the information in the right way)
 I have been looking around what could the problem be but no lucky at all. 
Also have ordered a disc from Ubuntu 2 but did not get them :(
 Hope we can get a logic solutions and get fixed this or a understandable reason to quit trying from my side, at least.

Cheers! :)

PS: Sorry for not replying to your post and putting my problems instead of :S

---

### Post by sikander3786 on 2010-12-23
Welcome to the forums :-)

So how was the CD created? Which software was used and did you create a "Data Disc" or "Burn image to disc"?

Once again, recheck the Bios boot order and make sure CD/DVD drive is set as first boot device.

Prior to burning the image to disc, check the image for any defects and make sure it is healthy.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the image is ok, burn a new disk and this time, at the lowest possible speed. 4x is recommended.

Hopefully, we would be able to solve this issue soon.

---

### Post by ChristopherB on 2011-05-06
> **sikander3786 said:**
> Welcome to the forums :-)

So how was the CD created? Which software was used and did you create a "Data Disc" or "Burn image to disc"?

Once again, recheck the Bios boot order and make sure CD/DVD drive is set as first boot device.

Prior to burning the image to disc, check the image for any defects and make sure it is healthy.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the image is ok, burn a new disk and this time, at the lowest possible speed. 4x is recommended.

Hopefully, we would be able to solve this issue soon.

I have either CD/DVD or HDD so am using a usb hdd which works on some machines yet not on the "Ga-M61P-S3". 

Is there a way to type in the image that it requires?  like: linux-image-############
?
Christopher

---

