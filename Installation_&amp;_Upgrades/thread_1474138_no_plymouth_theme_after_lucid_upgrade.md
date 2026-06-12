---
title: "no plymouth theme after lucid upgrade"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by mathfeel on 2010-05-05
Upgrade to lucid (by running update-manager -d) succeeded with no major error. But when I reboot the computer, the boot splash screen is "Ubuntu Studio" and the login screen's background is a "Ubuntu-eee" png picture.  A funny mess.

I was able to get to the new boot splash screen by remove --purge ubuntu-studio, which I must have installed sometimes in the past, but I don't see anyway of getting the new theme for the login screen.

I have this eeepc for about 2 years and never have to fresh-install Ubuntu except the first time.  I much rather not have to fresh-install just to solve some aesthetic problems.  I am pretty sure it's due to some package I installed in the past, but I don't see any Ubuntu-eee related package in Synaptic either.

Anyone?

---

### Post by charlesopondo on 2010-05-07
If you already have Plymouth installed, this trick, from elsewhere in this forum, worked for me:

In the terminal:

```
sudo pico /etc/initramfs-tools/conf.d/splash
```

then insert the text:

```
FRAMEBUFFER=y
```

exit, saving changes, then back to the terminal:

```
sudo update initramfs -u
```

Then reboot.

---

### Post by mathfeel on 2010-05-11
Actually I reinstalled/re-removed ubuntu-studio and it worked!

As for the login screen, all I have to do is run change background as gdm using
```
gksu -u gdm dbus-launch gnome-control-center
```

I have one more issues. The same Ubuntu-eee background shows up at the password prompt for locked screen.  I have no idea which user is responsible for that.

---

### Post by perspectoff on 2010-05-16
> **charlesopondo said:**
> If you already have Plymouth installed, this trick, from elsewhere in this forum, worked for me:

In the terminal:

```
sudo pico /etc/initramfs-tools/conf.d/splash
```

then insert the text:

```
FRAMEBUFFER=y
```

exit, saving changes, then back to the terminal:

```
sudo update initramfs -u
```

Then reboot.

Does nothing for me, even with the correct command

 sudo update-initramfs -u

---

