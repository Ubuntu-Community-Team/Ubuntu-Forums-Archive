---
title: "Another NVIDIA Resolution Problem"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by zafo on 2006-10-09
I know this has been covered in other posts but everything I have tried hasn't worked.  I have a new HP a1630n AMD64 x2 system.  I have installed the latest 6.06LTS AMD64 version.  I am unable to re-set the resolution to take advantage of the ViewSonic 20" LCD monitor, with a native resolution of 1680 x 1050.

I started with an NVIDIA 6150LE on the board, but have now installed an NVIDIA 7600 (to take advantage of DVI and 2nd monitor output).  My resolution on the latter won't go any higher than 1024 x 768.

I've downloaded and installed nvidia-glx, but when I try to enable it I get this error message:

```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
```

I have tried running the command listed, but I then cannot re-boot into xwindows at all.  

Clip from xorg.conf:
```
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

I have also tried to install the driver from the nvidia.com website, but get numerous messages saying there are missing files.

I've also tried editing xorg.conf per some other posts, but this also results in an inability to start up xwindows.  

Any ideas?

---

### Post by angkor on 2006-10-09
Login at the terminal and try this:

```
sudo dpkg-reconfigure xserver-xorg
```

Keep your monitors manual ready because you will need to know the horizontal sync and vertical refresh rates to get the correct option for your resolution. The rest of the questions are pretty self-explanatory ;)

You could first reinstall the nvidia-glx packages along with this command:

```
sudo aptitude install linux-restricted-modules-`uname -r` nvidia-glx
```

You don't need to enable the nvidia driver just yet, you will do that with the dpkg-reconfigure command. If the drivers installed correctly you can choose the 'nvidia' driver in stead of nv at one of the questions. Good luck.

---

### Post by zafo on 2006-10-09
Thanks very much, Angkor!  That's exactly what I needed and I now have a superb display running at 1680 x 1050.  

zafo :D

---

### Post by angkor on 2006-10-10
You're welcome, very nice screen btw I'm still stuck with a mere 19" ;)

---

