---
title: "Fiesty Upgrade - X Server Crash!"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by askmeabouttruth on 2007-04-14
I upgraded to Fiest Beta some time ago. But, today after getting the latest distribution updates and after the required reboot, X server simply fails, the main reason listed as "screens not found". Very odd and very discomforting. I have an nvidia card. anyone else have this issue? :confused: Will it fix itself out if I keep updating?

---

### Post by fice on 2007-04-14
Ive been running feisty for a while on an nvidia as well. When updating to feisty herd 5 there was a kernel upgrade so you have to update your nvidia driver for your new kernel. to be able to access your xserver try modifying your xorg file, you can type

sudo nano /etc/X11/xorg.conf

nano is the terminal text editor of my choice but you can try another one if you prefer, although gedit or kate and the other graphical ones wont work unless your actually get the xserver started first.

once there look for the section named device and under that section if you had the previous version of the nvidia driver properly installed it should say "nvidia" on the driver line, change that to "nv" which is the generic driver for the nvidia cards. Save it and restart your computer. You should be able to log in to your graphical interface where you can now update your nvidia driver properly. 

As a reminder for the future, with nvidia cards you have to update your driver as soon as you update your kernel. 

I hope that helps.

---

