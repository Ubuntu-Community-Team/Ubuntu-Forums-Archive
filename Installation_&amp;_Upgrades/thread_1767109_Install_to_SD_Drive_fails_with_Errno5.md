---
title: "Install to SD Drive fails with Errno5"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by RichFlorida on 2011-05-25
I am trying to install the netbook 10.04 version of Ubuntu on an Asus EeePC 1201HAB. 

The netbook had a 4G SD Drive that I use instead of a hard disk.

Every time I try to install to the 4G drive the install stops at 43% with [Errno 5]. I have checked the drive, reformatted the drive, re-partitioned the drive and I do not get any errors on the drive except when I install.

Thanks in advance for your help.

Rich

---

### Post by Quackers on 2011-05-25
Welcome to UF :-)
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok boot from the live cd and at the first purple screen press any key. Then choose your language and on the next screen choose the "check cd for errors". If any error is found the disc is no good.
You can then try burning the image again using the slowest possible burn speed. Others have got past this problem by changing the brand of the cd.

---

### Post by RichFlorida on 2011-05-25
I verified the checksum and it is ok. Btw I am booting from usb, not CD.

---

### Post by psusi on 2011-05-25
There has to be more text and/or context to the error than "errno 5".

---

### Post by Quackers on 2011-05-25
The process (and error checking) is the same for cd and usb.

---

### Post by RichFlorida on 2011-05-25
As I said before the check sum is correct. 

The error(errno5) is a general read/write error.

---

### Post by Quackers on 2011-05-25
> **RichFlorida said:**
> As I said before the check sum is correct. 

The error(errno5) is a general read/write error.

I was referring to cd checking (or usb checking), not md5sum

---

### Post by RichFlorida on 2011-05-25
I completed both a read and read/write check on the usb drive without errors.

---

### Post by danieljames626 on 2011-07-19
I had this same difficulty and solved it. I burnt the .iso to a new disk and still had a problem. I used the usb disk creator and still had a problem trying to install from usb, even though ubuntu worked fine live off the cd's and the usb.

What seemed to work is that I downloaded the .iso again and started over.  It seems that somehow the error was either in the .iso at the time I did the initial download or the file was corrupted the first time I downloaded it.

Try downloading again.

---

