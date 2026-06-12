---
title: "Trying to install ATI drivers"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by foolios on 2007-12-05
The command:
sh ./ati-driver-installer-8.28.8.run
I thought maybe it should be sudo ./ati-driver-installer-8.28.8.run

not working either.

Trying to use the auto installer from the page:
[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

Currently trying this:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Although it says it's for 9700, mine is a 9100, I am hoping it will work.

Pointers would be much appreciated.

Thanks in advance.

---

### Post by foolios on 2007-12-05
Unfortunately after following the directions for method #1, I don't get the results to identify the card as ati. I'm guessing it didn't work like it should have.

foo@foo-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

---

### Post by mike^_^ on 2007-12-05
You need to build the specific package for your os (assuming your using edgy, you can use --listpkg and replace "Ubuntu/edgy" with what ever you are using.)
```
sh ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/edgy
```

not just
```
sh ./ati-driver-installer-8.28.8.run
```

afterwards install the packages using dpkg

---

### Post by kelvin spratt on 2007-12-05
Why not Install Envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
It will download and install. ATI on NVIDIA drivers for you with no hassle i downloaded the latest ATI driver it works a treat.

---

### Post by casacerian on 2007-12-10
I am also trying to install ATI drivers for my 9100 card. So far no luck. Whenever I try to compile the driver from the desktop I get a syntax error and it craps out. :(


EDIT: More specifically this:

root@william-laptop:/home/william# sh /home/william/Desktop/ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.24.8.............................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 97: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

---

### Post by foolios on 2007-12-16
That's the same error I am getting when I run the provided line in the example given.

I will try the Envy. I didn't know it was for ATI as well. It seemed to be for nvidia when I went to the site.

I tried addenduming gibbon since I have gutsy gibbon.

---

### Post by foolios on 2007-12-16
It seemed to install, and then I noticed there was a new envy application. So I started it and told it to install the driver for ATI. I thought it had already done so but I wasn't sure.
The error I get is that the legacy driver does not support my card.

---

### Post by foolios on 2007-12-16
In the system though it does now show the card as an ati card, radeon version. So that' a whole lot better. Something worked. Just not sure if there's anything that could be wrong. I don't know if the envy application was not supposed to be started. But even still I would think it wouldn't error if everything was right.

---

