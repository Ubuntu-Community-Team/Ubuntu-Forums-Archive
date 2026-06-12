---
title: "[SOLVED] Can't log in after upgrade to Edgy"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by pinkunicorn on 2007-02-14
After upgrading to Edgy, I'm not able to log in. My problem is similar to the one in [http://www.ubuntuforums.org/showthread.php?t=357000](http://www.ubuntuforums.org/showthread.php?t=357000) but I don't think it's identical.

When I boot the computer, it gets to the log in screen as usual. After logging in, I get the splash screen and then see the panel opening on an empty screen. The background is set to the default theme and all the applets that are supposed to be in the panel appear. Gaim autostarts. Sometimes I have time to open an application.

Then, after at most perhaps thirty seconds, usually less, the screen goes black for a short time, then the screen appears as before briefly, goes black again, and then throws me back to the login screen. If I log in again, the same thing happens.

I can log into the computer through the network without problems. I have run apt-get update and apt-get dist-upgrade this way, but this does not change anything.

I have checked the permissions of the files in my home directory as the thread linked above suggests and see nothing alarming. All files are owned by the user except for .., .emacs.d, .rnd, and .viminfo. Apart from .., I think these as well should probably be owned by the user and not root, but on the other hand I can't imagine them having anything to do with logging in.

So, how to fix this?

---

### Post by pinkunicorn on 2007-02-14
Oh, one more thing: if I press C-A-F1 to get to a text console, it has lots of messages on it. Something like this:

> Calling INT 0x1A (F000:FE6E)
>   EAX is 0xB10A
[repeated some times, with the last hex value different]
> usplash: No usable theme found for 1024x768
> screen init failed
[a few more repeats of the first two lines, with different last hex values]

---

