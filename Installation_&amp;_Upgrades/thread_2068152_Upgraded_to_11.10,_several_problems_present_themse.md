---
title: "Upgraded to 11.10, several problems present themselves"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by abelundercity on 2012-10-08
Seeing the support period about to end for 11.04, I made the jump to 11.10.  Now having done so I'm finding several problems:

1) No GRUB menu.  Just a blank purple screen as I wait for the login screen.  Not an emergency, but I'd like the option of other modes/previous kernels should something go wrong in the future.

2) Reduced screen resolution. I run an nVidia 5600 card with 256 MB and a Dell E773c monitor.  Right now the best I can manage is 1024 x 768 when under 11.04 it could manage 1280 x 960.  It's a noticeable and aggravating difference.  xrandr tells me that 1024 x 768 is now as high as it goes, and resolution controls on my nVidia settings control panel are disabled.

3) Periodic failure to power down.  One out of every five times or so the shutdown command takes me to the login screen instead of shutting down, and from there "Shut Down" does nothing.

I'm running the UI on GNOME instead of Unity.  If anyone can point me in the right direction for any of these problems I'd greatly appreciate it.

---

### Post by cipherboy_loc on 2012-10-08
To answer question 2, I believe the key to access the grub menu is either the shift or escape key. Hit them on boot and it should display an option to load the grub menu. However, you can probably disable it and have it always show the boot menu by modifying /etc/default/grub. Check here for more information: [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

For question two, make sure all drivers are up to date and try reinstalling the nvidia driver.

As for the third question, do you have another user logged in (ornovae you logged onto a tty)? I have found that logging on to a tty prevents it from shutting down correctly.


Thanks,
Cipherboy

---

### Post by abelundercity on 2012-10-09
OK, I'll work with the GRUB at that link, thanks.

I tried getting the most recent drivers using the instructions found [here]("http://mygeekopinions.blogspot.com/2011/06/how-to-install-nvidia-2750907-driver-in.html") but the Additional Drivers application can't seem to find the driver and I walked back the changes.  Currently my system is using the Version 173 driver.  I tried removing and reinstalling that driver through the application and now the X Server Display Configuration outputs:

> Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.

My wife and I are pretty good about logging out of our accounts, so I don't know if that's it, for the shutdown problem.

---

