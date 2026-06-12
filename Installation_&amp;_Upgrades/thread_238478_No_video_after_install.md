---
title: "No video after install"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by Super King on 2006-08-17
I've just installed Xubuntu on my desktop machine w/ Nvideo graphics card, but video is broken on boot (lots of lines, some colors). I'm assuming I could load up the live CD, mount the HD that Xubuntu is installed on, edit the xorg file (I believe that's the one, to change graphics drivers), and reboot into a working install. Will this work? Is there an easier way to get my video working?

---

### Post by taurus on 2006-08-17
At a prompt, type

```

sudo dpkg-reconfigure xserver-xorg

```
to configure your X again...

---

