---
title: "Emachines Desktop Problems"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by shaddy on 2008-04-21
Hi, I have an Emachines computer (refurbished) and Windows Vista (sadly).  I downloaded Ubuntu 7.10 and made a Live CD, but when I boot using it and select the option to run Ubuntu from the disk, it screws up... It starts printing a few lines on a black screen, then the display flickers for a bit and occasionally I'll see oddly coloured bands or messed up looking versions of the Ubuntu logo (crazy pixely colours) and then it'll bring me to a blue screen tha says that my display has been turned off 6 times within the past 2 mintutes. From there I press OK and it does the same thing over until I turn off my computer. I've used this Live CD to install Ubuntu on a different computer so I know it does work, but it won't on my Emachines desktop computer. Also, even if I try this in "Safe Graphics Mode" or any other option that runs the Live CD it still messes up.
I have a 3.2GHz Pentium 4 single-core processor, 1.5GB of RAM, and an ATI X1600 graphics card. I'm assuming that the graphics card is conflicting with Ubuntu, but I'm not sure. Thanks for any advice!

---

### Post by phidia on 2008-04-21
Take a look at the 1st post [here]("http://ubuntuforums.org/showthread.php?t=515573").
You can try and get a CLI to work in, when X fails to start, by pressing the Alt+Ctrl+F1 keys and then type sudo dpkg-reconfigure xserver-xorg or if you have internet working you might try to use apt-get to install the fglrx driver. Hope that helps.

---

### Post by shaddy on 2008-04-22
I tried all that and then I was back at the screen where I pressed Ctrl + Alt + F1 to get to and I don't know what to type to make it keep loading from the Live CD and continue on like it would have....

---

