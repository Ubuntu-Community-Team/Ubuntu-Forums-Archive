---
title: "/dev/sda7: clean. XXX/XXX files, XXX/XXX blocks"
date: 2018-06-23
forum: Installation &amp; Upgrades
---

### Post by arghavanmh on 2018-06-23
Hi

I must say, I have searched this message in google and tried various solutions given. With no results, I have to ask here, hoping that someone could help me to solve this issue.
I installed boost and did ```
sudo apt-get update
``` and everything was fine. After some minutes, my gedit stopped working, so I tried to restart my system. However, my Ubuntu did not boot any more. 
It first printed lots of messages and stuck at this one:
> Started Update UTMP about System Boot/Shutdown

I have access to both recovery mode and tty. I tried these commands in both of them:
First I tried:
```
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel
```
I got the same messages...
I tried this solution to reinstall default graphics:
```
sudo apt-get purge nvidia-*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf
```
After this those messages disappeared and it stucked at :
> /dev/sda7: clean. XXX/XXX files, XXX/XXX blocks

I tried so many solutions by searching on google but couldn't solve the issue. I would be appreciative if one could help me, please.](*,)

---

