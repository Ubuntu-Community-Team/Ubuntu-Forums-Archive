---
title: "Ubuntu Lucid 64bit Intel Processor"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2010-07-24
Just built a new computer with Intel i5 750 (quad core) and intel P55A chipset.

The 32bit Lucid works fine and can use 3.6G of my 4G memory.

The Ubuntu download page does not recommend 64bit for daily usage?

dailyhttp://www.ubuntu.com/desktop/get-ubuntu/download

Also it lists the image as AMD64.

Can anyone tell me if this will work with Intel 64 bit processors and also
can you mix 32 and 64 bit applications, in other words, if an application like eboard was wrote for 32bit CPU's will it run ok on 64 bit CPU's ?

Thanks in advance.

---

### Post by PaulReaver on 2010-07-24
sorry.  Yes amd64 will work with your intel.




to use the missing ram on a 32 bit ubuntu install a PAE enabled kernel. I think there is a PAE kernel in the repos (i'm not sure I'm using mandriva)

A 64 bit ubuntu causes problems with adobe flash.

---

### Post by oldos2er on 2010-07-24
64-bit Ubuntu works just fine for everyday use. If you want to run 32-bit app on it you will need to install 1a32-libs.

---

