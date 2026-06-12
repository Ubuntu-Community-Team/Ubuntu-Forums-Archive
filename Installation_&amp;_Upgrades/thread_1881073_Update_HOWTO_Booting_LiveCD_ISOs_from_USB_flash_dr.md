---
title: "Update: HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by ghat on 2011-11-14
hi

This is about 
[URL="http://ubuntuforums.org/showthread.php?t=1288604&page=4"]
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2[/URL]

Grub versions have evolved since the thread was closed, and I found this another post

[ Using Grub2 and LUA installed on USB booting ISO images ]("http://linux.xvx.cz/2010/03/using-grub2-and-lua-installed-on-usb-booting-iso-images-2/")

Basically some of the syntax needs updating

in grub.cfg
```

insmod vbe

lua /boot/grub/listisos.lua

```and in listisos.lua
```

      "\nlua /boot/grub/bootiso.lua"

```I found this to be a good way to have multiboot OS, as you just need to plop in new versions on the iso when the distro updates in the same USB stick.  you can also update or addon to the bootiso.lua if you want to use any other types of linux CD's just figure out the kernel options and put another if-else block... 
and you can use the same USB stick (in my case micro-SD) in android, windoze, etc... for your other activities... 

Ghat

---

