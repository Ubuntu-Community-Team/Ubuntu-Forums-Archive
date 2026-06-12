---
title: "Doubts about the kernel upgrade ..."
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by hectorsales on 2013-07-04
I decided to install ubuntu 12.04.2 LTS 64-bit (current version), I think it brings with kernel version 3.5, X.org 1.13 and table 9.0 as well my question is if these kernel versions and graphic controller are automatically update or you have to install it manually from the terminal when a new version ...


Best regards...

---

### Post by Frogs Hair on 2013-07-04
Kernel updates for the 3.5 version come via the update manager and graphics updates can depend on whether you are using proprietary drivers . See software & updates - additional drivers. Any updates for the default/Nouveau driver would also come from the software updater.

12.04 will not likely update to the 3.8 or 3.9 kernel, but due to having five year support that may change since it is the first desktop release to have extended support. Ubuntu releases in the past have stayed with the same kernel version for the life of the release with the exception of patches, security, and firmware updates.

---

### Post by deadflowr on 2013-07-04
You will stick with the 3.5 series kernel for the duration, but it it be kept up-to-date.
However, as of now, the raring kernel is available for precise in the precise repos, if you want it.
I believe that 12.04.3 will move up from 3.5 to 3.8, but not fully certain of that.
As far as xserver, version 1.14 just made it into the development branch, saucy, so time will tell if it too moves into the precise repos.

---

### Post by hectorsales on 2013-07-04
Thanks for the clarification, but I have a question if I installed a proprietary driver for example ati / amd graphics card and then upgrade the kernel and xserver graphic controller. The driver (ati/amd) can be broken ?...

Thanks...

---

### Post by Frogs Hair on 2013-07-04
Some people have had problems with both  ATI and Nvidia , so I would do some  research online and here about possible problems with the card and driver . I have the cube up and running on with Nouveau open source driver on a 13.04/Nnidia system. This is a surprise because I have had to use proprietary drivers prior to the latest open source driver. If your systems graphics perform to your satisfaction you may want to leave things as they are.

---

### Post by deadflowr on 2013-07-04
> **hectorsales said:**
> Thanks for the clarification, but I have a question if I installed a proprietary driver for example ati / amd graphics card and then upgrade the kernel and xserver graphic controller. The driver (ati/amd) can be broken ?...

Thanks...

it usually depends on how you installed them, first off.
Though it's always possible that upgrading those parts can break the system, you are less likely to get to that point if you installed the drivers from the additional drivers, than from ati/amd directly.

---

### Post by hectorsales on 2013-07-04
Thank you both for yours advices, before closing the topic I would like to ask how I can known the driver version that i download via additional drivers ... Example I have the graphics card AMD Radeon HD 3000 Series, the latest official drivers AMD include AMD Catalyst &#8482; 13.1 Proprietary Linux x86 Display Driver, this is the last driver amd that can be installed manually , but as you know the version I download via additional drivers ...I do not know if I explain correctly.

Thanks ...

---

### Post by Frogs Hair on 2013-07-04
If you resize the the additional drivers GUI or use the scroll bar you can see what drivers are available for your card .  You select the driver you want to use from the box on the left  and then select  apply changes to install .

---

### Post by hectorsales on 2013-07-05
> **Frogs Hair said:**
> If you resize the the additional drivers GUI or use the scroll bar you can see what drivers are available for your card .  You select the driver you want to use from the box on the left  and then select  apply changes to install .

Thank you, all right now ;););)

---

