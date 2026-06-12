---
title: "Can You Custom Install Lucid?"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by DasFox on 2010-04-29
I was reading this on Ubuntu today:
[B]
[FONT=Arial Rounded MT][SIZE=2]When you install Ubuntu,  you will typically install a complete desktop environment. It is also  possible to install a minimal set of software (just enough to boot your  machine) and then manually select the precise software applications to  install. Such a "custom" install is usually favoured by server  administrators, who prefer to keep only the software they absolutely  need on the server. [/SIZE][/FONT][/B]

I have never personally noticed any sections in the install to allow you to do a custom minimal install, is this possible in Lucid?

If so how, or do I need to download just a mini install iso?

THANKS

---

### Post by drreed on 2010-04-29
There is a separate iso for that, called "alternate". I have one but I can't remember why I have it.

---

### Post by howefield on 2010-04-29
> **DasFox said:**
> If so how, or do I need to download just a mini install iso?

This sounds like what you need.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by DasFox on 2010-04-29
I found it for AMD:

[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso)

Thanks I'll give it a shot...

---

### Post by DasFox on 2010-04-29
This sucks the mini Lucid AMD mini iso doesn't have supported for my ethernet.

I find this odd since you can install a regular iso and it works, I would of thought the hardware support to be the same... :(

Darn...

---

### Post by drreed on 2010-04-29
> **howefield said:**
> This sounds like what you need.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Hey, thanks for that link. I wondered why I had that CD, but couldn't remember doing a text install from it. Now I know why. I actually tried building an install from a server iso to do that.

---

### Post by kerry_s on 2010-04-29
> **DasFox said:**
> This sucks the mini Lucid AMD mini iso doesn't have supported for my ethernet.

I find this odd since you can install a regular iso and it works, I would of thought the hardware support to be the same... :(

Darn...

did you even start it? there's no network manager to do it for you.

sudo ifconfig eth0 up
sudo dhclient eth0

---

