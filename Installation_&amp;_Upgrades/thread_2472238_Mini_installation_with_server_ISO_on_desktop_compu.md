---
title: "Mini installation with server ISO on desktop computer"
date: 2022-02-21
forum: Installation &amp; Upgrades
---

### Post by mwmb2 on 2022-02-21
I want to have an Ubuntu 21.10 desktop as slim as possible. Therefore I used a server ISO image, selected mini installation and later installed xubuntu-core. Everything works fine except one thing annoying.

Everytime I run ```
sudo apt update
``` and ```
sudo apt full-upgrade
```, it reminds me daemons using outdated libraries and let me select which services should be restarted. There's no such reminding with the pure desktop version. How to avoid that reminding?

---

### Post by foxsquirrel on 2022-02-21
Pretty sure you are heading down the road of problems.

Its best to use the entire package as configured by Ubuntu.

If you are only using it as a server just install the server version that is headless and ssh into it.

Its really dependent upon your use of the server, if its going to be serving information over the internet most certainly use the headless version.

---

### Post by Tadaen_Sylvermane on 2022-02-22
Is this an official ISO? I ask because I've done this before without a hitch. I used to use the Server ISO almost exclusively until recently when I started doing chroot installs with a pxe boot. I've never seen that before. Is it maybe a new thing with 21.?

---

### Post by MAFoElffen on 2022-02-24
Also curious about this, as both are built on the Ubuntu Core, and there are sound conversions between editions. It ins't lie yeas ago, when there were actual diffrent kernels for each edition. It is package differences and configurations that are all handled with certain package suites.

What was said about Desktop Edition not having any daemons is not exactly accurate. We are talking about systemd...

If you chose Minimal Install on the Server LiveCD, just which daemons does it say it has to restart? Desktop does still have some (mine 45), just because of systemd, but it would be curious to see if they are the standard Desktop suite of connected by systemd, or other(???)
```

systemctl list-units --type=service --state=running

```

---

