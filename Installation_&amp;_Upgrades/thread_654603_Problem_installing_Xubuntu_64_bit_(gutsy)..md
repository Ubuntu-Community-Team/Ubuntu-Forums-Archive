---
title: "Problem installing Xubuntu 64 bit (gutsy)."
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by Gigamo on 2007-12-31
Hi everyone.

I just formatted my 32bit ubuntu installation and wanted to try out XFCE in Xubuntu. So I thought, why not immediatly go for 64 bit as well. First I had problems getting the LiveCD to work, which wouldn't boot except if I added the "nosplash" boot option.

So there I went, installing Xubuntu. But when I booted into the freshly installed Xubuntu for the first time, I already got this X error popping up saying that it has to run in "low graphics mode", so I clicked continue. After that, my screen just stayed black for over 10 minutes and nothing happened. I don't know what's wrong here, I didn't have this problem when installing 32bit ubuntu, and neither did I get the X error :(

My CPU is a T7700 which has 64 bit support.

Thanks!

---

### Post by taurus on 2007-12-31
Press <Ctrl><Alt>F2 and reconfigure your X server again after you log in with your username and password.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, restart X with <Ctrl>Alt>Backspace.

---

### Post by Gigamo on 2007-12-31
> **taurus said:**
> Press <Ctrl><Alt>F2 and reconfigure your X server again after you log in with your username and password.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, restart X with <Ctrl>Alt>Backspace.

When exactly should I press <Ctrl><Alt>F2? I don't even get to the login screen as of now.

---

### Post by taurus on 2007-12-31
Or just boot into recovery mode from GRUB menu and run that command again except you don't have to use sudo now since you are logged in as root.

```
dpkg-reconfigure -phigh xserver-xorg
```
Then, reboot with

```
shutdown -r now
```

---

