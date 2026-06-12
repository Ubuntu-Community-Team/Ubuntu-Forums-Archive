---
title: "Update to Feisty and propetiary ATI drivers."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by DoktorNo on 2007-04-21
Hi there,

I have installed fglrx ATI propetiary drivers for my Radeon 9250 graphic adapter on my current Edgy box. Would be there any problem with them after upgrading to Feisty?

---

### Post by spin2cool on 2007-04-21
The drivers should work fine.  If you want to get the latest version, you can check out Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Crosbie on 2007-04-21
The drivers will likely work, though you may need to tweak some other settings.  I needed to tweak my gdm.conf-custom file in order to get the display to work correctly.  Be ready to do some little fixes with any customisation, especially proprietary ones, is what I've learned. :)

---

### Post by jiminycricket on 2007-04-21
X might not start on reboot--don't worry.  You'll need to do 'sudo dpkg-reconfigure xserver-xorg', and select the vesa driver.  If that still doesn't work, install the fglrx driver fwith this thread: [http://ubuntuforums.org/showthread.php?t=416509](http://ubuntuforums.org/showthread.php?t=416509)

---

