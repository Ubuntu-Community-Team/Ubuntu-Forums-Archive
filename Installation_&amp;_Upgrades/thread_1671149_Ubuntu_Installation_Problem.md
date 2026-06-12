---
title: "Ubuntu Installation Problem"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by XJLanzaro on 2011-01-19
I've installed Ubuntu Desktop Edition using Wubi on Windows XP, but whenever I select Ubuntu it the boot menu it won't boot. It shows the Ubuntu loading page but after that the screen goes black. I've waited hours and it won't get past that black screen. Does anyone know how I can fix this?

---

### Post by XJLanzaro on 2011-01-19
Someone please help me.

---

### Post by bcbc on 2011-01-19
Please boot into Windows and run chkdsk:
Go to my computer, right click on C:, Properties, Tools, Check disk for errors, Fix automatically. Reboot to complete. When it finishes, attempt to boot into Ubuntu.

If this doesn't work I have a more involved fix, but try the above first.

EDIT:
Sorry, just to confirm... did you ever get Ubuntu to boot successfully or does did it always hang like that? What computer brand/model and graphics card do you have?

Also, if you booted Ubuntu before, did you update grub?

---

### Post by XJLanzaro on 2011-01-20
Thank you, I will try that. I was never able to successfully boot Ubuntu. My computer is a Panasonic Toughbook CF-18 notebook with a Intel GME 64MB graphics controller.

---

### Post by bcbc on 2011-01-20
[https://wiki.ubuntu.com/CF-18](https://wiki.ubuntu.com/CF-18)> Which Version to Install?
There is a graphics driver problem that was introduced between versions 9.04 and 10.04 where Ubuntu boots to a blank screen. To work around this problem you must pass a special parameter to the kernel using F6 as described in this forum post. Unfortunately, the workaround seems to result in extremely slow graphics performance. Apparently this might be fixed by 10.10. In the meantime, 9.04, possibly 9.10 seems to be the latest, working version of Ubuntu on the CF-18.

[http://ubuntuforums.org/showthread.php?p=9940776#post9940776](http://ubuntuforums.org/showthread.php?p=9940776#post9940776)
> Quote:
Originally Posted by sotirovlyu  
I solved the issue, it is realated to Intel 855GM chipset video driver. One has to use 
Code:
i915.modeset=1
kernel boot parameter to resolve the issue (a workaround though.. ).
I confirm this works with the netbook LiveCD on my CF-18:
1. Boot LiveCD.
2. Press F6 when you see the two little icons at the bottom of the screen. This'll bring you to the good old Boot Options screen.
3. Press F6 again to add i915.modeset=1 to the Boot Option Configuration Line a la [https://help.ubuntu.com/community/Li...uration%20Line](https://help.ubuntu.com/community/Li...uration%20Line).
4. Boot. Video should now work.


Tutorial on overriding startup options: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
To override startup options during the initial Wubi install: [http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by XJLanzaro on 2011-01-21
Thanks for the info.

---

