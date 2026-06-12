---
title: "My solution to install 10.04 on laptop with nVidia G102M CUDA"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by jeecol on 2010-05-04
Hi everyone, 

As as ubuntu user, I really hate this problem. Now I would like share my experiences to solve this trouble.

Syndrome: The Ubuntu 10.04 laking F4--save graphic mode, thus when booting from live-CD,  no GUI appears (but the control+alter+F3 works to switch to terminal mode)

Computer: ASUS K50IN with nVidia G102M

My solution: 

1. Download alternate CD and install it into laptop (comparing to normal CD, it took longer to install, I did not know why!!).

2. After installating and rebooting (now GUI), switch to terminal mode (e.g. control + alter + F4)

3. Install drivers: sudo apt-get install nvidia-185*  and then I can can the screen at 800*600 (low resolution)

note: when I used 9.10, I found the proprietary driver is nvidia-185, that's why I suggestion this.

4. Install one more driver: sudo apt-get install nvidia-glx-185  and then the screen should be at correct resolution. 

I am not an advanced user of ubuntu, but the above way did work to solve this trouble. If you cannot solve it, my not-smart suggestion is: sudo apt-get install nvidia-* (to install all nvidia drivers)

As some bug reports, the xserver-xorg-video-nouveau did not work for this laptop. Some other suggestions from webs, like to install nvidia driver 190.42. Actually, I could not find this version of driver even I followed the instructions to add PPA to source list.


OK good luck guys!

---

