---
title: "HOWTO: Installing Ubuntu 7.10 on Dell Inspiron 1100"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by LennoxRock on 2007-12-27
I know that installing Ubuntu on this Dell has been a headache ever since I first installed edgy.  In mucking around with it, I have gotten a pretty simple, quick method that seems to work well.

First off, I highly recommend using the alternate desktop cd, as you will be able to install without having to deal with the display issues until later.  I'm not going to get into the actual installation process, as this guide assumes you are able to actually get the OS installed with the alternate CD

Once you've installed Ubuntu and you reboot, press Escape at the GRUB loader (it's the screen right after your bios initializes).  Select the recovery mode (should be the second option).  

This should take you to the command prompt as root.  From here type in

```
# dpkg-reconfigure xserver-xorg
```

This takes you to a series of setup questions regarding your keyboard, mouse, and video settings. 

1. Answer NO to autodetect video hardware

2. Select i810 from the list of drivers.

3. Hit enter for the default identifier

4. Make sure the Video card's bus identifier reads "PCI:0:2:0" (without the quotes).  This should already be the default.

5. Leave the memory question blank and hit enter.

6. Select NO on the kernel framebuffer interface question.

7. Answer the keyboard and mouse questions (use your common sense here) =p

8. Select YES on the question about writing the default Files section to configuration file.

9. Select NO to autodetect monitor.

10. Hit enter for the default identifier.

11. Select 1024x768, 800x600, and 640x480

12. Select ADVANCED method for selecting monitor characteristics.

13. Enter "31.5-48.5" (without the quotes) for the horizontal sync.

14. Enter "59.0-75.0" (again, without the quotes) for the vertical refresh.

15. Answer YES to the next question.

16. Select 24 for default color depth.


And you're DONE!!!

After this type 
```
# reboot
```

And you should reboot into your nice, working Ubuntu installation.  Enjoy!

---

