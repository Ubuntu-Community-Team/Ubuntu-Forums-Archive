---
title: "I cant install Nvidia Drivers!"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by psyboy55 on 2009-12-12
I have a nvidia geforce 9800 gtx+ made by sparkle and i cant seem to get the drivers working in ubuntu. it cannot find my graphics card under restricted driver manager. and when i run Nvidia settings it gives me an error saying im not running Xserver and i need to start it with root. i try the command that they give me and it doesn't change the error! This is super annoying because for some reason the resolution is getting lowered so everything looks all messed up! 

I used this tutorial and i got no errors until i ran nvidia settings
It almost seems like the tutorial did nothing! even though i followed it excatly!
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

note im running 32 bit ubuntu. Im running 8.04 and im trying to upgrade to see if that will fix the problem

---

### Post by darkod on 2009-12-12
I've found that EnvyNG package is great for video drivers. If you only have command prompt (but with internet), try to execute:
sudo apt-get install envyng-core envyng-qt

Start it in text mode with:
envyng -t

Select Nvidia and it will download a driver itself. I never removed the current one, the menu will give you that option. After the driver is downloaded and installed, reboot and see if it worked.

You can also try this by selecting the recovery mode entry in the grub menu, not the normal one. In the next menu choose something like "root with networking" to have internet access.

---

### Post by Shazaam on 2009-12-12
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)
Wow! A post not updated since 2005. j/k (just kidding).
Seriously, if (and when) you get Ubuntu upgraded there are quite a few newer posts reguarding video drivers.
If you upgrade to Karmic the default place to go is System>Administration>Hardware Drivers. This is basically the old "Restricted Drivers" entry. This will download and install drivers from the Ubuntu repositories. If you want to install drivers from the nvidia website PLEASE search the forums on how to install them. Different people have found multiple ways to get them installed correctly.

---

### Post by psyboy55 on 2009-12-12
I tried Envy but it couldn't detect my hardware. So if i upgrade to 9.10 my drivers should show up?

Also, if i wanted to try to manually install with envy what driver do i pick? there all just numbers!

---

### Post by Shazaam on 2009-12-12
The one I am using is the 190.42 drivers from the nvidia site. The ones you would want depend on your video card. Check here for the latest stable drivers...
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by realzippy on 2009-12-12
The 190.42 is "your" driver....
Also running a 9800 GTX on 8.10 and 9.10 here,strange that 8.04 won't "detect" your videohardware...what does:

[B]lspci | grep VGA
[/B]

say?Should return something like:

*01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX] (rev a2)*


Edit:

"*It almost seems like the tutorial did nothing! even though i followed it excatly!*"

this might be a problem,if you* exactly* did what alberto said 4 years ago..e.g. the
NVIDIA-Linux-x86-1.0-7667-pkg2.run instead of 183.x/190.42 won't run your card.If above given command returns something similar,please download this driver 

[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run&lang=us&type=GeForce)

to your Desktop.
To install run in terminal:

**sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**

then logout,press *alt+ctrl+F2*,log in at shell.Then:

**sudo /etc/init.d/gdm stop**

[B]cd Desktop
[/B]
**sudo sh NVIDIA-Linux-x86-190.42-pkg1.run**  (Use "TAB" after typing *sudo sh NV* to autocomplete command to NVIDIAnumbersbla.run)  

"*yes*" to all asked questions during installation,then:

**sudo reboot**

---

### Post by psyboy55 on 2009-12-12
3 things.
First i did the lspci thing and it returned how u said it would EXCEPT it sad unknown devive instead of 900 gtx. 

Second when i try to do the envy thing the driver u told me was not in the manual options!

third when i was following the tutorial i did use the package u said not the older one

---

### Post by wojox on 2009-12-12
[More updated version.]("http://ubuntuforums.org/showthread.php?t=1125400")

---

### Post by realzippy on 2009-12-12
> **psyboy55 said:**
> 3 things.
First i did the lspci thing and it returned how u said it would EXCEPT it sad unknown devive instead of 900 gtx. 

Second when i try to do the envy thing the driver u told me was not in the manual options!

third when i was following the tutorial i did use the package u said not the older one

I did not want you to do anything in envy.Envy is a script and should not be necessary...but,if using it,choose the 185.xx driver.But as I understood envy could not find your card...?


BTW,
you asked....yes,Ubuntu 9.10,your card,190.42 driver would be kinda perfect.But a fresh installation would be better than upgrading from 8.04 I think..

---

### Post by psyboy55 on 2009-12-12
Ill try to upgrade to 9.10 and hope it will recognize my hardware. if not i will try the updated tutorial. Ill respond back when its done upgrading (tommorow.)

---

### Post by psyboy55 on 2009-12-12
O no i just realized when i upgraded i cant hear anything on my speakers. it just has a cross over the volume controlls. how did this happen? Or is it just doing that becuase im upgrading?

---

### Post by psyboy55 on 2009-12-12
Good news. the upgrade to 8.10 fixed the sound and graphics card problem. now there is only one problem... Desktop effects says "could not enable effects" im gonna upgrade again to see if it gets fixed.

---

### Post by psyboy55 on 2009-12-13
Bad news. When i upgraded to 9.04 it wouldn't boot. it said xorg and x-server was broken. when i ran Dpkg it fixed it but now its mirroring the screen instead of 2 individual screens. I cant use "display" to fix it. When i run nvidia settings it tells me im not running a nvidia driver. im gonna see if another upgrade helps :( (9.10)

---

