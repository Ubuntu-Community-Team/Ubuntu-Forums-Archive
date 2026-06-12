---
title: "App does not launch (vibrantLinux and more)"
date: 2023-01-18
forum: Installation &amp; Upgrades
---

### Post by ottercat on 2023-01-18
Hello, 

I installed vibrantLinux from flatpak, ([COLOR=#000000][FONT=Menlo]flatpak install flathub io.github.libvibrant.vibrantLinux) and it seemed fine. The app comes up in app search, but when I click on it absolutely nothing happens. I then uninstallled ([/FONT][/COLOR][COLOR=#262626][FONT=Consolas]flatpak uninstall --all[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]) it and installed it again.  It did not help. Can I fix this? Thanks.[/FONT][/COLOR]

---

### Post by grahammechanical on 2023-01-18
As I understand it VibrantLinux only works with Nvidia video adapters and does not work on Wayland. If you are using Ubuntu 22.04 then Wayland is the default video server. You will need to switch to the X-Server at the login screen.

[https://github.com/libvibrant/vibrantLinux](https://github.com/libvibrant/vibrantLinux)

[https://flathub.org/apps/details/io.github.libvibrant.vibrantLinux](https://flathub.org/apps/details/io.github.libvibrant.vibrantLinux)

Regards

---

