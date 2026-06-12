---
title: "Moved HD to new computer, now have GUI startup issues"
date: 2020-06-01
forum: Installation &amp; Upgrades
---

### Post by pmowry911 on 2020-06-01
Good day,
  After a power outage I had a PC with a discrete video card die so I move the HD over to a PC with an Intel i5 with integrated video.  The original pc had both nvidia and an amd card in it at some point.

The behavior I have now is tty1 opens to a blank screen with a cursor flashing in the top left.  if I switch to tty5 to login, it is pulled back to tty1 pretty quickly.  I can SSH in I dont really know were to look for logs to troubleshoot.  Based off of web searches I've tried :
sudo apt-get remove amdgpu-pro
sudo dpkg-reconfigure gdm3
sudo apt-get remove xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-intel
sudo apt-get purge xserver-xorg-amdgpu*

cd /usr/share/X11/xorg.conf.d/
  sudo mv 10-amdgpu.conf  ~/
  sudo mv 10-radeon.conf ~/
  sudo mv nvidia-drm-outputclass-ubuntu.conf ~/

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

sudo apt-get install -reinstall gdm3 gnome-shell
sudo apt-get install --reinstall gdm3 gnome-shell

where do i go to troubleshoot this boot problem I assume is caused by the change in video card even though the whole machine changed. 

Thank you,

Edit: Forgot to mention that I had upgraded to 20.04.  Pretty sure that gdm3 is in charge, but i donr see logs for it and I dont know if/how X11 or Wayland are involved with a normal install.

---

### Post by pmowry911 on 2020-06-18
Update:  My problem was a problem with no access to the password for autologin causing a loop.  Turned autologin off and i was working at 640x480.  Put the nvidia drivers back and I'm all good.  Well, except for the dead power supply in the original system

---

