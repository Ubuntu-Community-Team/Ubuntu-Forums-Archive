---
title: "Sony Vaio VPC-F13Z1E/B issues"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by elvisd on 2010-12-10
Hi all,

I'm trying to install ubuntu 10.10 on the notebook (Sony Vaio VPC-F13Z1E/Z).
I start from the live CD and the session starts, with a low resolution but starts.
i install ubuntu (selecting update from web during installation) and after a while everything's done. restart.

the PC boots (with a ugly startup graphic) but instead of the graphical login the console mode is displayed.

how can i solve that. 
I had the same (unresolved-) problem 2 weeks ago with a toshiba lappie. hope i can solve both. ;)

Thanks for your help,

elvisd

---

### Post by Quackers on 2010-12-10
What does the screen say exactly?

---

### Post by elvisd on 2010-12-10
I can enter user and password and login in console mode... like switch to another console with, i.e. ctrl+alt+F2...

no error messages (apparently)

---

### Post by Quackers on 2010-12-10
After logging in type startx and hit enter. See if the desktop appears.

---

### Post by elvisd on 2010-12-10
Gave me:
(...)
(EE) Failed to load module nvidia (module does not exist, 0)
(EE) No drivers available.
Fatal Server error: 
no screens found
(...)

I have edited xorg.conf changing nvidia to vesa and now the graphical desktop is here.
What's next?

---

### Post by Quackers on 2010-12-10
Have you run Additional drivers from the System > Admin menu?

---

### Post by elvisd on 2010-12-10
I have installed nvidia binary drivers (and updated the whole system).
I have restarted and the screen remains purple.

I have started in safe graphic mode, run nvidia-xconfig and restarted but nothing changed, remains purple.

---

### Post by Quackers on 2010-12-10
"I have installed nvidia binary drivers"

where from please?

---

### Post by elvisd on 2010-12-10
from system > admin > additional driver, the recommended version.

---

### Post by Quackers on 2010-12-10
Thanks.
I'm not clear on which screen you are at.
You say it's purple. The default desktop is purple.
Does it say Ubuntu in the middle with white/red dots underneath?
Are there dark brown borders top and bottom?

---

### Post by elvisd on 2010-12-10
thank you for you simple questions.
even if i'm not a newbie it's always better to control twice and even simple things. ;)

during boot i have the purple screen with ubuntu and dots below.

after a while the ubuntu word and dots are removed but the purple background remains (no login request as configured) and thats not the desktop (no wallpaper no panels).
no mouse pointer, i can't even do a ctrl+alt+F2 to change to console mode.
no disk activity, already waited 4-5 minutes but nothing happens.

thank you for patience

---

### Post by Quackers on 2010-12-10
If you hold down the shift key while booting does a black screen with white writing appear?

---

### Post by elvisd on 2010-12-10
what do you mean? at grub loading or OS loading?

---

### Post by Quackers on 2010-12-10
I mean on a cold boot. From off to on hold the shift key down and the grub menu should then appear

---

### Post by elvisd on 2010-12-10
yes i can access the grub menu.

---

### Post by Quackers on 2010-12-10
From the grub menu your Ubuntu installation should be highlighted. If you press the "e" key you should get another screen up. In that screen navigate to the end of the line that says "quiet splash" Remove those words and replace them with "nomodeset" without the quotes, then press ctrl + x to reboot. Does the desktop appear then?

---

### Post by elvisd on 2010-12-10
no... the last message i see is 'checking battery status' then the screen goes black and nothing happens.

everything goes so fast but i don't see any error messages

---

### Post by Quackers on 2010-12-10
Which graphics card do you have in your machine?

---

### Post by elvisd on 2010-12-10
NVIDIA® GeForce® GT 425M GPU

if i remove nvidia driver then starts ok (but with very low resolution) i think is a nvidia related problem.
how about loading the latest nvidia driver?

---

### Post by Quackers on 2010-12-10
Some people visit the nvidia site and use drivers from there. However, it is normally enough to use the one from Additional Drivers, in my experience.
It may be worth a try, but that has to be your own decision :-)

---

### Post by elvisd on 2010-12-10
found this [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/655078](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/655078)
and as stated at #66 i have downgraded to 256.53 and seams working. the fan works to much for my taste... anyway better as working at 800x600

thanks Quackers for support

---

### Post by Quackers on 2010-12-10
No problem at all.
I hope all your problems are short-lived :-)

---

### Post by elvisd on 2010-12-15
Just as follow up:
I've downloaded today's new nvidia driver (260.19.29)and installed it manually and works like a charm.
what i should do is fix non working brightness buttons... but that's not priority for now... ;)

---

### Post by Quackers on 2010-12-15
Nice one :-)
The brightness keys may be a problem. Mine don't work at all.
However if you do a search in Hardware and Laptops section there have been some fixes which have worked for some people.

---

### Post by stevekh3 on 2010-12-17
> **elvisd said:**
> Just as follow up:
I've downloaded today's new nvidia driver (260.19.29)and installed it manually and works like a charm.
what i should do is fix non working brightness buttons... but that's not priority for now... ;)

I have the same notebook, i had the same problems you had, resolved with the 260.19.29, i'm also in the same your condition with the brightness problem.

Also touchpad was not working: solved with this [http://ubuntuforums.org/showthread.php?t=1565548&highlight=vaio+touch+pad](http://ubuntuforums.org/showthread.php?t=1565548&highlight=vaio+touch+pad) :)

---

### Post by zlatan87 on 2011-02-15
Hi! I've Sony Notebook F13Z1E and I've same problem, i've installed Ubuntu on my Laptop and all works Ok except Graphics Card, resolution is only 800x600 and when I try to update graphics drivers the OS not start and it stay on Purple screen blocked, why?? What is correct procedure to make working nvidia drivers??

Help me please!

---

### Post by elvisd on 2011-02-15
You should download and install latest nvidia drivers.
i actually have version  260.19.36 and install it manually.

but before, for the purple screen problem, restart in safe mode and remove nvidia drivers.

hope this helps.

---

### Post by zlatan87 on 2011-02-15
> **elvisd said:**
> You should download and install latest nvidia drivers.
i actually have version  260.19.36 and install it manually.

but before, for the purple screen problem, restart in safe mode and remove nvidia drivers.

hope this helps.

Ok thanks man, i've installed it today from terminal and next i've typed nvidia-xconfig, but unsuccessfully...can you help me to make a new clean driver installation?? I'm newbie for linux using and I don't say if my manually installation was correct!

Ps: if exist a guide that explan right steps to install drivers...

---

### Post by elvisd on 2011-02-17
Hi Zlatan.

On this thread [http://ubuntuforums.org/showthread.php?t=1598417](http://ubuntuforums.org/showthread.php?t=1598417)
I found a link to this tutorial [http://www.gaanza.com/blog/installing-nvidia-driver-on-ubuntu-10-04/](http://www.gaanza.com/blog/installing-nvidia-driver-on-ubuntu-10-04/)

Hope this helps

---

