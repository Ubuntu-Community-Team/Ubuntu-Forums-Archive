---
title: "New kernel didn't launch"
date: 2016-06-17
forum: Installation &amp; Upgrades
---

### Post by joaoamaroscp on 2016-06-17
Hi.

I compiled a new kernel for my ARM computer because I needed to change some configs. It's a Utilite Board, that has his own kernel. 

I cloned the right version from git:
```
git clone ...
```

Then I created the config file the way I needed to:
```
[FONT=Consolas][COLOR=#333333]make [/COLOR][/FONT]cm_fx6_defconfig
nano .config
```

Built the kernel image:
```
make -j4 zImage dtbs modules
```

Installed the new kernel on my computer:
```
sudo cp ./arch/arm/boot/zImage ./arch/arm/boot/dts/*.dtb /media/bootsudo make modules_install
sudo make firmware_install
sudo make headers_install INSTALL_HDR_PATH=/usr
```

After that, I rebooted the system and it still launches with the old kernel.

I have no GRUB on this computer, and I couldn't install, nor GRUB CUSTOMIZER.

Do you have any tip that could help me with this?

---

