---
title: "After Upgrade to Hardy Ubuntu does not boot"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by zilenCe on 2008-06-16
Hello,

I just upgraded gutsy to hardy and after it said that I need to restart my computer the whole thing hang up. I just saw the bouncing loading bar on splash screen. When booting in recovery mode it just stopped somewhere.

I then tried to boot with kernel 2.6.22 from gutsy which did only work in recovery mode. After reading through some stuff I found some initramfs stuff which my caused the error. I then did some initramfs update thingy and installed live-initramfs or so as recommended on that launchpad bug report. I guess that was not the problem.

Now no kernel boots any longer. In recovery mode it stops right after initializing the devices, I guess. I just see some scsi stuff with my external hdd and then it stops. Also, when I plugin my external hdd while booting I see that it loads the stuff, but still hangs after. It doesn't give me any errors. There are no problems with my external stuff since everything worked before on ubuntu and works still on windows.

Is there anything I can do, to fix that? Really want to use Ubuntu again!

Thanks in advance.

Cheers

---

### Post by hal8000 on 2008-06-16
Upgrades are never straightforward and take 3 times as long.
Its always better to back up your original data and install fresh.

If you backed up your original data, easiest is to rerun the cd and wipe the ubuntu partition(s) and install again.

Make sure that the Hardy Cd does run in live mode before you attempt a fresh install.

---

### Post by zilenCe on 2008-06-17
is there anything else I can do, to fix it? I don't want to reinstall windows and ubuntu at the moment :(

---

### Post by BCRailrodder on 2008-06-17
> **zilenCe said:**
> is there anything else I can do, to fix it? I don't want to reinstall windows and ubuntu at the moment :(

This sounds like a problem I was having with my laptop (HP DV9000).

I ended up manually editing grub on each bootup and taking out the quiet line as well as editing the second line and removing the quiet and splash out of it.

Do a bit of experimentation to see what may work for you.

As well, for MY laptop, I had to add noapic.  Never did figure out why but it works fine with 8.04 so I'm not worried <G>.

Good luck.

---

