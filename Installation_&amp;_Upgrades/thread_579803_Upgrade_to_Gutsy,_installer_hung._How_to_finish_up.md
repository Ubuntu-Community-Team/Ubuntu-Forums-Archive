---
title: "Upgrade to Gutsy, installer hung. How to finish up?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by gspr on 2007-10-18
Hi. 

My upgrade from Feisty to Gutsy went fine up until the last parts of the "clean up" step. The update manager began removing obsoleted packages as it was supposed to, before it all of a sudden started to gobble up more than 90% memory, and then reported "update manager crashing" before all of X hung (I'm guessing X got terminated because the system ran out of memory?) and I had to reboot. Since the upgrade was almost complete, the system came up just fine, and Gutsy seems to be working fine. Adept, does, however, still insist that a new version of Ubuntu is available. Clicking version upgrade tells me I'm already at the latest version and that no upgrade is possible.

What do I do to resolve this? Or in general: What does one do when the upgrade hangs for some reason? How do pick up the pieces in the correct manner?

---

### Post by gspr on 2007-10-18
Addendum: Installing any new packages now gives me: "Processing triggers for libc6... ldconfig deferred processing now taking place". That can't be right, or what?

---

### Post by cazzerson on 2007-10-19
I can confirm this problem...although my machine hasn't crashed yet, I do seem to be hung (for several hours) at this point in the upgrade...

---

### Post by cazzerson on 2007-10-19
In an attempt to copy and paste my current status, I realized that hitting ctrl-c keeps the installed moving through all of the "preparing to configure X" messages. I have to do this every 30 seconds or so, and I'm worried that I'm ending up with a completely broken upgrade...

---

### Post by Dark Aspect on 2007-10-19
> **cazzerson said:**
> In an attempt to copy and paste my current status, I realized that hitting ctrl-c keeps the installed moving through all of the "preparing to configure X" messages. I have to do this every 30 seconds or so, and I'm worried that I'm ending up with a completely broken upgrade...

I did actually..........

I am going to try the alternate CD next time.Its no big deal for me since I only had about 7 GB on the hard drive anyway.I had just reinstalled 7.04 about 3 weeks ago to change to 64-bit code.

I don't think I am going to try the network install again.

---

### Post by BrumleyGap on 2007-10-20
I also had the upgrade hang at the clean up stage. So how does one make sure all is well at this point? Do I need to go ahead and get the DVD and do a clean install?

---

### Post by Smeagle on 2007-10-25
Hi,

When I tried to upgrade to Gutsy from Fiesty, my installer also hung, but mine didn't get as far as yours did, it only got up to setting xserver-xorg when it hung. Before this point it had been complaining a bit about not being able to set up programs, mostly emacs. So I held the power key down for 8 seconds to shut the computer off and turned it back on again, and it booted into GRUB as usual as I am dual-booting this machine with Windows XP, and it gave me the choices of either booting Ubuntu 7.10 using (the new) kernel 2.6.22-14-generic in either normal or recovery mode, kernel 2.6.20-16-generic in either normal or recovery mode (which is the one I used to use), or kernel 2.6.20-15-generic in normal or recovery mode, or Windows XP. Booting using kernel 2.6.22-14 in either normal or recovery mode results in the error message Kernel panic - not syncing: VFS: Unable to mount root fs on unknown - block(0,0), but luckily kernel 2.6.20-16 still boots normally with the only new error message being under manual drivers: kernel.maps_protect unknown key, and so far I've only noticed that I can no longer mount my thumb drive.

I attempted the upgrade using Fiesty's Update Manager.

Would that fact that I have a 1 gig and a 256MB chips of RAM plugged in having anything to do with my laptop hanging?

Any suggestions as to how I complete my upgrade to Gutsy?

---

