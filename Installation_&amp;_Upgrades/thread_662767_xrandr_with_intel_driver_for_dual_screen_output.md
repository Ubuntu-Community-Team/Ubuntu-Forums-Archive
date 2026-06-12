---
title: "xrandr with intel driver for dual screen output"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by amaragon on 2008-01-09
Hello everyone,

I just installed from scratch v7.10 and I'm very satisfied with it, except for the dynamic handling of multiple screens. The System -> Administration -> Screens and Graphics application is really buggy at this stage, so I found that doing things through the command line using the xrandr command was  a better option.

I have an intel chip (915gm) and I was able to configure the dual screen using xrand as follows:

$> xrandr --output LVDS --mode 1280x768 --pos 0x0 --output VGA --mode 1440x900 --right-of LVDS

Now, the problem with this approach is that I loose DRI support because the combined length of the two screens in the X direction is 2720. There is a limitation with these cards of having a maximum virtual size of 2048x2048 and if you want a larger size, you can, but DRI support is lost.

I could place one screen on top of the other, something like:

$> xrandr --output LVDS --mode 1280x768 --pos 0x0 --output VGA --mode 1440x900 --pos 0x768

and this still works with DRI support because all screens lie within the limits. However, it is VERY annoying to have the VGA screen below when it is physically positioned to the right of my laptop.

Does anyone know how to solve this problem? I would like to have both screens working with DRI support, my laptop on the left and the VGA on the right. Any help is really appreciated.

a²

---

