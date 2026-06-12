---
title: "Installation problems with new motherboard"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by gibdogg on 2007-01-29
I've bought an Asus M2N-VM DH motherboard and AMD Athlon 64 X2 dual core processor. Installing has been a complete nightmare. The only thing I can't get working now is the on-board graphics.

(sound and ethernet were also malfunctioning until i put pci cards in for both - really don't want to have to buy a separate graphics card though as it defeats the point of having everything on board and I don't have a spare PCI-E card. The onboard GeForce 6100 is quite adequate for my needs and my small form-factor case is starting to look distinctly crowded.)

I actually installed and got everything working after considerable trouble, but now have reinstalled and can't figure out how to get it working again. Here is the process I followed so far:

- Boot from Edgy x86 CD, on the boot screen I have to change from VGA to 1024x768 or the screen gives me gibberish when X starts
- Installation goes without a hitch, I reboot and once again just get gibberish on the screen (even on console terminal when I press alt-f1)
- So I have to reboot and select recovery mode to get a command line. I install the NVIDIA driver from their website (not from the repositories this doesn't work at all).
- After I've done this all works fine, except when I reboot (choosing normal generic kernel not recovery mode). X fails to start again and I get the X blue-screen-of-death this time not gibberish. If I do alt-f1 now and type startx on the console output I'm told I have API mismatch, NVIDIA kernel module version doesn't match X module version. I now have to reinstall NVIDIA driver  and type startx.

So now everything works except I have to wait for X to fail, reinstall NVIDIA and do startx at every reboot - not exactly ideal.

I remember last time I got it working by uninstalling and reinstalling some of the various NVIDIA packages til I was blue in the face, and it was working with the NVIDIA driver in the repository not the one from the NVIDIA website.

Has anyone else had similar problems and figured this out? Any chance of Ubuntu having better support for on-board motherboard stuff anytime soon??

---

### Post by wpshooter on 2007-01-29
Are you installing this from the DESKTOP (live) CD version or from the ALTERNATE (text) based version ?

If you are installing from the DESKTOP version, I would recommend that you try the ALTERNATE.

---

### Post by gibdogg on 2007-01-29
I'm installing from the desktop CD.
Since the OS is now installed I'm not sure what the advantage of using the alternate CD would be- I suspect I'd have the same problem.
I'm writing this message with a working install of Ubuntu, only when I reboot I'll have to reinstall NVIDIA- should I not be able to get this working without reinstalling the entire system?

---

