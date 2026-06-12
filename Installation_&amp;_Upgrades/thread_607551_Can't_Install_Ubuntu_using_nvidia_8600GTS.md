---
title: "Can't Install Ubuntu using nvidia 8600GTS"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by psycho5 on 2007-11-09
I'm trying to do a fresh install of Ubuntu 7.10 Using LiveCD but as soon as I hit Start/install ubuntu in safe graphics or in normal mode, my screen goes blank. 

I had the same problem while I was running on my onboard graphics  and decided to switch to the pci-ex but ubuntu wouldn't boot up without making my screen go blank, so i decided to do a fresh install hoping to solve it. 

I tried Using Envy, automatic and manual install but still it wouldn't pick up my card upon boot. 

As of now, I installed windows to check if the card itself had any physical problems, but none, the card works fine. 

I read this thread already [http://ubuntuforums.org/showthread.php?t=556195](http://ubuntuforums.org/showthread.php?t=556195) but I don't understand whats going on in there, I am trying to do a fresh install all over. Ty for your help! 

My system :

Syncmaster 763MB
Amd 64 3600+
M2A-VN Asus Motherboard 
Onboard Ati x1250 
Nvidia 8600GTS
1 Gig RAM

---

### Post by bulldog on 2007-11-09
In your case I should use the alternate cd and install your graphics when the install is done.
I have a 8800GTS 640 and no problems with the card.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Hit the green box at the bottom and here you go.

Edit:
One other thing.
Did you disable the onboard graphics in the BIOS?

---

### Post by Pumalite on 2007-11-09
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

---

### Post by psycho5 on 2007-11-09
Yes, I did disable the Onboard graphics on my bios. 

Ty for the tips and links. I'll try installing from a different method.

---

### Post by Pumalite on 2007-11-09
Get in Recovery and install nvidia-glx-new

---

### Post by psycho5 on 2007-11-09
Let me know if I'm going in the right direction here:

A) I'm downloading the Alternate CD, and using the Installation/FromWindows Method. 

After that, if its successful, I'm going to boot and follow these steps :

B) Get in Recovery and install nvidia-glx-new

If that doesn't work then i'm going to do this: 

C) How to fix nvidia acceleration in Fiesty. (Hopefully it also works for Gutsy)

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

---

### Post by makeyre on 2007-11-15
I have no network support with this mainboard so I can't install restricted drivers, and it won't boot normally.

[http://ubuntuforums.org/showthread.php?t=609491](http://ubuntuforums.org/showthread.php?t=609491)

---

