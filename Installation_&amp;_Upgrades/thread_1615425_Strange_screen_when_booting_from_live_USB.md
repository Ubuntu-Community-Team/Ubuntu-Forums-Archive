---
title: "Strange screen when booting from live USB"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by theonlygreat on 2010-11-07
I am trying to run Ubuntu from a live USB, everything seems to be great until I get to the part where the GUI should come up. Then I get this screen
[IMG]http://i858.photobucket.com/albums/ab141/theonlygreat/2010-10-30_07-57-56_761.jpg[/IMG]
It's a little hard to see, but it's basically a white bar at the top and black underneath. The black is flickering a lot and the flickering can stay for a short while (30-120 seconds) even after I have rebooted into windows. Sometimes the bar at the top is another solid color (purple,blue, orange, usually white though), I think it is putting my monitor in a strange version of it's self test. When it is unplugged the monitor while cycle through full screens of different colors. 

I have tried Ubuntu 10.10 Desktop AMD64, 10.10 i386, and the latest Fedora to see if another distro had different results. I have also tried 2 other USB drives. I am using Universal USB Installer 1.8.0.8 to make the drives. My own searches have found some problems with graphic drivers for the GeForce 8800 GTX, but they a bit dated. I have tried adding vga=vesa to the boot arguments, I am not sure if I did it right or not, but it resulted in a black screen with a blinking line instead and no flickering.

System specs:
AMD Phenom II 740BE (unlocked to Quad Core @ 3.4Ghz)
ASRock Extreme3 870
WD Caviar Black 640GB 7200RPM 6.0Gb/s
GSkill 4GB PC1600
GeForce 8800 GTX
Dell 3007WFP

---

### Post by Quackers on 2010-11-07
Have you tried "nomodeset" as a boot argument? (Without the quotes)

---

