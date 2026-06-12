---
title: "11-04, Nvidia driver 173.14.xx and Unity desktop, Legacy card support"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by IPEX-731BA5DD06 on 2011-06-15
Solution to all 3 problems.

11.04 Install as per usual, you can operate multiple distribution on same home partition, see**_[COLOR=Red] [ This link for solution]("http://ubuntuforums.org/showthread.php?t=1739675")[/COLOR]_ **

Boot into the Low resolution desktop with basic support.

No don't update as yet, Open terminal window Cntl-Alt-T

Commands entered;

Sudo apt-get install unity-2d ( or 3d if you have the graphics card and power)
sudo gdm desktop.

Now you have a 2d Unity desktop, for non uber systems, Now you can install all updates, don't forget to add Authorisation for some programs such as Wine.

Nvidia driver 173.14.xx will show as installed but not operational. Open X-server, click on System information, and it'll show the driver as NVIDIA Driver Version 173.14.(latest released driver or 30)

Now are you using 173.14.22 yes and no, 

yes you using Nvidia driver, but 
no as in its using a more _**RECENT**_ version that's been updated.

If using legacy 93.xx.xx I really don't know.

If you using a later Driver for Nvidia, why are you reading this????

---

