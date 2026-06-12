---
title: "Install ATI Catalyst Control centre"
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by refle on 2013-08-04
Hi,
im using ubuntu 12.04 64bit, ATI RAdeon HD 5400
I installed the proprietary graphics driver as described here: [http://www2.ati.com/relnotes/catalyst_linux_installer.pdf](http://www2.ati.com/relnotes/catalyst_linux_installer.pdf)
I used the "Generate Distribution Specific Driver Package Option" way.

Now 2 questions:
1. how can i check if everything is installed properly?

2. i dont have the CATALYST CONTROL centre installed. how can i install it although i want to use the "Generate Distribution Specific Driver Package Option"  method?

THANK YOU!

---

### Post by Claus7 on 2013-08-04
Hello,

open a terminal and type the commands (one by one):

fglrxinfo
fgl_glxgears

if they work, then you have installed the driver in your computer. 

I can find catalyst control center under: system->preferences (this for gnome 2 using maverick though...).

If the aforementioned commands do not work then try this from here:
[http://ubuntuforums.org/showthread.php?t=1419962&page=3&p=11320620#post11320620](http://ubuntuforums.org/showthread.php?t=1419962&page=3&p=11320620#post11320620)
(using a similar card than the one you are using)
In every (re)-installation do not forget to purge the previous one, because it is going to cause conflicts with the new one.

Hope it helps,
Regards!

---

