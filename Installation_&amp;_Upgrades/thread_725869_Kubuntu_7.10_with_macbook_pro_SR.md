---
title: "Kubuntu 7.10 with macbook pro SR"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by jerrygdm on 2008-03-16
I follow instruction in this forum and in the wiki for installing kubuntu 7.10 but after the initial screen when it prompts "start and install kubuntu" I can see the 100% bar complete and after the screen become black, I heard the cd spinning but the screen is totally black. What I have to do?

PS: I have the june 2007 SR Macbook Pro with 2.4ghz

---

### Post by Pumalite on 2008-03-16
What graphics do you have?

---

### Post by jerrygdm on 2008-03-16
nvidia 8600gt m

before I was able to install it correctly...

the other problem is: I follow some guides for connect with wifi wpa-psk I was able to associate withe my access point but I can't surf on the web and enter in the configuration page of the router (i can ping google for example)...

an other question I have to let the nvidia drivers installed or I have to update it with new one to run compiz?


Thanks...

---

### Post by Pumalite on 2008-03-16
At the blank screen, try:
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver
Then: startx

---

### Post by jerrygdm on 2008-03-16
As I wrote I can successfully install kubuntu but I have some more prloblems with wifi...

---

### Post by Pumalite on 2008-03-16
If you made the Nvidia 8600 GT work for you, you are fine. As for wireless; what's your card?

---

### Post by jerrygdm on 2008-03-16
atheros....I follow some guides and it can associate with access point and can ping some internet address like [www.google.com](www.google.com) but I can not surf with konqueror for example...

---

### Post by Pumalite on 2008-03-16
This might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

---

