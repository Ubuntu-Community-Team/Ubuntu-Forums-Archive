---
title: "Can't boot live cd"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by headflux on 2008-03-03
Hi

I have strange problem that i hope someone can help with.

I'm running ubuntu 7.10, having first installed from a 7.04 live cd and then upgrading through the package manager.

Recently I decided to try out another distro and opted for Kubuntu.  However, when I try to boot from a live cd, I get the splash screen and the cursor appears, but then the screen just goes black, leaving me having to hard reboot.

I have now tried several different distros including: fedora, opengeu and each time get the same problem.

I'd be very grateful if anyone has any ideas.

Thanks

---

### Post by Scarath on 2008-03-03
You probably have but have you tried hitting Ctrl+Alt+F1 when the screen goes black to get back to a terminal? From there you could try to setup xorg?

---

### Post by headflux on 2008-03-03
Thanks but I've already tried that without any joy.

---

### Post by headflux on 2008-03-04
Ok.

Looking at some other posts on this subject, I tried booting from a Feisty live CD.  This worked and there was a sugestion that a clean install with Ubuntu Feisty 7.04 (given that I also had a dual boot with XP) might pave the way to boot from Kubuntu Hardy 7.10.  

being the adventurous type, I gave it a go but unfortunately, the install failed and kept hanging at 50%.  So at this point I had no system at all.

Fortunately I had a live cd copy of ubuntu dapper 6.06, which i have been able to boot from and install, but now I'm left 2 versions back from where I started.

At this point, I'll just be glad to get back to where I was with Hardy

Any suggestions anyone?

Thanks

---

### Post by MeURi on 2008-03-04
Uhm...

Have you tried a safe graphics boot? I have an nVidia card (6800GT) and a widescreen monitor, and I remember having some problems with the livecd, even specifying resolution and color depth

Maybe it's the same issue. Well, you'll boot into a stretched 640*480 Kubuntu Live, but it works :-) (at least for me)

For the problems during setup (stuck at 50%) I don't know what could be the problem, maybe a corrupted image, but I'm just trying to guess.

Let us know

---

### Post by pcjunkie on 2008-03-04
I can't boot with Nvidia 9600 cards, 8600, 6200 work fine....
Nvidia driver does not recognize the 9600 for some god awful reason so I can't use anything linux on that PC at all....

---

### Post by MeURi on 2008-03-04
AFAIK, booting in safe graphics mode loads only the vga generic driver - thus the 640*480 mode with not-so-many-colors @ some-low-refresh-rate, so any video card should display something (correct me if I am wrong)

If you mean that your boot problems come after Ubuntu setup, it's just a matter of time before nVidia releases drivers supporting your card (latest driver does not support GeForce9 series yet, as you can see from their website, in the [drivers download section](http://www.nvidia.com/Download/index.aspx?lang=en-us))

I hope you can boot into Ubuntu using the *nv* driver, meanwhile (I think no 3D acceleration, though)

---

