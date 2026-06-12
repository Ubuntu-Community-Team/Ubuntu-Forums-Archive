---
title: "32bit LiveCD on 64bit machine"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by fantab on 2012-05-22
I have encountered a strange (?) issue while trying to install a 32bit 12.04 on a 64bit machine.

I have another PC with only 1gb RAM and Pentium D 64bit Processor. I have always installed a 32bit version of BUNTU on it considering the relatively low RAM. However, **I could not install 32bit 12.04 BUNTU (neither Ubuntu nor Kubuntu) on it**. I tried almost every workaround there is, like "nomodeset", i915.modeset=1, pci=noacpi etc... I even tried LinuxMint-13_Maya-32bit-Cinnamon-RC with no effect. 

The culprit always was the X server... the system reported that:

```
"Failed to start X server(your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"
```

... on examining the /var/log/Xorg.0.log there were no errors/EE but a few warnings/WW:

```
[WW] /usr/share/fonts/X11/cyrillic : does not exist
[WW] /usr/share/fonts/X11/100dpi  : does not exist
[WW] /var/lib/deforma/x-ttcidfont-conf.d/dirs/TrueType  : does not exist
Also,
[WW] Falling back to old probe method for vesa
[WW] Falling back to old probe method for fbdev

etc/X11/xorg.conf is not configured correctly; restart Display Manager after you have configured xorg.conf. And the same goes for
/usr/share/X11/xorg.conf.d

Screens found but no usable configurations (or something like that)

Segmentation Fault at address 0x116
```

Then I tried installing Ubuntu-64bit 12.04 with a LiveCD (which I have already installed on my other desktop) and the LiveCD worked fine and I was able to install the 64bit Ubuntu without any issue. The installation ran like a knife through cheese. 

**I need to understand why I could not run 32bit LiveCD nor install 32bit BUNTU on a 64bit machine.** 

Can someone here please explain it to me? Is it a bug or does it have something to with PAE Kernel? Because AFAIK we can install 32bit BUNTU on a 64bit Desktop, after all Ubuntu "recommends" it as a safe bet.

Thanks.

---

### Post by jadtech on 2012-05-23
have you tryed to boot that on another computer   could be a bad burn  ???

i have seen people  through here more then a few who load the 32bit recomend on there 64bit processor no problem ..

---

### Post by mastablasta on 2012-05-23
> [WW] /usr/share/fonts/X11/cyrillic : does not exist
[WW] /usr/share/fonts/X11/100dpi  : does not exist
[WW] /var/lib/deforma/x-ttcidfont-conf.d/dirs/TrueType  : does not exist
Also,

 
do you use cyrilic keyboard? have you tried with DVD then?

---

### Post by fantab on 2012-05-23
> **jadtech said:**
> have you tryed to boot that on another computer   could be a bad burn  ???
i have seen people  through here more then a few who load the 32bit recomend on there 64bit processor no problem ..

> **mastablasta said:**
> do you use cyrilic keyboard? have you tried with DVD then?

It is definitely not a bad burn. And this did not happen with any previous version of any BUNTU. 

No. I don't use a cyrillic Keyboard. It normal US. And NO, I did not try it with DVD. 

Also, there is no Xorg.conf file anymore in BUNTU, so...

By the way the desktop in question has onboard Intel GMA950.

---

### Post by mastablasta on 2012-05-23
ah. strange then that vesa fallback is not working.
 
950 has poor 3d acceleration. could that be the issue, sicne unity uses 3D? 
does 10.04 work? what about xubuntu?

---

### Post by fantab on 2012-05-23
I have tried Ubuntu 12.04 _32bit, Kubuntu 12.04_32bit and LinuxMint Maya RC_32bit. Yes, all the previous versions of BUNTU work. 

I understand that there are issues with 950GMA but how come 64bit gets installed with the same graphics... off course the Monitor Resolution does not work and I had to force it with xrandr.

---

### Post by roelforg on 2012-05-23
> **fantab said:**
> I have tried Ubuntu 12.04 _32bit, Kubuntu 12.04_32bit and LinuxMint Maya RC_32bit. Yes, all the previous versions of BUNTU work. 
 
I understand that there are issues with 950GMA but how come 64bit gets installed with the same graphics... off course the Monitor Resolution does not work and I had to force it with xrandr.
 
Try another 64bit machine, maybe it's a problem with the ubuntu 12.04+your hw setup combi?

---

### Post by fantab on 2012-05-23
> **roelforg said:**
> Try another 64bit machine, maybe it's a problem with the ubuntu 12.04+your hw setup combi?

It works on another 64bit machine, which I tried after creating this thread. I know there is an issue with my hw, I am trying to figure out what.

I tried Knoppix_DVD and it works on the affected machine...

---

