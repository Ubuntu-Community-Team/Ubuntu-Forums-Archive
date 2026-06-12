---
title: "Request for Ubuntu CDRom to install package"
date: 2021-05-15
forum: Installation &amp; Upgrades
---

### Post by Automat2 on 2021-05-15
Hello,

I just upgraded to Hirsute from Groovy, used a USB memory stick and made a clean install.

Ubuntu is my PC native OS.

I have tried installing gdebi package through Terminal ```
sudo apt install gdebi
```.

It has started the installation but I had to abort it because this message has appeared: 
> Do you want to continue? [y/n] y
Media change: please insert disc labeled 'Ubuntu 21.04_Hirsute Hippo_ - Release amd64 (20210420) in the drive '/cdrom/' and press [Enter]

I don't have a CD -I installed Hirsute through a USB memory stick! And I have some 400GB still unused in the HDD and 1.5TB free in another external HDD.

Does anybody know what is happening and how to sort it?

Thanks.

---

### Post by mikewhatever on 2021-05-15
Nothing is happenning, no need to panic. You need to remove the CD-ROM entry from the available sources.
There is a GUI for that, as shown in the picture below.

[https://i.stack.imgur.com/iC2SL.png](https://i.stack.imgur.com/iC2SL.png)

---

### Post by Automat2 on 2021-05-15
Thank you. :P

I had installed a previous distro through the same USB but I don't remember unticking the source -or maybe I had done as the installation had finished without giving it too much of a thought.

---

