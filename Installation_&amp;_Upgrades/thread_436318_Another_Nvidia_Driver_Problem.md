---
title: "Another Nvidia Driver Problem"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by bothebobo on 2007-05-07
I seem to have the same problem as everyone else using the nvidia driver.
Ive installed all the relevant softwares i suppose, but im still kinda a newbie so im not sure exactly what kernels have to be and when to do 'em.
Originally I wanted to setup two screens but found out that nvidia drivers need to be installed.
So the prob is: when using restricted drivers manager, nv is changed to nvidia in the xorg.conf. once i restart X, the message: 

"FAILED TO INITIALIZE THE NVIDIA KERNEL MODULE. PLEASE ENSURE THERE IS A SUPPORTED NVIDIA GPU IN THIS SYSTEM & THAT NVIDIA DEVICE FILES HAVE BEEN CREATED PROPERLY"

now the packages i have installed (which i believe to be somewhat relevant) are:
[LIST=1]
[*]linux-image-386
[*]linux-image-2.6.12-10-386
[*]linux-image-2.6.12-9-386
[*]linux-image-2.6.15-23-386
[*]linux-image-2.6.15-27-386
[*]linux-image-2.6.17-10-386
[*]linux-image-2.6.17-11-386
[*]linux-image-2.6.20-15-386
[*]linux-restricted-modules-2.6.15-27-386
[*]linux-restricted-modules-2.6.20-15-386
[*]linux-restricted-modules-386
[*]nvidia-glx
[*]nvidia-kernal-common
[*]xserver-xorg-video-nv
[*]linux-restricted-modules-common
[/LIST]

I've also checked out the various websites and followed most of the advice and steps but to no prevail:
[LIST=1]
[*][http:///www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http:///www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)
[*][https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[*][http://ubuntuforums.org/showthread.php?t=213409](http://ubuntuforums.org/showthread.php?t=213409)
[*][http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)
[*][http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
[/LIST]

Here's my xorg.conf
```

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"TwinView"	"True"
	Option		"TwinViewOrientation"	"RightOf"
	Option		"UseEdidFreqs"	"True"
	Option		"MetaModes"	"1280x1024,1280x1024; 1024x768,1024x768"
	Option		"UseDisplayDevice"	"DFP"#replace 'string' with either #'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected #via VGA ports), or 'TV'
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

```
and here's what happens when i punch in lspci | grep -i nvidia
```

bo@bo:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

Other wierd things ive tried:
[LIST=1]
[*]sudo vi /etc/default/linux-restricted-modules*
Change the DISABLED_MODULES=”" to DISABLED_MODULES=”nv”
[*]tried to install the nvidia driver from [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)
[*]installed this weird package linux-restricted-modules-2.6.15-27-386 2.6.15.12-1 (i386 binary) in ubuntu dapper from [https://launchpad.net/ubuntu/dapper/i386/linux-restricted-modules-2.6.15-27-386/2.6.15.12-1](https://launchpad.net/ubuntu/dapper/i386/linux-restricted-modules-2.6.15-27-386/2.6.15.12-1)
[*]sudo depmod
[*]modprobe nvidia
[*]bo@bo:~$ sudo gedit /etc/X11/XvMCConfig
added line: libXvMCNVIDIA_dynamic.so.1
[/LIST]

Maybe theres some way to remove all the crap ive done and start fresh, rebuild a new kernel etc.?
Any help will be grateful, ive spent the good part of a weekend on this mess.

---

### Post by kyphi on 2007-05-07
You said that originally you tried to set up two monitors.

You have done a lot of fiddling hereI and I wonder if you tried

```
sudo nvidia-glx-config enable
```

If I were in your position I would start all over again - reformat - reinstall.

---

### Post by bothebobo on 2007-05-08
I just tried
```

sudo nvidia-glx-config enable

```
No luck, same answer.

So if I was to reformat and reboot, which method should i use to install nvidia?

---

### Post by suntin on 2007-05-08
I can recommend Envy
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) 
Only problem is after updating to latest version of Ubuntu I have two software updates (nvidia-glx and nvidia-glx-dev) that won't install but aside from ignoring the update icon until I get round to removing these files from my install everything works great.

This should really be included in package manager it's a fantastic app.

---

### Post by bothebobo on 2007-05-08
Im gunna try it, right now im just deleting a bunch of unused music so i can reformat my main drive. thanks a ton

---

### Post by bothebobo on 2007-05-08
Thanks Suntin & Kyphi, I ended up reformatting as Kyphi recomended and everything went ok. WHen it came to installing the nvidia drivers, i ended up just using the restricted drivers manager. and then installed beryl ontop of it no prob. It seems to me since ubuntu is so well integrated with each release, conflict are inevitable, when using restricted modules. Well thanks again, finally i can start plotting some truly demanding graphs.

---

