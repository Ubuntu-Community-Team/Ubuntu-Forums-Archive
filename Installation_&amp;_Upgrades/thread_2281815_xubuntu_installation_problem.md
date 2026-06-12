---
title: "xubuntu installation problem"
date: 2015-06-09
forum: Installation &amp; Upgrades
---

### Post by Gokturk_Demir on 2015-06-09
Hello,

I am trying to install Xubuntu on a very old Sony Vaio Laptop. The proplem is,  installation always crashes before it is completed. I suspect the graphics card is causing the problem (Nvidia Go 6400) as some distorted graphics appear during the installation and the laptop either freezes or shuts down .When I try "Try xubuntu before installation" option , there doesn't seem to be any problems.
Now I am wondering, is there such an option to install xubuntu without graphics card support/drivers as in the safe mode boot?so I can try to install /update proper drives after the installation?

Thanks..

---

### Post by kc1di on 2015-06-10
Hello Gokturk_Demir and Welcome to Ubuntu,

You need to use the Nomodeset parameter at boot time. 
You can find it by Hiting the tab key just as Ubuntu live begins to boot.  You should then see some F-key options at the bottom of the page.
select F6 and then select nomodeset hit Esc and enter, when it boots up the graphic will not be right but go ahead and install it.
on the first boot select the nomodeset again and when you get to the desktop Go to system settings and additional drivers install the recommended driver for your video card.
and then all should work ok. 
good luck.

---

### Post by Gokturk_Demir on 2015-06-10
Thanks a lot kc1di,
I will try this.[COLOR=#000000] [/COLOR]

---

