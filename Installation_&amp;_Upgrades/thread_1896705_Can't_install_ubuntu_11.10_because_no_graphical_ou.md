---
title: "Can't install ubuntu 11.10 because no graphical output"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by arthur_8200 on 2011-12-17
Hi,


a few weeks ago I tried to install Ubuntu 11.10 amd64 on a
Medion Akoya P5330 D
CPU: Intel® Core i5-2320 3,0 GHz
Video: Geforce GTX 550 Ti (PCIE)


In the first seconds after choosing "Install Ubuntu" I see text output flushing during startup.
But then no new text appears and the output is still only the text - as you can see it here:
[http://666kb.com/i/bzljpg30en2b61bf0.jpg](http://666kb.com/i/bzljpg30en2b61bf0.jpg)
But changing to tty1 (ctrl + alt + f1) does work. I logged in there and tried some gdm restart, changing xorg.conf etc. with no success.

I even tried installing from ubuntu amd64 altnerative but the same error appeared again.


Any help is welcome.

Regards,
Arthur

---

### Post by MAFoElffen on 2011-12-17
> **arthur_8200 said:**
> Hi,


a few weeks ago I tried to install Ubuntu 11.10 amd64 on a
Medion Akoya P5330 D
CPU: Intel® Core i5-2320 3,0 GHz
Video: Geforce GTX 550 Ti (PCIE)


In the first seconds after choosing "Install Ubuntu" I see text output flushing during startup.
But then no new text appears and the output is still only the text - as you can see it here:
[http://666kb.com/i/bzljpg30en2b61bf0.jpg](http://666kb.com/i/bzljpg30en2b61bf0.jpg)
But changing to tty1 (ctrl + alt + f1) does work. I logged in there and tried some gdm restart, changing xorg.conf etc. with no success.

I even tried installing from ubuntu amd64 altnerative but the same error appeared again.


Any help is welcome.

Regards,
Arthur
With that video Card you need to use "nodeset" as a boot option for the LiveCD and after your install, on the first reboot, until you can get the NVidia drivers installed.

For the LiveCD:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Modesetting and the LiveCD]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")**[/SIZE][/COLOR][/SIZE][/COLOR]

For after the install, (It reboots after the install finishes):
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

Then when you get to the desktop, go to System Settings > Additional Drivers... and select the driver That has "recommended" after it. That would most likely be nvidia-current.

Tell me how it goes.

---

### Post by arthur_8200 on 2011-12-17
> **MAFoElffen said:**
> With that video Card you need to use "nodeset" as a boot option for the LiveCD and after your install, on the first reboot, until you can get the NVidia drivers installed.

For the LiveCD:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Modesetting and the LiveCD]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")**[/SIZE][/COLOR][/SIZE][/COLOR]


Hi MAFoElffen,

thank you very much for your explanation! I will try it in a few days.

Did you mean "nomodeset"?

---

### Post by MAFoElffen on 2011-12-18
> **arthur_8200 said:**
> Hi MAFoElffen,

thank you very much for your explanation! I will try it in a few days.

Did you mean "nomodeset"?
Yes. "nomodeset"... fingers weren't listening to my brain.

---

### Post by arthur_8200 on 2011-12-23
> **MAFoElffen said:**
> With that video Card you need to use "nomodeset" as a boot option for the LiveCD and after your install, on the first reboot, until you can get the NVidia drivers installed.

For the LiveCD:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Modesetting and the LiveCD]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")**[/SIZE][/COLOR][/SIZE][/COLOR]

For after the install, (It reboots after the install finishes):
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

Then when you get to the desktop, go to System Settings > Additional Drivers... and select the driver That has "recommended" after it. That would most likely be nvidia-current.

Tell me how it goes.


Hi MAFoElffen,

thank you very much for your help.
Yesterday I installed Ubuntu 11.10 with the nomodeset-trick and it and it works great :-)

The PC with quadcore cpu and ssd harddisk is just awesome fast :biggrin:


Regards,
Arthur

---

