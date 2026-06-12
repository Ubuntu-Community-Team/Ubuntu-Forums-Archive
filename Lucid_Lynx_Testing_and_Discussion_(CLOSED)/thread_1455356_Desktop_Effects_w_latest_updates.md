---
title: "Desktop Effects w/ latest updates"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jeggen on 2010-04-15
I lost all desktop effects with the latest updates.  (Yesterday)  I have tried using both the Nouveau driver and the proprietary Nvidia driver and have had no luck with either.  I am using a NVIDIA Quadro FX 570M graphics card on a HP 8510w.

I am using the xorg-edgers/ppa PPA and wonder if it is related to recent updates from this.

---

### Post by dalonso on 2010-04-15
Same thing here.

I believe it's related to the fact that last updates brought kernel 2.6.32-21, but there's no linux-backports-nouveau for this kernel version. The last one is for 2.6.32-20.

I suppose the updated package will be coming eventually.

I hope ...

---

### Post by cariboo on 2010-04-15
Have you tried running **sudo nvidia-xconfig** in a terminal, then reboot?

---

### Post by jeggen on 2010-04-24
Anyone else still having this issue?  The only way I get my desktop effects is with the Nvidia driver, but I prefer to use the nouveau driver so I get brightness control.

nvidea-xconfig only works when using the nvidia driver.  I have selected the nouveau driver using the technique selected here:
[http://ubuntuforums.org/showthread.php?t=1423210](http://ubuntuforums.org/showthread.php?t=1423210)

I'm not sure what else to do, but find it unlikely that the nouveau driver wouldn't work with the RC stage.

---

### Post by jeggen on 2010-04-25
I am still looking for some help on this.  Over the weekend I updated and now I can't boot with the Nvidia drivers... my system becomes unresponsive during the display of plymouth boot splash.  So I either have Nouveau with no effects (and terrible performance) or Nvidia and a big paperweight.  I can still boot into the old kernel though, which is a workaround for now.  Since I don't see anyone else chiming in on this it makes me wonder if I just have a silly configuration error or if there are just limited people using 10.04 with this chipset.

---

### Post by Sarvatt on 2010-04-25
If you are going to use xorg-edgers, please at least try to read the PPA page when you have problems. All of your issues are explained along with how to fix them..

[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

As I have said on there, linux-backports-modules is no longer supported because upstream nouveau on was rebased against 2.6.34 and required touching way too many other components to continue. You need to use a 2.6.34+ based kernel to use the userspace components from xorg-edgers with nouveau, I put the 10.10 kernel as it is now in there and there are also the mainline kernels to use. You may think it is annoying to do that way, but you already cannot use a 2.6.34 kernel with the lucid nouveau userspace components, they broke compatibility upstream.

---

### Post by jeggen on 2010-04-25
Thanks for the pointer.  I forgot to check back in there.

I disabled xorg-edgers (using "sudo ppa-purge xorg-edgers") and then running an update to ensure I have the latest.  I still am unable to enable desktop effects with the latest updates.

Let me clarify, I can get effects with the proprietary Nvidia driver... just not with Nouveau.  W/ proprietary driver though I loose all of the built-in brightness control, so am hopping to switch back to Nouveau at some point.

---

