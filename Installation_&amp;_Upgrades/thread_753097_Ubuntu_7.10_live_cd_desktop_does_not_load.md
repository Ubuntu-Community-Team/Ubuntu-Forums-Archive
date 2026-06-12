---
title: "Ubuntu 7.10 live cd desktop does not load"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by scottptn on 2008-04-12
Hello,

I got Ubuntu 7.10 (Gutsy Gibbon). When i boot the live CD on my laptop , i get the option screen where we have options to start or install ubuntu , start in safe graphics mode etc...
When i select 'start or install ubuntu', i get the usual splash screen , then a screen that shows all the drivers getting loaded etc.. , then when it reaches the stage where the desktop is to be loaded , i get a mouse pointer for a while and then the whole screen goes blank . The desktop does not load.
Ive tried the following things but none of them worked :

1) I tried using vga=771 as a boot option .

2) I tried booting in safe graphics mode , but the same thing happened.

My video card is Via Chrome9 HC IGP . 

So is there any way this issue can be resolved ?.

Thanks a lot.
'

---

### Post by Pumalite on 2008-04-12
Install with the Alternate CD.

---

### Post by scottptn on 2008-04-12
Thanks for the reply Pumalite. Well, i had requested the Ubuntu 7.10 CD online from [shipit.ubuntu.com]("http://shipit.ubuntu.com") . 
I received a single CD . So i dont have an alternate CD . Anything else that can be done ?

Thanks.

---

### Post by Pumalite on 2008-04-12
You can download from here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Check box below sign 'Start Download'
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Burn at 4x or less onto CD-R

---

### Post by scottptn on 2008-04-12
Thanks for the links Pumalite . Apart from using the alternate CD , is there any way i can make the current CD work ?. Any way to start the installation directly without going to the desktop ?.
Also, what do you think is the reason why the desktop does not load in my case.

Thanks.

---

### Post by Pumalite on 2008-04-12
I believe this is your problem:
'Via Chrome9 HC IGP '
No amount of boot parameters will jump through that loop.
Here are some common ones if you want to try:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)

---

### Post by scottptn on 2008-04-12
Thanks a lot Pumalite . Well, is this a general problem of Ubuntu 7.10 with Via Chrome9 HC IGP or is it just the problem with the disk i have received  ?. I had tried loading Ubuntu 6.06 (Dapper Drake), and i was able to get to the desktop with that CD . It is only with 7.10 , that im facing this issue . Is this issue already documented somewhere ?

Thanks.

---

### Post by Pumalite on 2008-04-12
I don't know personally, but you could check Launchpad:
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by scottptn on 2008-04-12
Thanks....found something related at[ https://bugs.launchpad.net/ubuntu/+source/linux/+bug/179675]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/179675").
Anyways, will have to try the alternate cd now i think .

Thanks a lot :)

---

