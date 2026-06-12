---
title: "Black screen, boot"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MartinCarlsen on 2008-10-05
I installed ubuntu 8.10 yesterday. After grub it doesn't show any text or usplash, just a black screen. This doesn't change with ctrl+alt 1-7. This doesn't change until login. After boot I've tried different things. Ctrl + alt 1-6 still doesn't work; the screen locks.  
I've tried the following without succes:
dpkg-reconfigure xserver-xorg -phigh
sudo /etc/init.d/gdm stop (total crash)

I think the problem is related to Ubuntu-kernel 2.6.27-4 generic because   
everything works as usual with the 2.6.24-19 kernel which of course is great.

lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500M GS (rev a1)

---

### Post by MartinCarlsen on 2008-10-06
Problem solved with the following workaround from

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269457](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269457)

"The workaround suggested by "captn" in this [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/246269) bug also worked for me :) on 2.6.27-4 -generic kernel. Thank you captn!

1) install: v86d
2) create: /etc/modprobe.d/uvesafb
with the following content (adjust resolution):
options uvesafb mode_option=1024x768-32 mtrr=3 scroll=ywrap
3) edit: /etc/modprobe.d/blacklist-framebuffer
add: blacklist uvesafb
3) edit: /etc/modules
add: uvesafb
4) run: update-initramfs -u
5) reboot "

---

