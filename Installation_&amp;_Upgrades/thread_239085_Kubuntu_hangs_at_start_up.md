---
title: "Kubuntu hangs at start up"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by moogii on 2006-08-18
I've installed Kubuntu

But it frrezes at start up.

It starts ok


Splash screen then. Kubuntu loads everything ok..

THEN....

Splash screen appears again (strange??!!)....then freezes there ..

Suppose to be login screen appear

Any fix?

---

### Post by anopheles on 2006-08-19
Might be the X-server failing.

CTRL-ALT-F1 and get a text prompt.
Login.
Have a look at the xserver logs, e.g. /var/log/Xorg.0.log

I had something like this when I tired to use an ATI 8500 and kubuntu attempted some default 3d acceleration driver that just doesn't work.  If that has bitten you, then you need to downgrade your X installation to use a normal driver, and then see here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Of course, there might be some other reason your X server has failed.

---

### Post by moogii on 2007-01-06
thanks ,but its ok now .

that was something to do with BIOS..VGA mode...

I turned it off..

Now my monitor turns off itself at start up and during shut down...?

---

