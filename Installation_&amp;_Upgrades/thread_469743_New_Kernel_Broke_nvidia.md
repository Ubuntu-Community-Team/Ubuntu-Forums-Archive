---
title: "New Kernel Broke nvidia"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by ART_Adventures on 2007-06-10
Hello People,

Ubuntu Feisty 15 downloaded the new kernel 16, and now on restart it says it cannot startx. Originally I installed nvidia drivers via the restricted drivers manager. But now, kernel 16 says it cannot startx. I booted into recovery mode and typed dpkg-reconfigure xserver-xorg. Since I don't know the settings, I accepted all the defaults. Now it boots into 16 fine, but not with the nvidia drivers enabled (it uses VESA) and the restricted drivers manager in 16 says it can find no hardware to install drivers for.

I would like to reinstall my nvidia drivers which it annoyingly broke for me. Can anybody help me?

Thanks.

---

### Post by calraith on 2007-06-10
What kind of nVidia card do you have?

---

### Post by ART_Adventures on 2007-06-10
nvidia  GeForce 6500

---

### Post by calraith on 2007-06-10
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get remove nvidia-glx
sudo apt-get install nvidia-glx-new nvidia-kernel-common
```Then modify /etc/X11/xorg.conf so that driver "nvidia" loads, rather than driver "nv".  Does that help?

If not, you might also try downloading and running Envy from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) .  Envy automates the installation of the nVidia driver.

---

### Post by ART_Adventures on 2007-06-10
Thank you very much. I tried Envy and now it works :-)

---

