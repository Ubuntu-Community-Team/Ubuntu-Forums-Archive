---
title: "cannot boot past splash screen after 16.04 to 18.04 upgrade"
date: 2018-05-16
forum: Installation &amp; Upgrades
---

### Post by mfox on 2018-05-16
Following an upgrade to 18.04, a reboot gets me past the Ubuntu splash screen but not to login screen. I believe I know what the problem is, but not how to fix it. In Ubuntu 16.04 I had the proprietary amdgpu-pro driver installed. I forgot to remove it after the upgrade, and I believe it isn't compatible with Ubuntu 18.04. I tried booting into repair mode, got to a terminal, and was able to uninstall the proprietary driver with the amdgpu-pro-uninstall command. But that didn't solve the problem, as when I boot I can get past the Ubuntu splash screen, but not to a login screen. What I see are vertical color bands. These come on go away and come on repeatedly, but I never get past that.

I think that I have to reinstall the open source amd driver, but I don't know how to do this on a non-booting partition. Is there a way I can do it in repair mode or from a live usb? Other suggestions?

---

### Post by dino99 on 2018-05-16
From a tty console you should be able to check that: dkms, build-essential, kernel headers are well installed; and also checking 'journalct -b' for errors  :P

---

### Post by mfox on 2018-05-17
Thanks for the reply dino99. When I get to the terminal, how do I check that those packages are installed, and how do I check 'journalct-b' for errors? I also wonder if it has anything to do with graphics-related packages that were removed when I uninstalled the amdgpu-pro driver. I saw things like mesa removed, though it might have been a version specific to that driver.

---

