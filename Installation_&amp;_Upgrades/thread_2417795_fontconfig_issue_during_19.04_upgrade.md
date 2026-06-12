---
title: "fontconfig issue during 19.04 upgrade"
date: 2019-04-27
forum: Installation &amp; Upgrades
---

### Post by amirian on 2019-04-27
I've currently upgraded to Ubuntu 19.04 from 18.10 LTS but stopped at a stage with an error from fontconfig. The x session now doesn't work. I tried many ways such as even purging fontconfig and all its dependencies and reinstalling ubuntu-desktop having it's name followed by:^ but the problem remains. The log file of fontconfig contains: 
"fc-cache: symbol lookup error: /usr/lib/x86_64-linux-gnu/libfontconfig.so.1: undefined symbol: FT_Done_MM_Var"
Surfing the web I guess this is caused by freetype2 which I installed in the past with difficulties and I don't know how to even uninstall it now! Any solution for having a clean Ubuntu with my files and settings safe?

---

### Post by dino99 on 2019-04-27
if you cant get a gui now, then you might opt to a fresh install, its quicker than fighting against ghost. But you can first cleaning the system via :
> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get -y install
sudo dpkg --configure -a

---

### Post by amirian on 2019-04-27
> **dino99 said:**
> if you cant get a gui now, then you might opt to a fresh install, its quicker than fighting against ghost. But you can first cleaning the system via :

What do you mean by fresh install? The total os or just the GUI? I should save my files and programs and I don't know how to fresh install the GUI. Moreover, among your 6 proposed command lines, the 3rd, 5th and 6th commands come with the same error of fontconfig.
I tried Installing fontconfig:i386 and fontconfig-config:i386 and got no error but the past commands re-need fontconfig:amd64. I downloaded and installed libfontconfig1-dev_2.13.1-2ubuntu2_amd64.deb but the problem with FT_Done_MM_Var remains.
Tired of trying several solutions, a fresh GUI installation is perfect if possible

---

### Post by amirian on 2019-04-28
> **dino99 said:**
> if you cant get a gui now, then you might opt to a fresh install, its quicker than fighting against ghost. But you can first cleaning the system via :

I finally succeeded uninstalling the dirty freetype2 and running all your 6 commands successfully. What's the next step? The x session now can show the background but I have previously uninstalled fontconfig and all its dependencies with the command: sudo apt-get purge --autoremove fontconfig

---

