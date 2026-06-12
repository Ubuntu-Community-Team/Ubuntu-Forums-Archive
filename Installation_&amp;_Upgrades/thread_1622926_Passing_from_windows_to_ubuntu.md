---
title: "Passing from windows to ubuntu"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2010-11-16
Hi,

I have been using for two year windows + ubuntu, now I would like to switch off completely from windows. I have a little problem with ubuntu, it can't manage the power of CPU, GPU and the others components as good as windows does. For instance the temperature of CPU is about 40-45 °F higher than in windows, the same for GPU. Furthermore the battery has 15-20% minus life. I have tried from 8.04 to 10.10 (32 and 64 bit).

I also have installed third party driver for GPU (nvidia). Where could be the problem? Are there capability to set the options like in windows where you can choose the frequency of pci-e, motherboard, wireless, etc.

Thank you in advance

---

### Post by Peter09 on 2010-11-16
What version of Ubuntu are you using. Earlier versions were not so good at power management, however the latest version (maverick) is very good.

---

### Post by dino99 on 2010-11-16
many users have this issue but be sure of bios settings first, then install the latest kernel (2.6.37 works fine)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)

[http://www.geekishblog.com/2008/08/advanced-power-management-in-ubuntu/](http://www.geekishblog.com/2008/08/advanced-power-management-in-ubuntu/)

---

### Post by erotavlas on 2010-11-16
> **Peter09 said:**
> What version of Ubuntu are you using. Earlier versions were not so good at power management, however the latest version (maverick) is very good.


I'm using ubuntu 10.10 with latest kernel available from repository 2.6.35.23-generic.

---

### Post by erotavlas on 2010-11-16
> **dino99 said:**
> many users have this issue but be sure of bios settings first, then install the latest kernel (2.6.37 works fine)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)

[http://www.geekishblog.com/2008/08/advanced-power-management-in-ubuntu/](http://www.geekishblog.com/2008/08/advanced-power-management-in-ubuntu/)

Thank you. The bios setting is good and is the same for windows and ubuntu. Now I will try your suggestions.

---

### Post by erotavlas on 2010-11-30
I have installed the last version of kernel 2.36.37rc2 [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/) but the problems are still here...

I'm not able to install this [http://www.geekishblog.com/2008/08/advanced-power-management-in-ubuntu/](http://www.geekishblog.com/2008/08/advanced-power-management-in-ubuntu/). My ubuntu 10.10 64 bit version can't find the Kpowersave package.

What can I do with the last link?

Thank you

---

