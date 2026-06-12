---
title: "problem in ubuntu 11,10 installatin"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by fire planet on 2012-06-02
[SIZE=3][FONT=Calibri]Hi every one,[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]i have a dell xps 1530 with a 64bit capable system,i have a 32 bit window7 on it.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I&#8217;d installed Ubuntu 11.10 successfully several times before. This week I replaced my hard drive,so decided to install Ubuntu again but I&#8217;ve countered a problem during installation.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I want a dual boot of Ubuntu and windows7.so in &#8220;Allocate drive space&#8221; page I chose &#8220;something else&#8221; and then create two partitions(one for ext4 ,another for swap),then I pressed &#8220;install&#8221; button[/FONT][/SIZE]
[SIZE=3][FONT=Calibri],in "install" page a progress bar showed Ubuntu files was copying normally, but nothing happened after progress bar completed(the page was existed even after one hour and no &#8220;restart &#8220;option was shown! )[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]After one hour waiting, I press the power button to force computer be shut down.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]When I pressed power button again, no grub menu appeared and windows logo showed directly! Inside windows7 I checked disk management and it shows two partition of Ubuntu![/FONT][/SIZE]
[SIZE=3][FONT=Calibri]how should I do now?[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I don&#8217;t know what is the problem that it can&#8217;t complete the installation? [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Please help.[/FONT][/SIZE]

---

### Post by fantab on 2012-06-02
TRY AGAIN. 
And remember to install GRUB boot loader on Hdd (/dev/sda) and not on any partitions (/dev/sda2, /dev/sda4, etc).  

Also why not install Ubuntu 12.04 LTS_64bit.

---

### Post by fire planet on 2012-06-03
hi again,
after 3 times trying to install ubuntu ,i found what the problem is!
it seems there is a bug if you using  arowkey of keyboard to choose your desired language!
and the solution : "Don't use keyboard ! just use your mouse to scroll up/down during selecting the keyboard language of ubuntu" :D

the bug had been reported in the below link :
[https://**bugs](https://**bugs)**.launchpad.net/**bugs**/[B]645449


[/B]

---

