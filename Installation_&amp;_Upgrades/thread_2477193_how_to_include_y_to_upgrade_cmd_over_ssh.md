---
title: "how to include y to upgrade cmd over ssh"
date: 2022-07-17
forum: Installation &amp; Upgrades
---

### Post by buill on 2022-07-17
Hi I use a phone to control an Ubuntu laptop in my kitchen but from time to time i need to upgrade it so i ssh 
[COLOR=#067d17]"export DISPLAY=:0.0 [/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17] sudo apt update & sudo apt upgrade[/COLOR][COLOR=#0037a6]\n [/COLOR]password[COLOR=#0037a6]\n[/COLOR][COLOR=#067d17] y[/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"

the update and upgrade works fine but at the y gets sent at the same time not after upgrade has finished, and you are prompted y/n 

anyone know how to fix this?

thanks buill
[/COLOR]

---

### Post by deadflowr on 2022-07-17
```
apt upgrade -y
```
Though I don't know why you are exporting the display as command line does not need it.

---

### Post by buill on 2022-07-17
thanks yeah got working by 
[COLOR=#067d17]"sudo apt update & sudo apt -y upgrade[/COLOR][COLOR=#0037a6]\n[/COLOR]password[COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"

the reason i was exporting display was i wanted to open a visible terminal and see the updating on remote screen so i would know when finished as the remote ubuntu is controls my tv in the living room


echo didint do the job 
[/COLOR]

---

