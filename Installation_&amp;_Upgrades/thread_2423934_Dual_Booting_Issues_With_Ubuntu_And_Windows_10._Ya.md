---
title: "Dual Booting Issues With Ubuntu And Windows 10. Yayyy Me!!!! Lol!!!!"
date: 2019-07-31
forum: Installation &amp; Upgrades
---

### Post by pmarcal12 on 2019-07-31
I installed the Ubuntu 19.04 on my computer (ASUS FZ50VX) alongside with Windows 10 Home (freshly installed). The 18.04 booted to the GUI before the installation and then crashed, so I tried the 19.04... It allowed me to install (on safe mode only), then I restarted it as asked and the it stopped on the ubuntu initial loading screen. After that I selected the advance boot and then it finally started lookin like safe mode. I installed some updates and restarted once again, and then it stopped again on loading screen (on the second dot) but after that it showed up the screen on the picture. What have I done wrong?[https://i.stack.imgur.com/IgLEN.jpg](https://i.stack.imgur.com/IgLEN.jpg)

---

### Post by jeremy31 on 2019-07-31
Moved to a new thread, please do not use image tags on large images as some people have slow internet

---

### Post by pmarcal12 on 2019-07-31
I installed the Ubuntu 19.04 on my computer (ASUS FZ50VX) alongside with Windows 10 Home (freshly installed). The 18.04 booted to the GUI before the installation and then crashed, so I tried the 19.04... It allowed me to install (on safe mode only), then I restarted it as asked and the it stopped on the ubuntu initial loading screen. After that I selected the advance boot and then it finally started lookin like safe mode. I installed some updates and restarted once again, and then it stopped again on loading screen (on the second dot) but after that it showed up the screen on the picture.
What have I done wrong?

---

### Post by oldfred on 2019-07-31
Have you updated UEFI from Asus? And updated SSD firmware?

If nVidia, you will need nomodeset.
You say you installed Windows. It should be installed in UEFI boot mode, but if you re-installed you may have used the old BIOS/MBR configuration? Ubuntu must be in same boot mode.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
Some new versions of Ubuntu will now install nVidia driver as part of install. But most need nomodeset on first boot also, and then you can install nVidia driver from Ubuntu repository.

See also link below on steps to install Ubuntu in UEFI boot mode.

---

### Post by oldfred on 2019-07-31
Duplicate threads merged.

Please do not post duplicate threads.

---

