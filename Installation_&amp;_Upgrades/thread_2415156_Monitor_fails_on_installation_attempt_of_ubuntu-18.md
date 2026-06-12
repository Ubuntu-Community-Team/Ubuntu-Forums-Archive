---
title: "Monitor fails on installation attempt of ubuntu-18.04.2-desktop-amd64"
date: 2019-03-21
forum: Installation &amp; Upgrades
---

### Post by ronjo2 on 2019-03-21
Hi, I've been running Ubuntu dual booted with w10 for some time but it failed when updating to later version - kept returning to login screen. All attempts to solve the problem failed although it seemed to be related to Nvidia driver. I decided to do a new installation of ubuntu-18.04.2 but now am completely lost - the installation starts with the Ubuntu logo and lights indicating activity under the logo then my monitor screen crashes so am unable to see anything on the screen at all. The monitor is in fact a TV and therefore has an RGB connection only.
This worked with previous versions of Ubuntu until the latest updates.
I am unable to try any of the suggested fixes from other threads as I haven't got a clue what is happening on screen.
Is there a way to modify the installation .iso to allow installation or is it possible to install an older version of Ubuntu to work from?

---

### Post by CatKiller on 2019-03-21
You can try adding the nomodeset boot parameter.

---

### Post by ronjo2 on 2019-03-21
Thanks CatKiller but I have no way to access the boot parameter as installation not possible as per original question - any other ideas?

---

### Post by CatKiller on 2019-03-21
No, use that parameter for the install. Once you've done the installation - which will probably also initially need that parameter - you'll be able to install the proprietary driver. The problem is that nouveau is unable to identify the resolution of your television, and so your TV can't handle the one it picks, which makes the screen go black. The nomodeset parameter tells it not to try to set a different resolution, so the install will use the same resolution as the BIOS screen. It won't be pretty, but it will work.

---

### Post by ronjo2 on 2019-03-21
I've reinstalled ubuntu-16.04.6-desktop-i386 and it works fine.
Now that I have a working system I will try to upgrade and follow your advice re the nomodeset boot parameter.
Thank you very much for your time and help - wish me luck

---

