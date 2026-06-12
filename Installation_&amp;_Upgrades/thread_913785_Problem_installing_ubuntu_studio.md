---
title: "Problem installing ubuntu studio"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by PamelaPopo on 2008-09-08
Hi, i am relatively new to ubuntu but quite interested in ubuntu studio. I downloaded the iso file, freed some space on my hard drive, and sort of installed ubuntu studio. the installation process went well for the most part, except that no connection was found. 
My problem is that ubuntu doesn't start properly. when i choose ubuntu in GRUB, i get a few lines in DOS, then i'm asked to log in, and when i do, i get a line saying :
pierre@ubuntu:§ (or something close, pierre being my name)
I never get the expected graphical interface. could someone please help me fix this? Did i do something wrong during the installation? And if i did, can i remove what i've installed and give it another try? 
Thanks!

---

### Post by Partyboi2 on 2008-09-08
When you got to[[COLOR=Blue] this part[/COLOR]]("http://news.softpedia.com/images/reviews/large/ubuntustudio-large_022.png") of the installation did you select to install the ubuntu studio desktop? If not then you can install it from the terminal. After you have logged an see
```
pierre@ubuntu
```type
```
sudo apt-get install ubuntustudio-desktop 
```If you didn't install the other options you can install them as well with:
```
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

---

### Post by PamelaPopo on 2008-09-08
I don't think i've installed anything but the audio package actually... I can't try it right now but your answer seems very much sensible. thanks a lot for this quick reply!

---

### Post by PamelaPopo on 2008-09-08
Hi, sorry it didn't work. Looks like it's only looking on the HD to find the components to install, and not on the DVD. How can i get it to search the DVD instead? thank you!

---

### Post by Partyboi2 on 2008-09-09
Stick the cd in the cdrom and try[FONT=monospace]
[/FONT]```
sudo apt-cdrom add
sudo apt-get update
```then try installing the packages with the above commands.

---

### Post by PamelaPopo on 2008-09-12
Hi, it didn't work... everything got installed, but whenever i try to boot from ubuntu studio I get weird lines and colors, then a black screen and my pc is frozen. I tried to install Hardy a few weeks ago and it was working fine. Should i try to upgrade to Studio from a working Hardy? 
Thanks!

---

### Post by Partyboi2 on 2008-09-12
Yeah, that sounds like a good idea. 

[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy)

---

