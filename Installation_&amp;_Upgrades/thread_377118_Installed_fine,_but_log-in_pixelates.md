---
title: "Installed fine, but log-in pixelates"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by TheOne0908 on 2007-03-05
I installed the alternate AMD64-bit Ubuntu 6.10 CD and everything went great.  I was able to reboot and use the multi-boot interface to launch Ubuntu Edy 6.10.  I am able to log-in with my username and password, but when the small little ubuntu/gnome load screen pops up in the middle of the screen after that, it appears distorted.  The pixels in the image go crazy.  If I stay in the log-in screen and don't log in and hit my options menu.  It will popped up the normal submenu, but if I click on of the sub-options, the sub-option will appear in the center of my screen, also, distorted pixels.  It ends up locking the whole computer and I have to restart my machine.  Any thoughts on what the issue might be?  I have an AMD 4000+, 7800GT's in Sli(Which I disabled, but the problem still remains), Asus Sli Deluxe motherboard.

---

### Post by carlosfocker on 2007-03-30
Have you installed the NVIDIA drivers. If not use Envy since its extremely easy. 

1. Download the deb [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb)

2. Install the deb package

```
sudo dpkg -i envy_0.9.1-0ubuntu4_all.deb
```
if you get an error about dependicies type this then run teh dpkg command agian
```
sudo apt-get install -f
```

3. Type** sudo envy** this in a terminal or goto your Applications/System Tools to the Envy Icon (This is preferred) and follow the menu to install nvidia Drivers.

Post back if this doesnt help.

---

