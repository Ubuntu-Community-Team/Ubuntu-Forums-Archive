---
title: "Multible 10.04 Problems"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by bingobingo on 2010-06-20
I had upgraded to 10.04 but can not use kernel 2.6.32-22.32+, I had to go back to kernel 2.6.31-21. because of the default video driver had change from the one kernel to the other, and I do not know how the correct it. In 2.6.32-22 the font would change and to a smaller size and I can barely view anything because it looks like some two year old puke a box of crayons all over the screen.

Second issue is it does not matter what power-saving mode I am in, in 5 minutes time it with go into suspension. Or right after coming out of hibernate, it will go into suspension indefinitely and no coming out of it and must to a hard boot.:confused:

---

### Post by quixote on 2010-06-22
If you have ATI graphics, I think it's best to know the exact model to get the right driver.  Open a terminal (Applications > Accessories > Terminal) and type ```
lspci | grep 'VGA'
``` (that's case sensitive.)

As far as I know, fglrx is the driver used for ATI, generally.  Do you have that installed or are you using another driver?  If so, which?  (I'm sure there are better ways to do it, but I just open synaptic and search for ATI.  fglrx will be one of the packages that comes up.  If it's installed, you can see that there.)

What's causing your suspend problem, I'm not sure.  That's really a separate issue, so I'd suggest starting a new thread for that in any case.

---

### Post by bingobingo on 2010-06-23
After typing in the code, I get

00:09.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

But why did the driver change during the upgrade? That is one thing it should never have been touched.

And no fglrx is not installed, when searching radeon, while using the kernel 2.6.31.21, I get and have installed...

libdrm-radeon1
xserver-xorg-video-ati
xserver-xorg-video-radeon

---

### Post by quixote on 2010-06-23
Well, some searching on that specific model suggests we're pulling at what looked like one little thread which leads to a big mess!  Seems there's a [hardware bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565607") causing the issue, and it also seems I was wrong about the suspend issue.  It's all related. The graphics problem makes the computer lose its tiny mind.  

The reason there's a problem now but there wasn't before is that the software (ie linux kernel etc) changes so it may need drivers to be updated, which then can cause things to be more sensitive -- or less -- to some fault, and so on.  :(

On the [X quirks page]("https://wiki.ubuntu.com/X/Quirks") in the Ubuntu wiki, they list some workarounds.  I don't understand half of what they're talking about myself, so I may be wrong here, but the impression I get is that the easiest thing to try would be to install the fglrx driver.  You can do that in synaptic, and say to install any dependencies it might want too.

Restart X by logging out and back in again, or rebooting.  If the problem is gone, we celebrate.  If not, the next step is to edit the file /etc/X11/xorg.conf. (Easy, just a bit tedious.)  I believe 10.04 doesn't have xorg.conf by default, so see if the simple method is enough first.  If not, then we'll do the xorg edits.

---

### Post by bingobingo on 2010-06-23
Thanks, I never heard of fglrx before this, I installed it and it's ds while barely able to read anything with kernel 2.6.32.22 and rebooted. Another shine day with Ubuntu.:popcorn:

---

### Post by quixote on 2010-06-24
Did you get all that popcorn finished before it would boot?  Or did it actually work? :biggrin:

---

### Post by makindue on 2010-06-28
> **bingobingo said:**
> I had upgraded to 10.04 but can not use kernel 2.6.32-22.32+, I had to go back to kernel 2.6.31-21. because of the default video driver had change from the one kernel to the other, and I do not know how the correct it. In 2.6.32-22 the font would change and to a smaller size and I can barely view anything because it looks like some two year old puke a box of crayons all over the screen.

Second issue is it does not matter what power-saving mode I am in, in 5 minutes time it with go into suspension. Or right after coming out of hibernate, it will go into suspension indefinitely and no coming out of it and must to a hard boot.:confused:

Nice. I think that problem was already solved. We have the same problem and I solve it because of this thread. I think now I can use the kernel 2.6.32-22.32+. :D

---

