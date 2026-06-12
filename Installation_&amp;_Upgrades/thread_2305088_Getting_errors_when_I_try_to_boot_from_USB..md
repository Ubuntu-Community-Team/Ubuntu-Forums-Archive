---
title: "Getting errors when I try to boot from USB."
date: 2015-12-02
forum: Installation &amp; Upgrades
---

### Post by Itson on 2015-12-02
**Hi people**. I'm turning to you since I'm trying to save the few string of hair that still remains ontop of my head. 


I've tried to install Ubuntu and other distributions of Linux on my computer many times for a year. It usually ends with me rage-quitting after many hours of online-search.


This is what I end up with after a few seconds on a purpule screen. Does this make any sense to you? Is it something that I've by mistake changed in my bios? I've got a Asustek M4A785TD-V EVO motherboard. (I'm running Windows 10 on the system without any problems and I intent to install Ubuntu on a separate SSD.)


[Bad picture of my screen]("http://imgur.com/vOKCcwV").



**I'm very thankful for replies.**

---

### Post by yancek on 2015-12-02
Did you download Ubuntu from the official site?
Are you actually trying to install Ubuntu or one of the many derivatives (Mint, Lubuntu, Kubuntu, etc.)?
Did you do an md5 checksum on the downloaded iso file?
The correct hashes are shown at the site below for the various Ubuntu derivatives.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

How to check it explained at the site below.  If you only have windows installed, scroll down the page and that is explained.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you put Ubuntu on a DVD by burning it as an image?  This is necessary as copying it is a waste of time.
Did you use some software to create a bootable flash drive?  If so, what was it?

---

### Post by Itson on 2015-12-02
> **yancek said:**
> Did you download Ubuntu from the official site?
Are you actually trying to install Ubuntu or one of the many derivatives (Mint, Lubuntu, Kubuntu, etc.)?
Did you do an md5 checksum on the downloaded iso file?
The correct hashes are shown at the site below for the various Ubuntu derivatives.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

How to check it explained at the site below.  If you only have windows installed, scroll down the page and that is explained.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you put Ubuntu on a DVD by burning it as an image?  This is necessary as copying it is a waste of time.
Did you use some software to create a bootable flash drive?  If so, what was it?

Hi. Thanks for your response.

I'm trying to install Ubuntu 15.10. I'm certain that the bootable flash drive works (tried it on my laptop, which I installed Ubuntu with). Created it with Rufus 2.5. I've had Ubuntu installed on this computer three years ago and that went smoothly from what I recall. 

Anything else that I can try?

---

### Post by Itson on 2015-12-02
Changed USB and got these errors when booting up: [https://youtu.be/wR28V--tX9c](https://youtu.be/wR28V--tX9c)

---

### Post by ubfan1 on 2015-12-03
Looks like a disk problem, maybe try the "check disk for defects" menu choice.  Could be video too, did you try any of the function key options like "nomodeset"? Is the SSD in an external enclosure?  TRIM does not work over USB, so you might really be out of filesystem space.  The only way I know of to handle that issue is to use the SSD internally and run TRIM, then replace in the external encl.

---

