---
title: "New Video card upgrade"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by matamoscas on 2012-03-11
Hi,

I don't have a problem yet, but if possible, I want to avert it in the future. =)

I have an ATI video card atm, and it works on my system, but I want to upgrade to a new Nvidia card.

Is it just as simple as turning everything off, plopping in the new video card, and installing the new Nvidia driver??

I am curious if I can expect conflicts with the old driver? Do I need to remove the old driver?

Thanks in advance,
-matt

---

### Post by lrgmmc on 2012-03-11
From my experience you will need to remove the ati drivers first. then reboot with the new card in. then install the new drivers.

---

### Post by papibe on 2012-03-11
Right after you installed the card. Boot into recovery mode and go to text mode. Remove (or just rename) it:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then restart your computer. While you are in the desktop, go to 'Additional Drivers' and install the Nvidia driver.

Regards.

---

### Post by matamoscas on 2012-03-12
Cool thanks for the help =)

---

