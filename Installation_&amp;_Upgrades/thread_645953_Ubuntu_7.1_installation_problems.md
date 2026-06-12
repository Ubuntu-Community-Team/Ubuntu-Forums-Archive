---
title: "Ubuntu 7.1 installation problems"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by gl72287 on 2007-12-20
I recently tried to upgrade from Windows to Ubuntu, also trying xubuntu. I try to run the live CD on both and after loading the parameters it sits at a blank screen, then about 5 minutes later a warning comes up saying Im running in low graphics mode. I click continue, then it sits at another blank screen with no response, I have let the computer run upwards of an hour with no response. I have tried both versions of the live CD, as well as both versions of the alternate install on both OSes with no response.

Im using an Averatec 3280 Laptop, runs with 512 megabytes of ram.

---

### Post by Pumalite on 2007-12-20
Graphics?

---

### Post by gl72287 on 2007-12-20
The exact specs are listed here on the website:

[http://www.averatec.com/products/portable/thinlight/3200Series.asp](http://www.averatec.com/products/portable/thinlight/3200Series.asp)

---

### Post by Pumalite on 2007-12-20
You probably have integrated graphics. You have to install with the alternate CD and maybe configure your xserver at the end of the intallation. So if after installing with the Alternate, you end up with a blank screen, post back and we'll help you.

---

### Post by gl72287 on 2007-12-20
I will do that tonight and let you know, thanks for your help.

---

### Post by gl72287 on 2007-12-21
Same thing has happened with the ubuntu alternate install, it installs, then boots and I get the unbuntu loading screen, then it again goes to a blank screen.

---

### Post by Pumalite on 2007-12-21
Try to install other distros to see if you are incompatible with Linux in general or Ubuntu in particular.

---

### Post by gl72287 on 2007-12-21
Any you would suggest?

---

### Post by Pumalite on 2007-12-21
LinuxMint 4.0

---

### Post by gl72287 on 2007-12-22
After trying to run LinuxMint4.0 it again results in a blank screen for several minutes, then gives this message:

Ubuntu is running in Low Graphics mode (Even though Im running from the LinuxMint4.0 CD O.o)

Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself.

Then I have an option to always run in low graphics mode, then I have configure, shut down, and continue options. The continue option just again results in a blank screen.

---

### Post by Pumalite on 2007-12-22
At the end of the installation:
sudo dpkg-reconfigure xserver-xorg
This you can probably do with Ubuntu too.
Accept most defaults, choose 'vesa' as the driver. Then: startx

---

### Post by gl72287 on 2007-12-22
Is there an alternate install of Linuxmint available? Because the only versions ive seen are the ones with the live CD.

I will also try this with ubuntu later tonight.

---

### Post by Pumalite on 2007-12-22
I don't know about LinuxMint. Try Ubuntu first. You already have the CD.

---

### Post by gl72287 on 2007-12-23
I have completed the installation, now where is it that I exactly type in the above commands?

---

### Post by Pumalite on 2007-12-23
At the command line.
Ctrl+Alt+F1 to get one if you are faced with a blank screen.

---

### Post by gl72287 on 2007-12-23
Alright, I got into the OS :D

Now as far as setting up wireless, how would I go about that? I use a wireless router at home through a cable modem.

---

### Post by Pumalite on 2007-12-23
Find your solution among these:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[http://ubuntuforums.org/showthread.php?t=586387](http://ubuntuforums.org/showthread.php?t=586387)
[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by gl72287 on 2007-12-23
I actually got it figured out. Thanks for all your help with this. :)

---

### Post by thiebaude on 2007-12-23
Mark your post as solved!

---

### Post by Pumalite on 2007-12-23
> **gl72287 said:**
> I actually got it figured out. Thanks for all your help with this. :)

You are welcome. Good luck!

---

