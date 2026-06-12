---
title: "Ubuntu Drivers..."
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by iSephy on 2009-12-21
I have a dual-booting HP Pavilion a1209n, with two 200gb hard drives. Windows is installed on the slave drive and Ubuntu on the master. I have all the drivers I need on the Windows drive, but I want to get them on Ubuntu so I can set my screen resolution bigger and enable my wireless internet. Ubuntu's Hardware Drivers program (System>Administration) does not detect the wireless PCI card or Integrated Intel Graphics Card. Help D:

Thanks

~Seph

---

### Post by Mark Phelps on 2009-12-21
You don't "get drivers" for installing in Ubuntu, it does hardware detection, determines the drivers, and obtains them by itself.  IT's not like MS Windows where you need a driver disk.

Howver, since your machine comes with only 64MB of video memory, my guess is that you have a really old video chip -- one way to old to have restricted drivers available in the newer Ubuntu distros.

To find out what you have, boot from an Ubuntu Live CD.  Once running, open a terminal and type "lspci".  In that list somewhere, it will show the video card/chip you're using.

You can post that back here, but my guess is it's probably something like an Xpress 300, for which there are no restricted drivers.

---

### Post by iSephy on 2009-12-21
I fixed it by downgrading to 9.04 which lets me use the resolution 1024x768, which makes my screen look a lot better, I still need to fix the wireless internet, but for now, I'm good! Thanks!~

---

