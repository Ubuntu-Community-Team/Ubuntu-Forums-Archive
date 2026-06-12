---
title: "Dual boot Ubuntu with Xubuntu"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by sheepop39 on 2008-09-10
I am planning on upgrading my computers memory from 256 mb to 1gb or 2gb and after that I am planning on dual booting Ubuntu with Xubuntu (don't ask why) and I am wondering if there is way to install Ubuntu onto the another partition but without have GRUB installed again since I have of heard problems with having GRUB installed again, does anyone have an idea what to do?

---

### Post by snowpine on 2008-09-10
You can install Ubuntu on top of Xubuntu by typing:

```
sudo aptitude install ubuntu-desktop
```

Then, you can choose between them each time you log in using the Sessions feature (Gnome for Ubuntu, Xfce for Xubuntu). All of your apps and documents will be common to both Xubuntu and Ubuntu.

Should you desire to install Ubuntu on a completely separate partition, Grub is smart enough to find existing operating systems and create the appropriate entries. The only catch is that Ubuntu and Xubuntu will appear exactly the same in your Grub menu (as they use the same Linux kernel), so you'll have to distinguish between them using the partition name (/dev/sda1 vs /dev/sda2 for example) or edit your /boot/grub/menu.lst file to give them descriptive names such as Ubuntu and Xubuntu.

Hope that helps you out!

---

