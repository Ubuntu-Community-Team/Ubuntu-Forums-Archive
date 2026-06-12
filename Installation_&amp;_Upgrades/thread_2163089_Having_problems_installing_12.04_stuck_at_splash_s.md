---
title: "Having problems installing 12.04: stuck at splash screen"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by kbryant on 2013-07-17
Hello,

I'm running a freshly built computer, no windows installed or anything, and I am trying to install 12.04 from a usb stick.

So first attempt gave me a bootloader install failed error and I think I was able to fix it with boot repair.  This is the result of that: [http://paste.ubuntu.com/5883070/](http://paste.ubuntu.com/5883070/)

I rebooted with the ssd I installed into, and the problem now is it gets stuck on the splash screen indefinitely.  I tried booting in recovery mode too, but the same thing happens.

Any suggestions on how to fix the problem would be appreciated.  If more info is needed, I'd be happy to give it.

Thanks!

---

### Post by dino99 on 2013-07-17
boot without "quiet splash" to let you see where/when it hangs : you can do that by editing the boot line, or making it parmanent (sudo gedit /etc/default/grub ; then: sudo update-grub)

maybe some boot options could help : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by kbryant on 2013-07-17
Oh I think I fixed it!  I guess I had grub installed on the live usb.

---

