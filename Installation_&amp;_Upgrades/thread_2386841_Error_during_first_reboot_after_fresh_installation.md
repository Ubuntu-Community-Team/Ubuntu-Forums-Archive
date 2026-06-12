---
title: "Error during first reboot after fresh installation"
date: 2018-03-11
forum: Installation &amp; Upgrades
---

### Post by jhong2 on 2018-03-11
Hi

I reinstalled Ubuntu 16.04.4 today, - fresh install.

system hang during the first reboot straight after finished install the Ubunut, screenshot provided.

Can you someone have a look please?

Thanks
[ATTACH=CONFIG]278901[/ATTACH]

---

### Post by oldfred on 2018-03-11
nouveau issues may mean you need nVidia driver?
What brand/model system?
What video card/chip?

If you needed nomodeset to boot installer, you need that to boot install or until you install correct nVidia driver from Ubuntu repository. Do not install from nVidia directly.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

[/URL]nVidia Must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 

 17.10 defaults to wayland where nvidia's driver don't work 
   [https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959](https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959) by 1fallen
> EDIT: This seems to work for my card here, instead of using "nomodeset" I am using this "nogpumanager"
And I have to watch carefully any changes made to "/etc/X11/xorg.conf" 

[ ]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by jhong2 on 2018-03-12
Sorry, I'm using 16.04.4 and the graphic card is Nvidia Quodra K2200

after I booted into the system and installed nvidia 384 driver, everything seems working
Thanks

---

### Post by Federico_Carta on 2018-03-13
Hi, I think I have exactly the same problem. I wrote it here [https://ubuntuforums.org/showthread.php?t=2386946](https://ubuntuforums.org/showthread.php?t=2386946)

Now I am also trying to install the 348 NVidia driver. Hopefully it will work.

I have one question: also in your case before installing the driver the system was unable to reboot/shut down, after logging in?

---

