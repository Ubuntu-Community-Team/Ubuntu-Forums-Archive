---
title: "Ubuntu installation fails on desktop pc"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by Shallowmist on 2011-11-01
I am trying to install Ubuntu on my mother's computer since i have it installed on the rest of the 8 computers/laptops however i always hit a road block with it if you will. I've tried with every version since 10.04 till 11.10.
I start the installation through a cd/usb tried both any way i get the ubuntu menu 

boot from live cd
install ubuntu on hard drive etc

So i check the install ubuntu on hard drive than it starts loading and the screen goes blank. However it doesn't return to normal so that the installation could continue it just stays black i've tried waiting for it for an hour on end nothing happens and i am forced to restart. However the live boot does work.

Computer specifications are (not exactly sure about the CPU since i've build it a long time ago.

Athlon 64x 3GHZ dual core (not sure about the model name any more)
Ram: Basic 667 DDR2 3GB 2 sticks of 512 and 1 stick of 1024
Video card: Nvidia GTS8800
Motherbord is either:Asus M3N78-VM or a cheap Asrock again gotta check the model name)
2 Drives one Western Digital 160GB normal SATA drive and 1T Sata Western Digital Caviar Green. I am trying to install ubuntu on the caviar green.

Also the computer is running Windows 7 32BIT Professional as dual . However the windows it self is installed on the 160GB drive. I have also attempted to install it right after fresh format same story.

---

### Post by Hakunka-Matata on 2011-11-01
Hi, Welcome to the forums;

Boot to a liveCD/USB, instead of choosing install on first menu, choose "Try Ubuntu without installing".  Once booted up, run this code and post results:
```
sudo fdisk -l && sudo sfdisk -luS
```

---

### Post by Shallowmist on 2011-11-03
Actually i think i am going to first try with Kubuntu or Mint maybe they might load. Problem is i can't right now cause mother keeps being busy during the week :S

---

### Post by Quackers on 2011-11-03
You may need to use a boot option such as nomodeset, with your graphics card.
Details below
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

