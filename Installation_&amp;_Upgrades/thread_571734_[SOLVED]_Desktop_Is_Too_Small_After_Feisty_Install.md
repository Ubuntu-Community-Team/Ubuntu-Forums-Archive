---
title: "[SOLVED] Desktop Is Too Small After Feisty Install"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2007-10-09
I've just done a clean install of Fiesty, not an upgrade. What do i need to configure to increase the desktop, so it occupies my full laptop's screen area?

Edit:
This is an Acer Tavelmate 630. I've looked at some of the solutions to edit xorg.conf, but neither Dapper, Edgy, or Fiesty upgrades ever had problems with the monitor and the laptop's screen area. I'm just wondering what the change might have been.

---

### Post by tgm4883 on 2007-10-09
You need to increase the resolution.  I have a compaq that is the same way.  It runs at 1024x768, and if you try to use a smaller resolution, you get black bars all the way around.

EDIT

You may also need to install the proprietary driver for your video card before you can increase the resolution.

---

### Post by cmnorton on 2007-10-09
my problem is how to increase it, and as soon as my post-installation update manager session runs, I'll go into restricted drivers and enable the nvidia driver. It won't enable with the update going on.

Edit: enabling in restricted drivers fixed problem

---

### Post by tgm4883 on 2007-10-09
System > Preferences > Screen Resolution

---

