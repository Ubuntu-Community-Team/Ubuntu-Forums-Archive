---
title: "fglrx fails to load after 24-20 kernel upgrade?"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by scradock on 2008-07-28
Has anyone else noticed this? I accepted the upgrade to the 2.6.24-20 kernel files this afternoon but found that when I rebooted the display did not have direct rendering enabled (glxinfo). The logs showed that fglrx did not load during start-up of X, so I am using the mesa driver.

The xorg-driver-fglrx is labeled as applicable to 2.6.24.14-20, so it looks as if it is supposed to work with the 2.6.24.20 kernel, but not for me. Any ideas? Shall I file a bug, or is there one already?

Simply reverting to the 2.6.24-19 kernel gives me properly accelerated display with direct rendering.....

---

### Post by Sysmech on 2008-07-28
I have a number of rigs running 8.04 x64.  The 24-20 upgrade has required me to manually set my driver and reinstall with Envy to get back to the previous kernel functionality.  I use the rt version of the kernel and cannot address how the upgrade goes with the generic. 

The 24-20 upgrade is not ready for prime time if it hoses the video driver.

---

### Post by Rocket2DMn on 2008-07-28
Restricted drivers often have to be reinstalled with newer kernels for compatability.  You may need to make sure you have the linux-restricted-modules for the new kernel.  Otherwise if you installed manually or with EnvyNG, you need to uninstall the old ones and reinstall them.

---

### Post by scradock on 2008-07-28
> **Rocket2DMn said:**
> Restricted drivers often have to be reinstalled with newer kernels for compatability.  You may need to make sure you have the linux-restricted-modules for the new kernel.  Otherwise if you installed manually or with EnvyNG, you need to uninstall the old ones and reinstall them.

Good point - but I do have the 2.6.24-20 linux-restricted-modules, so that isn't the problem. There may be a problem in the modules, but they are there.

---

### Post by Rocket2DMn on 2008-07-28
Then I suggest disabling the hardware driver that Ubuntu comes with and install it using EnvyNG - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by scradock on 2008-07-29
> **Rocket2DMn said:**
> Then I suggest disabling the hardware driver that Ubuntu comes with and install it using EnvyNG - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

Yes, I've been all round that route before - could help. But for the moment I think I'll stick with the 24-19 kernel and use the ubuntu-packaged fglrx driver.

What were the promised benefits of the 24-19 to 24-20 kernel upgrade, btw?

---

### Post by Rocket2DMn on 2008-07-29
You'd have to look at the changelog.  Probably nothing major, so I suggest using what works for you!

---

### Post by scradock on 2008-07-31
The problem with fglrx appears at the drmOpenDevice line: the /dev/dri/card0 that is expected is not there. I have checked the /dev/dri address in both 24-29 and 24-20 8.04 - it appears in the first (19) but not in the second. 

Does that ring any bells?

---

### Post by markbuntu on 2008-08-02
The -20 kernel does not know what to do with the fglrx kernel modules so it leaves them out for you to install manually. You can dpkg the modules again or your can just reinstall the driver.

---

### Post by scradock on 2008-08-03
> **markbuntu said:**
> The -20 kernel does not know what to do with the fglrx kernel modules so it leaves them out for you to install manually. You can dpkg the modules again or your can just reinstall the driver.

That's interesting - can you point me to more details? 

I'm very curious as to why after several months (years?) of well-integrated handling of the fglrx driver the integration has been  dropped - or is it only a temporary problem?

****

P S I just checked Jockey (Hardwire Drivers) - it claims that no restricted drivers are in use, which is correct; but it does not list the fglrx driver for me to enable. xorg-driver-fglrx is installed, and its name (2.4.26.14-20.46) implies it should be working with kernel 2.4.26-20.

*****

P P S Reinstalling xorg-driver-fglrx does not change the Jockey situation - still no option to enable it.....

---

### Post by markbuntu on 2008-08-04
I don't know about that, I was using the 8.7 driver from ATI and sort of expected something would happen eventually so I kept the debs around just in case.

You will probably have to remove the fglrx package and reinstall it to fix the problem. The driver is installed, but the kernel modules are not.

Anyway, this did not happen with my amd64 Hardy install, only on i386. Hardy Proposed installed the -20 kernel with no problems at all and updated my fglrx to 8.501 which I believe is the 8.6 driver.

I am running on my new i386 UbuntuStudio install right now so I can't easily access the info on the other installs but when I get back into them I will post back here with more info.

---

### Post by scradock on 2008-08-04
Today's story is that the fglrx module now installs, and I get accelerated video with kernel -20. I don't think there has been a relevant update in the last couple of days, though I know there are some changes in the -20 kernel coming to fix other errors.

NOPE, just checked my term.log - I did re-install both xorg.driver.fglrx and linux-restricted-modules-2.6.26.14-20.46, but both were supposed to be the same versions. And the fglrx module listed by lsmod is the same size as the one I get using kernel -19.

Well, I'll see what happens next time I boot into the -20 kernel. At the moment it's still not very usable, as aMSN isn't able to connect to its server, though Firefox loads web pages OK.....grrr

---

### Post by markbuntu on 2008-08-05
Well yes, that would make sense. All you really did was load the missing fglrx kernel modules that the kernel could not deal with automatically. The fglrx modules did not change, they just did not get installed in the automatic update.

---

