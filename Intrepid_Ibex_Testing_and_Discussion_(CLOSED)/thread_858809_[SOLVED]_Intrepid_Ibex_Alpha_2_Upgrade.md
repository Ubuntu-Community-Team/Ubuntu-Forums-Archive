---
title: "[SOLVED] Intrepid Ibex Alpha 2 Upgrade"
date: 2008-07-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by VexVishnu on 2008-07-13
If I upgrade to Intrepid Ibex Alpha 2 (the second alpha release of Ubuntu 8.10) does it change the kernel as well, or would I need to download the Alpha 2 ISO and burn/install to get the new kernel?

[http://www.ubuntu.com/testing/intrepid/alpha2](http://www.ubuntu.com/testing/intrepid/alpha2)

The reason I want to know is because when I reported my "no sound" bug on Launchpad they suggested I upgrade to Alpha 2 via a livecd, but I have nothing to burn it to. I also want to know how much of a difference does it make, if any, to upgrade with or without the cd?

Thanks in advance.

---

### Post by nowshining on 2008-07-13
prob. little diff. to upgarde via synaptic, etc.. & it should download a newer kenel, once u update - reboot.

---

### Post by VexVishnu on 2008-07-13
Cool, because I think the newer kernel was the major concern here anyway. Thanks for the quick response!

---

### Post by LeoSolaris on 2008-07-13
Maybe this is still a little ignorant of how Linux works, but would you be able to upgrade the 8.04 with a newer kernel from somewhere other than the repositories, for instance from Linux from Scratch?

Or do too many things need an exact kernel, or need to be reconfigured by the specific .debs in the repos?

Leo

---

### Post by nowshining on 2008-07-14
> Maybe this is still a little ignorant of how Linux works, but would you be able to upgrade the 8.04 with a newer kernel from somewhere other than the repositories, for instance from Linux from Scratch?

Or do too many things need an exact kernel, or need to be reconfigured by the specific .debs in the repos?


More than likely - it should be fine. I personally run 2.6.24.7 on my box. :) it was on Gutsy, but then I re-installed but this time with Hardy and it works fine. I use the vanilla kernel from kernel.org with patches from grsecurity.

If you have trouble with the 2.6.25.xx kernels - just use the 2.6.24.7 kernel.

Alas don't forget - u need to put the kernel source untouched from ur last compile into the /usr/src/ folder, and re-install your video drivers, esp. if u use nvidia and or ati.

Once done, make a backup of the kernel src that is un-altered along with the deb files or else you won't be able to re-install ur Graphic Drivers in the future. :)

---

