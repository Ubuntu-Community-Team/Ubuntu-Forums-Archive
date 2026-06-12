---
title: "Advanced Ubuntu on USB key."
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by kevpatts on 2007-04-12
Hey all,

I'm looking to install a beryl enabled Ubuntu installation on a 2GB USB Key. This is fine, and I have got this basically working, but only for NVIDIA cards. Is it possible to have grub offer me two options, one of which I can use when I put the key in an NVIDIA box and one for use on ATI hardware, and have beryl working in both when running the correct hardware?

Kevpatts

---

### Post by kidders on 2007-04-12
Hi there,

Having your bootloader do that for you would be rather complicated, since its influence over your system ends the moment it begins booting.

Personally, I would prefer a more automated solution. Consider, for instance, the difference in the output of **lspci | grep -i vga** (assuming your machines only have graphics cards by one manufacturer) on a machine with an Nvidia card vs an ATI one. The most straightforward way to solve your issue would be to use that (or perhaps other distinguishing information, such as a network card's MAC address) to identify the proper X driver.

Imagine you created three xorg.conf files...[LIST]
[*]One for Nvidia, called maybe /opt/xorg.conf/xorg.nvidia.conf
[*]One for ATI, called maybe /opt/xorg.conf/xorg.ati.conf
[*]A fallback version (/opt/xorg.conf/xorg.generic.conf) with only a basic configuration.[/LIST]Now, suppose you created a script that copied (or maybe symlinked) the appropriate version into /etc/X11. You could call it /usr/local/bin/xorg-rewrite or something. At a bare minimum it could contain...```
#!/bin/bash
ln -s /opt/xorg.conf/xorg.$1.conf /etc/X11/xorg.conf
```You could then configure your system for ATI by invoking **xorg-rewrite ati**.

Then, using a pre-existing script as a template, you could set up a new service (let's call it /etc/init.d/xorg-rewrite) that would configure your system automatically at boot-time (and de-configure it at shutdown), based on the chosen criteria (eg the output of **lspci**). Once you kick-start things once with **sudo /etc/init.d/xorg-rewrite start**, your Ubuntu should be ready to go.

---

### Post by kevpatts on 2007-04-12
Thanks man, that's an excellent suggestion. Means I wouldn't even have to choose.

Thanks again, I'll get back to you if I have any issues implementing it.

Kevpatts

---

### Post by kidders on 2007-04-12
> **kevpatts said:**
> Thanks man, that's an excellent suggestion. Means I wouldn't even have to choose.Yep... the automation would be nice. :-)

Depending on your level of expertise, this may be stating the obvious, but one thing to watch out for is permissions. Creating shell scripts that run non-interactively as root is a *major* security risk ... be sure to **chown root:root** and **chmod 755** anything in /usr/local/bin or /etc/init.d, so your system stays nice & secure.

Post back if you have any difficulty.

---

