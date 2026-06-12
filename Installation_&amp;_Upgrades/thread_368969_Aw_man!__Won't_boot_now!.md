---
title: "Aw man!  Won't boot now!"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by mgrusin on 2007-02-23
Hello, I've had an Ubuntu installation working for a few months now.  Tonight I installed some recommended updates, including I believe a kernel update.  The machine asked to be rebooted, so I did.  But now when I boot into Ubuntu, I get the splash screen with the progress bar for a handful of seconds, then it crashes to a black screen with a busybox prompt.  Grub now lists a few kernels, and it does this for all of them.

I'm a bit of a noob but willing to get my hands dirty.  What should I check first?

Thanks! -Mike G.

---

### Post by taurus on 2007-02-23
Log in with your username and password.  Then, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```
Use **vesa** as a driver for your graphic card.  Then, reboot and see what happens to X this time.

```
sudo shutdown -r now
```

---

### Post by willc0de4food on 2007-02-24
also, if you have an ATi video card you'll want to try the radeon driver.
when trying to boot to the ubuntu 6.10 livecd (xorg/gdm never starts by default) but the only driver i can get to a gui with is the radeon driver.
BUT if you have an nvidia car, this wont matter :]
to edit the xorg config file from command line you'd do sudo nano /etc/X11/xorg.conf taking note of the capital X in X11. also, if you can't get to a command line by default, try pressing ctrl+alt+F1 and then logging in with your regular user.

---

