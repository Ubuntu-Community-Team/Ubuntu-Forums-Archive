---
title: "ati radeon 9250 problems"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by sewercake on 2007-04-29
HI
I followed the instructions for downloading and installing the drivers for my ATI radeon 9250 with this howto [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25)

I used the 6.10 instruction (i am using 7.04) and when I did the "fglrxinfo" command, this came up
> X Error of failed request:  GLXBadContext
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  15
  Current serial number in output stream:  15


Does anyone know the problem here?
thanks



-Sewercake

---

### Post by neildarlow on 2007-04-29
Is there any reason why you want to use the proprietary ATI drivers when the Xorg radeon driver works nicely with the 9250?

I have similar hardware (a Connect3D 9250-based card with 256M of RAM) and the default install of Feisty permits operation of Compiz through the Desktop-effects Manager out-of-the-box.

---

