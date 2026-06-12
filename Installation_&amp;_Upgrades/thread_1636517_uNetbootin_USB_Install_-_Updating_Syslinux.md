---
title: "uNetbootin USB Install - Updating Syslinux?"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by Holymartyr on 2010-12-03
Hey, I used unetbootin to install Ubuntu 10.04 to my usb drive so I could plug it into the school computers and boot into linux. I have sucessfully done that, and it works on all the school computers except for the one I am currently on in my Engineering class. I have to use plop boot manager to boot from the usb. My thoughts are that if I were to update my syslinux from 3.8 (I think is what I have) to 4.0, it might be able to boot from USB without the plop boot manager CD. 

So my main question is how do I  update syslinux on my USB, I know my way around terminal decently well, but a step by step guide would be much more helpful to me. Thanks a bunch.

---

### Post by sikander3786 on 2010-12-03
You only need plop boot manager when your Bios is not capable of booting a USB directly. And if it is unable to do so, I don't think upgrading syslinux would be of any help here.

---

### Post by C.S.Cameron on 2010-12-03
I believe with UNetbootin, syslinux is in a squashfs file that is real uneasy to update.
You could try a Full install to flash drive, but I think I agree with Sikander.

---

