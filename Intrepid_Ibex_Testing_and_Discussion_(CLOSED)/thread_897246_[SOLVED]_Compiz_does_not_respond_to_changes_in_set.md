---
title: "[SOLVED] Compiz does not respond to changes in settings"
date: 2008-08-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by milky2313 on 2008-08-21
Hello all...

I am currently working with Intrepid Alpha 4 on a Dell Latitude D610 with an ATI Mobility Radeon X300 video card.  I am using the open source ATI drivers.  I know that these drivers have been blacklisted under compiz, but with Hardy I was able to enable compiz with SKIP_CHECKS=yes, and compiz worked with no problems.  With Intrepid Alpha 2, I used this same method to enable compiz and it worked great as well.  However, this is not the case with Alpha 4.  I can enable compiz, but I only get the 'normal' desktop effects.  If I change to 'extra' effects, nothing happens at all. Compiz continues to run, but only with the 'normal' effects enabled.  I also installed CompizConfig settings manager and tried change the settings that way, but compiz still does not listen to me. I cannot even change my desktop size.  

Perhaps this is just a temporary problem since Intrepid is still in development stages. I hope that this does not stick around to the final release of Intrepid, but I don't think I should report a bug since compiz is officially not supposed to work with my graphics card anyway.

I am just wondering if anyone has a workaround or any more info about this...

Thanks for your help...

---

### Post by rgabi88 on 2008-08-24
I have the same problem.
Nvidia Gforce 3 Ti200 :)
I had some problem with drivers, but now it works, except Compiz...
Ah... Ubuntu 8.04=>Linux Mint=>Intreprid...:lolflag:

---

### Post by readams on 2008-08-28
Same here; can't change any compiz setting.  I've tried deleting all compiz settings including running gconftool-2 --recursive-unset /apps/compiz but changing any setting related to compiz has no effect.

Metacity works fine.

---

### Post by milky2313 on 2008-09-09
I found a solution by looking around at some similar problems on the forums. Try this out, it worked for me:

Check your **~/.config** directory, it should contain a directory named either **compiz** or **compizconfig**. For me this folder was owned by root and I could not make any changes to it(I think that is what was causing the problem).  Anyway delete the compiz or compizconfig folder. If it is owned by root, you will have to use the command line and sudo to do it:
```
sudo rm -R ~/.config/compizconfig
```
or
```
sudo rm -R ~/.config/compiz
```

After that open ccsm and go to preferences. Make sure that it is set to **flat-file backend**. After that try to set all the settings that you want. Everything worked correctly for me at this point.

Hope this helps!!

---

