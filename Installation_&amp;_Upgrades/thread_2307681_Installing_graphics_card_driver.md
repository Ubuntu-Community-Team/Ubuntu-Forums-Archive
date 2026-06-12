---
title: "Installing graphics card driver"
date: 2015-12-27
forum: Installation &amp; Upgrades
---

### Post by paul246 on 2015-12-27
I am attempting to give Ubuntu a go. I've never used it, or any form of Linux before, and I'm completely stuck. I've managed to install 14.04 on my old Dell laptop; I have gotten as far as logging in to my account and then the screen goes completely blank. I have spent a lot of time trawling through forums and help sites and from this I believe I need to install a driver for the NVIDIA graphics card. I have found a couple of guides on how to do this, but I am so completely new to Linux I can't figure them out.

i have gone to NVIDIA's website (from my Mac mini) and downloaded what I believe is the correct driver onto a USB stick. I have managed to switch the (Ubuntu) laptop to Terminal view (ctrl+alt+F1) and now I'm stuck. Can anyone offer up a COMPLETE BEGINNER step by step explanation of how to do this? I would stress again that I have absolutely zero experience of working in command line. So I can't make sense of guides like these:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu_14.04_and_up](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu_14.04_and_up)
[http://www.beginninglinux.com/home/graphics-drivers/install-nvidia-custom-driver-on-ubuntu-12-04](http://www.beginninglinux.com/home/graphics-drivers/install-nvidia-custom-driver-on-ubuntu-12-04)

even though I'm sure they're painfully obvious to more experienced Linux users.

If needed my computer spec (most of whic means nothing to me) is:

Dell Inspiron 5150
mobile Pentium 4 HT 3.06 Ghz/1.60 Ghz
application CPU: Enabled
Current CPU speed: 3.06
level 2 cache: 512 KB
system memory: 2048 MB
video controller: NVIDIA GeForceFX5200
video memory: 64 MB
panel type: 15" Super XGA+
audio controller: Sigmatel 9750
modem controller: Broadcom Polaris
primary hard drive: 80 GB
modular bay: DVD+RW

Huge thanks for any help anyone can offer

---

### Post by Bashing-om on 2015-12-27
paul246; Hello, Welcome to the forum.

Ouch ! :
> 
install 14.04 on my old Dell laptop; 
bk
video controller: NVIDIA GeForceFX5200

And Nvidia tells us :
> 
The 173.14.xx driver supports the following set of GPUs: 
GeForce FX 5200 
Note: Support for the 173.14.xx series is discontinued. No further releases from this series are planned.


Maybe, just maybe in 14.04 there is still a proprietary driver. Let's check.
From that ctl+alt+F1 console interface, what returns from terminal commands:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```
If it turns out the 173 driver is still available it is a simple matter to make sure the system is clean and ready to accept the installation of the proprietary driver FROM our software repository .

fingers crossed ->
[INDENT][INDENT]maybe YES
[/INDENT][/INDENT]

---

### Post by deadflowr on 2015-12-27
> If it turns out the 173 driver is still available it is a simple matter to make sure the system is clean and ready to accept the installation of the proprietary driver FROM our software repository .


It is, at least for 14.04.
```
nvidia-173:
  Installed: (none)
  Candidate: 173.14.39-0ubuntu3
  Version table:
     173.14.39-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/restricted amd64 Package
```


My second thought, though, is that I'm not sure how well Ubuntu -normal, would run on that card and cpu.
I'm confident that the system CAN run Ubuntu, but I think it'll be slow.
(Ubuntu is graphically intensive)
Perhaps something lighter would suffice. Ubuntu Mate or Xubuntu, maybe...

---

### Post by Bashing-om on 2015-12-27
paul246; deadflowr; :)

+1

I sure like (L)ubuntu on older hardware:
> 
Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware.


[INDENT][INDENT]hey
[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-12-27
> video controller: NVIDIA GeForceFX5200
video memory: 64 MB

That would rule out Ubuntu + Unity in my opinion even with the Nvidia 173 driver. My advice would be to install again but with Lubuntu 14.04 and do not tick the box labelled "Install third party software." That action installs not only some proprietary but free audio & video codecs but also a proprietary video driver which might not support that video card.

Once you get to a working desktop a person can install  the audio & video codecs buy installing Restricted Extras from the software centre. Which might also be the location for Nvidia binary X.Org driver ('version 173' driver) if it cannot be found in Additional drivers.

Regards.

---

