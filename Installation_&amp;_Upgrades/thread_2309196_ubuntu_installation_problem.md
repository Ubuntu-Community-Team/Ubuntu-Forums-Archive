---
title: "ubuntu installation problem"
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by Akhunbala on 2016-01-08
Hi. I have a p4m89-m7 mohherboard. DDR2, 1500 mb ram and 8 bit standart vga. I can not install ubuntu this PC. error "snd_hda_intel  CORB reset timeout" and after one minut come black screen. what can I do it? please help me

.

---

### Post by kansasnoob on 2016-01-10
It looks like that may have VIA P4M800 graphics:

[http://www.biostar-usa.com/mbdownloads.asp?model=p4m80-m7](http://www.biostar-usa.com/mbdownloads.asp?model=p4m80-m7)

If so Ubuntu will not run on that hardware but either Lubuntu or Xubuntu should. That said I've found Trusty (14.04) to be much more stable and suitable for older hardware than Wily (15.10). I prefer using the 14.04.1 versions to avoid [HWE EOL]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support"):

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

[http://cdimage.ubuntu.com/xubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/14.04/release/)

You'll notice that those links include downloads for 14.04, 14.04.1, 14.04.2, and 14.04.3. I prefer using the 14.04.1 versions to avoid the aforementioned HWE EOL, but if you're dual booting you should be aware of this nasty bug in the 14.04.1 installer:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Besides being more stable Lubuntu and Xubuntu Trusty are also supported until April 2017 whereas the Wily (15.10) versions are only supported until July 2016. 

Another option is to install [Ubuntu 14.04.1]("http://old-releases.ubuntu.com/releases/14.04.2/") selecting Install from [the advanced boot menu]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options") and then be certain NOT to select auto-login during installation. Then after installing you can access the terminal from the login screen (Ctrl+Alt+F1), install 'gnome-panel' (sudo apt-get install gnome-panel), reboot (sudo reboot), and then select the [flashback w/metacity session]("http://ubuntuforums.org/showthread.php?t=2220264") at login.

While that latter option is a bit more complex than simply installing either Lubuntu or Xubuntu the flashback w/metacity session is used by Edubuntu for its LTSP installs and the Trusty version is supported until April 2019. I've done that on a number of older machines because the added two years of support is important to me :D

One other heads-up, in case you didn't know that hardware will require the i386 (32 bit) version rather than the amd64 (64 bit version) regardless of which flavor you choose.

---

### Post by Akhunbala on 2016-01-10
I intallaled lubuntu, xubuntdu, mageia, but have same problem . But linux mint installed correctly

---

### Post by kansasnoob on 2016-01-10
> **Akhunbala said:**
> I intallaled lubuntu, xubuntdu, mageia, but have same problem . But linux mint installed correctly

Probably because Mint is based only on Ubuntu's LTS versions, currently 14.04:

[http://www.webupd8.org/2014/05/confirmed-next-3-linux-mint-releases.html](http://www.webupd8.org/2014/05/confirmed-next-3-linux-mint-releases.html)

They don't even mess with the interim versions like 14.10, 15.04, or 15.10 anymore.

---

