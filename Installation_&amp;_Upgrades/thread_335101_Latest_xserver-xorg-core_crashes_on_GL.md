---
title: "Latest xserver-xorg-core crashes on GL"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by Basho on 2007-01-09
Bit of a newbie here ... please help me.

Running Edgy with Nvidia's 9631 drivers (latest available for my card, as far as I can tell). Everything was working just fine. However, I just did a "Full Upgrade" in Adept and got a new xserver-xorg-core. Now, anything GL (glxgears, Beryl, etc.) causes X to crash to a black screen and then to my login screen.

How can I roll back to the previous package? Or, anywhere I can look to diagnose and perhaps fix this problem with this newest xserver-xorg-core package?

Thanks ...

---

### Post by scrooge_74 on 2007-01-09
any time you upgrade you have to reinstall the drivers, follow this advice

[http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

---

### Post by Basho on 2007-01-09
Thanks! That worked!

---

### Post by rev_b on 2007-01-09
After installing some software updates prompted today by update manager, I found myself presented with a X error on reboot. I remember Xorg was one of them.

I could fix it reinstalling Nvidia 9746 binary drivers from the command line, but should this happen? I mean a simple software update from the repositories rendering the system unusable?

---

### Post by scrooge_74 on 2007-01-09
That is what the instructions say it will happen, I suppose since the drivers are not part of the packages the xserver tries to go back to an original state and crashes

---

### Post by Daggan on 2007-01-10
Thank you!  Problem solved!

I had exactly the same problem with Mythtv after the update.. ](*,) 

Daggan

---

### Post by farstrider on 2007-01-10
> **scrooge_74 said:**
> any time you upgrade you have to reinstall the drivers, follow this advice

[http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)


I do not understand, I followed the link and ..............?? Help!

---

### Post by arnieboy on 2007-01-10
[http://ubuntuforums.org/showpost.php?p=1993792&postcount=8](http://ubuntuforums.org/showpost.php?p=1993792&postcount=8)

---

### Post by farstrider on 2007-01-10
Thanks arnieboy I will try but I am sure I will bugger something up! Anyway will give it a go! Thanks again!

---

### Post by penvzila on 2007-01-11
> **rev_b said:**
> After installing some software updates prompted today by update manager, I found myself presented with a X error on reboot. I remember Xorg was one of them.

I could fix it reinstalling Nvidia 9746 binary drivers from the command line, but should this happen? I mean a simple software update from the repositories rendering the system unusable?

No, but that's the way it goes.  It's one of the reasons why Linux will never be a widespread desktop OS.

---

### Post by scrooge_74 on 2007-01-11
> **penvzila said:**
> No, but that's the way it goes.  It's one of the reasons why Linux will never be a widespread desktop OS.


That is not really a reason because 10 years ago you had similar weird problems using Win 95.  If the drivers where included in the distribution there would not be this kind of trouble.

---

### Post by penvzila on 2007-01-11
Downloading the driver installation script from NVIDIA worked, but it broke beryl (the classic disappearing window borders.)  I decided I can live fine without beryl, since I had to close it to use Ogle anyway.  Most other OpenGL apps work though.

By the way, people keep mentioning the 9746 drivers, but if you have an older card, you actually need the 9831 drivers (for example, my Ti4200.)

[http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html)

---

### Post by scrooge_74 on 2007-01-11
I had to use legacy drivers myself

---

### Post by ChrisNiemy on 2007-01-22
Hi,

thanks for this thread. Reinstalling the driver from the website worked for me, too.

I guess, a xorg-update seems to override some GL-files (Nvidia OpenGL headers).

Mhm, still waiting that Intel will produce PCI/AGP cards... ;)

---

