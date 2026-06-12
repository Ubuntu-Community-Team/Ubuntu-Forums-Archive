---
title: "Geforce 7900GS whole cataloge of problems"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Archaon on 2008-07-07
Hi,

After the 8th install of Ubuntu on my desktop after playing around with my graphics drivers to the extent of having to reinstall, ive decided to come begging for help:

Upon a fresh install I have one monitor running at a decent resolution (~1280 or so, i didnt check) with my second monitor "out of range")  For the sake of this article I will consider the other monitor unplugged, as it is currently not the issue.

Current issues:

When I install the drivers, either from the NVidia site, or the repository, after restarting X server I get the "running in low graphics mode" popup, and nothing i do in there satisfys it or will save.  Upon logging into to ubuntu (8.04 btw) I can see the Nvidia control pannel, but when I click it, it says you are not running X, run Nvidia-xconfig and restart X.  Which I did, many many times.  At no point during any isntallation do I get the Nvidia flash as X loads (as I get on my laptop also).  The maximum resolution availible is 800X600.

I have looked in the xconf file, and nothing there seems vastly different to the setup in my laptop (which also runs Nvidia, just a different graphics card)

I have looked on the net at a vast number of tutorials, and cannot seem to find a solution to this, as all seem to come to the conclusion once you have installed libc and subsequently the drivers, assuming you dont have two different kinds installed, you are sorted and should get the Nvidia flash, and the Nvidia X loading, which it isnt for me.

Any help would be greatly appreciated.

Regards,

Arch

---

### Post by Archaon on 2008-07-07
Also tried using EnvyNG and the same problems occured, kinda implying that there isnt a great deal wrong with the driver install itself.

Also interestingly it randomly booted in high resolution mode once, but apparently this wasnt Nvidia drivers doing it as when I tried to look at the Nvidia config it still claimed I wasnt running them and should activate them.

Upon trying something in cntrl alt F2, after stopping X, i tried starting using the "startX" command rather than /etc/init.d/gdm start and got the following error message:

"Your geforce 7900 gs graphics card does not have the necessary exernal power cables attached.  X will not start unless this is rectified....please retart computer etc etc.  If you feel you got this message in error please add "NoPowerConnectorCheck" in screen section of xconf.

I also got an fatal server error, no screens found.

Adding NoPowerConnectorCheck as it is in the xconf file seems to make no difference. 

Arch

---

