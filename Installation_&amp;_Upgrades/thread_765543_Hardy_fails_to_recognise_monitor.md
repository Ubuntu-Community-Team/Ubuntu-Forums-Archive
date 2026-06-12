---
title: "Hardy fails to recognise monitor"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Smudger on 2008-04-24
Just upgraded to 8.4 and it fails to recognise my monitor.

All I get is an "Out Of Range" message against a black background.

Anyone got any idea's what I can do to resolve this issue?

---

### Post by Peter09 on 2008-04-24
Whats your graphics card?

PC

---

### Post by ssam on 2008-04-24
can you get a commandline?

if so can you run
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

and then reboot

---

### Post by Smudger on 2008-04-24
Nvidia NV44A [GeForce 6200]

---

### Post by Smudger on 2008-04-24
> **ssam said:**
> can you get a commandline?

if so can you run
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

and then reboot

I cant get nothing, all I have is a blank screen

---

### Post by Peter09 on 2008-04-24
the other option is to install envyNG from the command line.

I think its something like

```
sudo apt-get install envyng-gtk
```

then run

```
envyng
```

which will install the lastest nvidia driver

PC

---

### Post by peterlozano on 2008-04-25
I have this same problem.

I installed Ubuntu 7.10 3 weeks ago and everything has been running fine.

Upgraded to 8.04 and I got 'Out of sync' on my monitor and a black background.

After trying the dpkg-reconfigure and anvyng advices above it started working at 800x600 but nvidia-settings seems not to recognize my monitor.

I did the same upgrade on a laptop and it went ok.

---

