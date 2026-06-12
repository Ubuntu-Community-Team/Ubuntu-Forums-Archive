---
title: "Problem installing Ubuntu 6.10"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by Schjoh on 2007-04-02
Hi.

I'm trying to install Ubuntu 6.10 on my machine (AMD 64). I've tried installing with the versin for AMD64 and the one for I386. Furthermore i've tried to install Ubuntu 7.04. All have the sam problem. When I boot from the CD, I come to a menu, where the first chose is: START AND INSTALL UBUNTU.
If I choose this one, I come to a loading screen, and then the screen turns black, and nothing happens.

I've tried hitting F6 and writing:
Nolapic (It got a little further before turning to blackscreen)
acpi= ht noapic nolapic (An message appears: Kernel synchronising. Killing init (or something like that))

I've tried the I386 on two other computers, where there were no problems at all.

---

### Post by taurus on 2007-04-02
Could be a problem with your graphic card.  Try the alternate CD instead.

---

### Post by snailian on 2007-04-02
Try this:
Before you choose  "Start or install ubuntu", hit F4 and choose a resolution. Then try and install it. I had the same problem, and this fixed it. Good luck.

---

### Post by Schjoh on 2007-04-03
Thanks for the advices. I tried the alternate cd, and I the I had no problem in installing Ubuntu. Except that I know can't start Ubuntu. When I'm booting, my computer I just get a black screen.

---

### Post by taurus on 2007-04-03
So it does boot but X is having a problem running!  If that's the case, boot into recovery mode from GRUB menu and reconfigure X again with

```
dpkg-reconfigure xserver-xorg
```
Use **vesa** driver for your graphic card for now and if you're not sure about a question, just use a default.  Then, reboot and see what happens.

```
shutdown -r now
```

---

