---
title: "Flash performance issues"
date: 2009-01-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Glowing Fish on 2009-01-16
Hello, I did a quick search for this, but nothing came up specifically dealing with this, it seems.

I just updated to jaunty yesterday, and it seems like everything is working. Flash, is not working as well as it was. I only notice it on certain sites. For example, Facebook (which I believe uses flash) displays pictures wrongly (it only displays half the picture, and the other half is black). Youtube also stops and stutters every few seconds while playing.

Its still usable in most respects. Should I just apt-get dist-upgrade regularly and hope it works out perfectly?

Also, am I wrong in thinking that this is a flash problem? Could it also be a java problem? 

Sorry for asking open-ended questions like this. I don't really know where the problem is, or how much of a problem it is.

---

### Post by agim on 2009-01-16
I guess you could upgrade regularly, but unless you're testing jaunty and helping out, there is no reason to go with an alpha version. A lot of things aren't really working the way they should yet.

---

### Post by marmuta on 2009-01-16
I can only speak for ATI and there flash performance is very dependent on the graphics driver. In order of descending flash performance it's fglrx, radeon XAA and radeon EXA (which is the new default) for me.
To get good radeon EXA performance I had to add 
```
Option		"AccelDFS" "true"
```
to the device section of /etc/xorg.conf. With that most flash plays ok.

---

### Post by jlward4th on 2009-01-16
Can you post your whole Device xorg.conf section?  Thanks!

---

### Post by marmuta on 2009-01-16
Sure, this is most of my /etc/xorg.conf (the rest are ServerFlags): 
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:1:0:0"
	Driver	        "radeon"

	Option		"AccelMethod" "EXA"
	Option		"AccelDFS" "true"
	Option		"EnablePageFlip" "true"
EndSection

```
AccelMethod EXA should be redundant since it's default now. Both of the other options may have issues with some cards but it's what I found to work best for mine in Jaunty.
If you want to experiment a bit more
```
man radeon
```
has all the options described.

---

### Post by Glowing Fish on 2009-01-18
```
Section "Device"
	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

```

Perhaps I should see about getting a new video card, as well?

---

### Post by marmuta on 2009-01-18
Maybe..., apparently flash needs 128MB of video ram to enable gpu acceleration.
[http://www.adobe.com/products/flashplayer/systemreqs/index.html](http://www.adobe.com/products/flashplayer/systemreqs/index.html)
I remember there was quite a speed-boost when they added that feature, especially for full screen videos.

---

### Post by Glowing Fish on 2009-01-18
Incidentally, you know what I should know before I use Jaunty? Its minimum system requirements. I've never really seen many of those on most Linux releases, since the MSR are pretty much higher than what anyone has, unless they are running a 486.

(Although I have a 486 laptop running Debian, that I haven't turned on for years)

---

### Post by TenPlus1 on 2009-01-18
I have an Nvidia MX400 and my flash works fine, I only have a 32mb card although I have turned the 3D Vsync On if that helps...  I'm also using the latest version of Flash 10 from Adobe (.deb ubuntu)...

---

