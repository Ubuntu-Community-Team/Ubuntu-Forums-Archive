---
title: "X won't start - Xorg.conf problem?"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by gwilson on 2006-10-25
Hi,

Since I upgraded to Edgy, my X configuration has been unstable. I can get X working properly, but when I restart the system, it's as if my xorg.conf file is not being read properly. X will not start.

I've done:  

sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg-reconfigure -phigh xserver-xorg
sudo dpkg-reconfigure xserver-xorg

When I do the reconfigure, I can type in "start x" and everything works fine. When I restart the system, I usually get a "no screens" error from X.

I have an Nvidia 5200 video card and had no problems whatsoever in Dapper. I've been selecting the "nvidia" driver lately when I reconfigure, and it seems to work fine until I restart.

Any ideas?

Glen

---

### Post by ahaslam on 2006-10-25
If you set your driver to the generic 'vesa' driver, does X start?

I know you don't want this driver but if it does work, it points to driver problems & you may consider another choice.

Tony.

---

### Post by gwilson on 2006-10-25
No.

I already tried selecting VESA and even VGA and it doesn't help.

It's as if it is looking at some non-customized xorg.conf that is located somewhere other than /etc/X11/xorg.conf  or maybe the reconfigure routine is writing xorg.conf to some odd location.

Either way, it's an odd one.

---

### Post by Josey on 2006-10-27
gdm.cfg-custom

remove everything under xgl

---

