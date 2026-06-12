---
title: "ATI / X server install problem fix!!!"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by hemes on 2006-06-28
Hi,

Last night I finally got ubuntu installed and running after having video driver related problems with multiple distributions.  I thought I would share what I did to help others with the same issues.

I have a AMD 3800+ X2 with a ATI x800GTO video card.  This was tested on the i386 install.

**While trying to run the live CD, I kept getting the error: "failed to start X server..."**  There are two work-arounds I discovered.  The first will allow you to run the  live CD to test things out and let you (hopefully) install graphically.  The second involves a text install followed by installing the ATI graphics drivers.

**_Fix 1:_**
After receiving the error message you are placed back at the prompt.  Run the following code to install the ATI graphics drivers.

[B]     sudo apt-get update
     sudo apt-get install linux-restricted-modules-$(uname -r)
     sudo apt-get install xorg-driver-fglrx
     sudo depmod -a[/B]

These next two lines will updated your xorg.conf file to use the new driver

[B]     sudo aticonfig --initial
     sudo aticonfig --overlay-type=Xv[/B]

Finally we want to apply the setting without rebooting (erasing our progress).  Run these last two lines

[B]     sudo telinit 1
     sudo telinit 2[/B]

If all goes well ubuntu should restart and you will be greeted with the welcome screen and maybe sound.

[For me the graphical install did not work.  It initialized, asked me the questions, and started; but it would repeatedly hang on 15%.  I found two others that had the same problem fixed with a text install (see Fix 2)]

**_Fix 2:_**
This second fix (what I used) involves a text install with the same process as above.  Get the alternate install from the ubuntu website and boot from it.  After the install it X server will cry and you will find yourself again at the prompt.  Type the following code to install the ATI drivers and edit xorg.conf
[B]
     sudo apt-get update
     sudo apt-get install linux-restricted-modules-$(uname -r)
     sudo apt-get install xorg-driver-fglrx
     sudo depmod -a
     sudo aticonfig --initial
     sudo aticonfig --overlay-type=Xv[/B]

Reboot and smile as ubuntu starts graphically!!  :)

Sources:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30284](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30284)
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_driver](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_driver)

---

