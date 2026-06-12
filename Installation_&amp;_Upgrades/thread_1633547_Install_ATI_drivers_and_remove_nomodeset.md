---
title: "Install ATI drivers and remove nomodeset"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by sim0s on 2010-11-29
Hello guys,

I have managed to install ubuntu 10.10 at my laptop but by removing the quiet splash in the grub menu and setting the nomodeset. This as I know it reduces the resolution and I can say that the resolution while interacting with the interface is quite poor. The reason is because the ATI drivers are not installed or there is any other reason?

Also can you give me some help as to how to install the ATI drivers and remove the proprietary one?


Thanks,
sim0s

---

### Post by dino99 on 2010-11-29
remove xorg.conf (now drived by the kernel)

sudo rm -f /etc/X11/xorg.conf

open synaptic: system admin synaptic (top panel menu)

search for: fglrx and remove it if installed
search for: ati and remove the related installed packages


search for xserver-xorg-video-ati and install it

now rebbot then check driver activation (system admin additional driver)

---

### Post by sim0s on 2010-11-29
HEy ,, THEre is no xorg.conf file in the x11 folder. I followed the procedure you suggested and after rebooting I didn't notice any change. Also the title bar is missing and there is a windows manager error.

What should I do?

---

