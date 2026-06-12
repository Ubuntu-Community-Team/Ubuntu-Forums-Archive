---
title: "Problem installing ATI drivers."
date: 2015-12-16
forum: Installation &amp; Upgrades
---

### Post by Roman_Oswald on 2015-12-16
I'm just busy installing a new computer whit the latest Lubuntu version. This computer has an ATI X1500 graphic card and I'm not able to install the driver, (at least the performance is poor). The installed driver is "VGA compatible controller". 

On [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) I found that i need xserver-xorg-video-ati package. 

Next I did "sudo apt-get install xserver-xorg-video-ati" and that give me a message that the driver already is up-to-date. So i downloaded the latest one on  [https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati](https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati) , the latest and the latest stable, although that is one a diff file and i don't know what to do whit that. But when i unpack the latest version and try a ./configure it says that it can't find a C-Compiler, could be on a just installed Lubuntu version, so which do I need? In the Software Centre there are so much, that I don't know which I have to install.

Or am I totally wrong (as the German says, "on the wood way")...

---

### Post by deepakdeshp on 2015-12-18
To install c please follow
[http://askubuntu.com/questions/428198/getting-installing-gcc-g-4-9-on-ubuntu](http://askubuntu.com/questions/428198/getting-installing-gcc-g-4-9-on-ubuntu)

If that doesnt work you can try installing the latest Kernel which may support the graphic card. But it may also crash your system if some of the hardware isnt supported.
[http://tecadmin.net/install-linux-kernel-on-ubuntu/](http://tecadmin.net/install-linux-kernel-on-ubuntu/)

---

### Post by QIII on 2015-12-18
Do ***not*** attempt to install the package in either manner suggested above.

Your video adapter is old and AMD no longer supports it with a proprietary driver.  Not for the newer kernel, not with gcc 4.9.  It is not supported at all with any X Server version since about 2009.

Following either of those sets of instructions will render your system non-operational which will require some work from recovery mode to remedy.

Continue to use the default driver installed when you originally installed Ubuntu.  You don't need to install anything further.

@deepakdeshp -- please be very careful with your advice.

---

### Post by Roman_Oswald on 2015-12-18
On this link: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) it says that my card is fully supported from 12 trough the latest 15.10.  

But I noticed that when I set the Software Centre to Advanced that the xserver-xorg-video-ati package is already installed. But why does it feel so slow on the desktop. There are also lost of other packages installed that I doubt that I don't need those, like xserver-xorg-video-mach64, xserver-xorg-video-neomagic and lots of other hardware i don't have. Will I gain more speed removing those? Especially boot time.

---

### Post by QIII on 2015-12-18
It is supported by the open source Radeon driver.

It is ***not*** supported by the proprietary AMD Catalyst driver.  In my post above I was referring to deepakdeshp's suggestion that installing it, gcc 4.9 or a newer kernel would be helpful.

The open source driver is installed when you install Ubuntu, which is why you can see your desktop after you install Ubuntu.  It is slow because that card is very old, it is not very powerful and Unity, the desktop environment in Ubuntu, is very resource intensive.  You might have better luck with a lighter desktop environment, such as comes with Xubuntu or Lubuntu.  But if that is still slow, there is not much to be done.

---

### Post by mörgæs on 2015-12-18
Yes, your card is fully supported by the open source Radeon driver, which is installed by default. As mentioned above, don't try to add closed-source (fgl-rx) drivers.

If you are using Lubuntu 15.10 with default drivers you can't get much more out of the system.

(Ninja'ed!)

---

### Post by Roman_Oswald on 2015-12-18
Aha, ok. thanks for the information.

---

