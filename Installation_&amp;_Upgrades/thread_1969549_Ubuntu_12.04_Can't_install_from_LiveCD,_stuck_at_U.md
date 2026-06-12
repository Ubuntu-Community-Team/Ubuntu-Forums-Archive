---
title: "Ubuntu 12.04: Can't install from LiveCD, stuck at Ubuntu dots screen, no desktop"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by veroslav on 2012-04-30
Hi,

I am trying to install Ubuntu 12.04 (64-bit) from a Live CD (verified SHA-1 sum and also verified disk after burning).

After booting from the Live CD, the boot process gets stuck at the Ubuntu text and the blinking orange dots. At first, the dots are progressing (on/off) but after a while they just stuck at the white light and nothing happens after that. I never manage to get to the desktop.

The output from the lspci gives the following:

```
user@laptop:~$ lspci -v | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) (prog-if 00 [VGA controller])
```

I've tried booting the Live CD with both acpi=off and nomodeset boot options but it made no difference (still stuck at the Ubuntu dots and no desktop). I also tried combining these options together but no difference.

I find this strange as I have Ubuntu 11.10 (64-bit) previously installed on the same laptop without any problems and working flawlessly. :(

Could anyone give me a helping hand?

Thank you in advance.

Regards.

---

### Post by nothingspecial on 2012-05-01
*Thread moved to **Installation & Upgrades**.*

---

### Post by Malvazar on 2012-05-10
I am also having this issue. I can't get to a desktop on the live cd. I've tryed loading from flash drive and cd and nothing, just the loading screen for hours. I've got 10.04 amdx64 installed now without any problems. Can't figure out what the problem is especially scene the 32bit version loads perfectly on my laptop. Would really appreciate some incite on this issue.

---

### Post by jadtech on 2012-05-10
you could try  to install with the mini ISO you will end up with the same program  how ever it  installs with out graphics ( Texted based install) and most report its a faster install  and many are having better luck with it ..

---

### Post by Malvazar on 2012-05-10
Well it looks like I'm doomed to staying with 10.04. I've tried everything now...... *annoyed*

---

### Post by jadtech on 2012-05-10
everything ??? 

the mini ISO  wont install  ?? 

just out of curiosity have you tried the boot  without internet connection I havea trouble free 12.4 install I have ATI video I did the whole boot and install not allowing any internet connection as soon as everything  was booted installed and booted I installed the additional drivers for the wireless and ran all the updates after ..

I burned the ISO to a dvd because  the burn is actually  more then can actually fit on a CD the actual boot from disc took 7  mins on a new lap top right out of the box booted  win7 just long enough to delete a partition and shrink the volume to make room for ubuntu  and yes the ubuntu splash screen and flashing dots seemed to  be there for ever it did  finally boot but it kept  nagging for me to  connect to the internet and for password .. 

first thing I did once the live cd booted was to  get to gparted and partitioned   got the swap partition going and then things moved  alot faster then I moved on to installing ..

---

### Post by Malvazar on 2012-05-13
Just don't get it..... I'm pretty sure I've done everything now... I've tried the no Internet method, the mini iso method, usd method, cd method, and so much more I can't remember what it is anymore.... >.<
I really wish I knew why it is that I can't load the darn live cd to load, even just try the new version. How could it be so completely different from 10.04 that is can't load on my system. I have a buddy down the road that was able to get it to load on his amd 64bit system just fine. This is very irritating.

---

### Post by oldfred on 2012-05-14
Did you check to see if it is a video issue?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Malvazar on 2012-05-16
Okay I'm think I'm finally starting to make some headway in this most annoying problem. I got the live cd to use the "nomodeset" option on its initial startup, and it did as its always done and hung up on the splash screen, but this time I finally got an error message at least. And it goes as followed:

[112.778948] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[112.778959] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[112.778965] Please visit [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) Please read and follow directions carefully to install the missing firmware

I went to the address and read it all but its was just telling me what I have to do to install my wireless card after I've install the OS initially. So now I'm more confused then ever.......

---

### Post by Malvazar on 2012-05-16
Okay I finally got the darn OS to boot and install. I don't know why not after at least 4 older versions of ubuntu, but for some reason 12.04 would not boot because of my wireless card. I pull it out and tried again and suddenly it worked just fine. I'm not very please that I can't have my wireless card now though...... >.<

---

