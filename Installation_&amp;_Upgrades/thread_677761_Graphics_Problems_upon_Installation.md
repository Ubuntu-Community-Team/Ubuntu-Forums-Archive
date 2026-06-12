---
title: "Graphics Problems upon Installation"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by paulroberts20 on 2008-01-25
Having a little trouble with my graphics..

(i've got an NVIDIA GeForce 7600 GS)

boot off the live cd, get splash, get desktop, everything's fine :)

but after installation, i reboot off HDD and splash doesn't appear
(montior says input is 1280x1024, which my monitor can't display - only goes up to 1024x768 )

after splash, I get a white screen (logon screen) so I have to type my username and password in blind, but get pale orange background colour (normal) and when wallpaper image appears, it's all garbled with parts of the dialog box from the installation mixed in with it
(will try to get a screenshot up)

I can just make out the top and bottom dock/panel bars, but can't click on anything and have to hard shutdown.

i've tried downloading NVIDIA restriced driver while on LiveCD, but needs system reboot to complete..

---

### Post by overdrank on 2008-01-25
> **paulroberts20 said:**
> Having a little trouble with my graphics..

(i've got an NVIDIA GeForce 7600 GS)

boot off the live cd, get splash, get desktop, everything's fine :)

but after installation, i reboot off HDD and splash doesn't appear
(montior says input is 1280x1024, which my monitor can't display - only goes up to 1024x768 )

after splash, I get a white screen (logon screen) so I have to type my username and password in blind, but get pale orange background colour (normal) and when wallpaper image appears, it's all garbled with parts of the dialog box from the installation mixed in with it
(will try to get a screenshot up)

I can just make out the top and bottom dock/panel bars, but can't click on anything and have to hard shutdown.

i've tried downloading NVIDIA restriced driver while on LiveCD, but needs system reboot to complete..

Hi when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` or startx. Hope this helps and good luck!

---

