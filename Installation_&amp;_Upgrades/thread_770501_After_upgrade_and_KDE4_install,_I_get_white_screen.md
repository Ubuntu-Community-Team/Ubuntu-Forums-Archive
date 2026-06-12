---
title: "After upgrade and KDE4 install, I get white screen"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by bioShark on 2008-04-27
Hi All

I have just made an upgrade from kubuntu 7.10 to kubuntu 8.04. After the upgrade, I have installed from adept the "kubuntu-kde4-desktop" package. Everything seemed to work fine, but when I try to log in with KDE4 session, I get a white screen , and that's it. But actually I am logged in fine, because if I press on the screen where I know I have some icons, the applications do open.

After the upgrade and reboot, at first it didn't wanna start the X server because it said some error about the graphic card driver. I have installed manually the driver...and still at some point it through me an error, but I didn't pay attention because the startX worked. Maybee it's got something to do with that.

Hope you can help me because I really like KDE4.

Thx.

---

### Post by bioShark on 2008-04-27
Don't ask me how, but somehow I have managed to reconfigure the xorg.conf file, and to repare the X server.

It works now...looks fabulous.

---

### Post by bioShark on 2008-04-27
Sorry guys, but it looks it's still not solved. That one time I have managed to log into KDE4, I needed to reboot, and after that the same problem appeared.
It's clear to me that this is a driver problem. For example after I normally install the driver, in KDE3.5 I have access to the NVIDIA configurations, but the time I was logged in KDE4 those configurations weren't available, exactly as I wouldn't have installed the driver. And the screen wasn't clear at all.


Thx in advance

---

### Post by kingtaurus on 2008-04-27
Are you using kwin or compiz?
Are you using Xgl or just vanilla xserver (perhaps with AIGLX)?

I was getting the white screen while using compiz and AIGLX (with an ATi card). The work around was to use:

<Alt>-F2 to get a run prompt (still in white screen mode), and typed
kwin --replace (or metacity --replace if you were in gnome).

---

### Post by bioShark on 2008-04-27
thx, I will try that...and get back to you!

---

### Post by bioShark on 2008-04-27
I works, thx. But it seems I have to do this every time I reboot. I really don't know if I am using xgl or not. I would guess xgl, because my videocard is old, geForce4 MX 440. But still...hope I'll find something.
Regarding compiz, yes when In first logged into KDE 3.5, after the upgrade I have installed it from desktop effects. Do you I should uninstall it?

---

### Post by bioShark on 2008-04-27
Yes, disabling the Desktop effects did solve the problem. But still there are some minor desktop features which I had in KDE 3.5 and in KDE 4 (without effects) I don't have, such as: transparent windows. But, I'll find a solution.

---

### Post by kingtaurus on 2008-04-28
I don't know what the best course of action is ... but I think you would probably be best off leaving it disabled until they release the first round of major updates (my guess is there is going to be at least a few patches in the next few weeks).

---

