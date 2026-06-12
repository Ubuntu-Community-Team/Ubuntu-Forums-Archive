---
title: "new user - md5 error on Ubuntu 5.10 installation cd"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by munwai on 2005-10-26
Hello

I am new to linux but am interested to use Ubuntu after reading the reviews

However I am experiencing problems with burning the installation CD.  I downloaded the ISO images from the Ubuntu website.  A MD5 check on the downloaded file  was confirmed ok.  However after burning to several CDs and running a MD5 check on all the files on the CDs, I get errors on 2 files each time

\install\netboot\pxelinux.cfg\default and
\install\netboot\pxelinux.0

I have downloaded the ISO images from various official Ubuntu sites and get the same error.  Have also tried burning the CD on two different CD burners on different machines and get the same error.

Anyone with any ideas on where it is going wrong?

Cheers

---

### Post by aysiu on 2005-10-26
This error occurs during the MD5 checksum? Or during boot-up? I'm confused--when does this error pop up?

---

### Post by munwai on 2005-10-26
error occurs when I run the MD5 checksum on the burnt installation cd

---

### Post by Irony on 2005-10-26
What instruction do you use to checked the sum of the burnt disc - I couldn't find the sum for the burnt disc; it is presumably different to the .iso.

---

### Post by munwai on 2005-10-26
After burning the CD, if you browse throught the contents of the CD you will find a MD5 file called "md5sum", this file seems to list all the files on the CD together with the corresponding md5 checksum value.

I use md5summer ([www.md5summer.org](www.md5summer.org)) to verify the checksum of the files on the CD.  I get the following error on the following 2 files (this is copied direct from the report generated).

.\install\netboot\pxelinux.cfg\default ERROR: D:\.\install\netboot\pxelinux.cfg\default does not exists.
.\install\netboot\pxelinux.0 ERROR: Checksum did not match.

When I look in the \install\netboot\ directory these 2 files exist but are 0KB in size.

I am stumped as to what is happening ......

---

### Post by MTCONE on 2008-05-11
*bump*

Same issue with Hardy. Checked CD on diff comp and works fine. MD5 error on only one comp.


Tried diff CD drives, tried diff CDs, tried diff IDE channels. No matter what I do, I get MD5 error.


Cannot find solution.

---

