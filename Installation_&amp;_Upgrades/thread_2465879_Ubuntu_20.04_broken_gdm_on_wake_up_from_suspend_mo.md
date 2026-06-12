---
title: "Ubuntu 20.04 broken gdm on wake up from suspend mode"
date: 2021-08-13
forum: Installation &amp; Upgrades
---

### Post by kauanmocelin on 2021-08-13
[COLOR=#242729][FONT=-apple-system]I'm using a desktop with Ubuntu 20.04 and a Nvidia RTX 2070 with driver "nvidia-driver-470". Sometimes when SO goes to suspend mode, on wake up GDM come back broken [like this image]("https://i.stack.imgur.com/ewiKh.png").

[/FONT][/COLOR][COLOR=#242729][FONT=-apple-system]So I need to run this command to GDM works again: ```
sudo systemctl restart gdm
```[/FONT][/COLOR][COLOR=#242729][FONT=-apple-system]

[/FONT][/COLOR]I tried to downgrade nvidia driver to 460 but when clicked do suspend its showed a black screen with underscore blinking and nothing happened.

I tried to use nouveau driver and when I click on "settings" feature of Ubuntu my session simply logout.[COLOR=#242729][FONT=-apple-system]
[/FONT][/COLOR]

---

### Post by MAFoElffen on 2021-08-16
For the 460 Linux Driver, here is what NVidia says is know porblems and the fixes...
> - Disable flipping in nvidia-settings (uncheck "Allow Flipping" in the "OpenGL Settings" panel)
- Disable UBB (run 'nvidia-xconfig --no-ubb')
- Use a composited desktop
Which Wayland would be the fist to go off the list for that driver...

Have you tried using other Desktops yet?

---

