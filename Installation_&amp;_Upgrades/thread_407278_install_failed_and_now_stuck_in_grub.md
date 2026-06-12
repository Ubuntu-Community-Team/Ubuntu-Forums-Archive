---
title: "install failed and now stuck in grub"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by wonkderboko on 2007-04-11
Hi, I am attempting to install Ubuntu (for the first time) on my machine with no cd-rom drive that was running win98 at the time.

I followed this excellent page:
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

And it worked fabulous, but then during the install I screwed up and it was not able to find the image over the network.  So now I have no win98 but can boot into Grub successfully.

I would like to restart the install of ubuntu. Is it possible from within grub?  
thanks
-wb

---

### Post by ndefontenay on 2007-04-12
I think that you will have to burn this image on a CD and install from your CD ROM drive...

I don't think it would be possible. You would need to have your network configured first and if it's screwed, then you can't access the image.

I'm not sure grub can configure your network drive.

Can you type ifconfig from withing grub?
If it returns some network information then there's some chance : )

---

