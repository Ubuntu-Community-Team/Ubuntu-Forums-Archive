---
title: "Hotplug and agpgart/nvagp?"
date: 2004-12-16
forum: Installation &amp; Upgrades
---

### Post by bube on 2004-12-16
I have just pluged in my old nvidia TNT2 and installed nvidia-glx. That works great! Now I also want to use Nvidia's **nvagp** insted of **agpgart** so I enabled it in my X config. But **hotplug** seems to load **agpgart** and **via_agp** eventhoug I listed them i **/etc/hotplug/blacklit**.

How do i make sure that hptplug dosn't load the agpgart module? :confused:

---

### Post by p!=f on 2004-12-17
[QUOTE=bube]I have just pluged in my old nvidia TNT2 and installed nvidia-glx. That works great! Now I also want to use Nvidia's **nvagp** insted of **agpgart** so I enabled it in my X config. But **hotplug** seems to load **agpgart** and **via_agp** eventhoug I listed them i **/etc/hotplug/blacklit**.

How do i make sure that hptplug dosn't load the agpgart module? :confused:[/QUOTE]
This is probably not that type of an answer you'd like to hear...
I've never really used agpgart module since I found out using internal nVidia AGP support gives me more performance (GF2, GF4MX440, GF4Ti4200). Unfortunately, I have also never successfully blacklisted that module from loading. :) Does anyone know how to do it? The workaround I use is quite simple, create your custom kernel without agpgart module support compiled in.

---

### Post by bube on 2004-12-17
here is another quick and dirty trick: simply rename/remove the unwanted modules.

But there must some way to do it clean. :-k

---

