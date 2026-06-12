---
title: "Enable Xorg Hardware acceleration"
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by jemt on 2005-07-29
Hi Experts.

I have just performed a Minimal/Server installation and now got X running with Xface . Everything seems to be working fine. But unfortunately I have no Hardware Acceleration enabled on my Matrox G200 AGP Graphics Card (I have been running with Hardware Acceleration under Mandrake Linux so I'm pretty sure that my card supports it).

Could someone please tell me how I enable hardware acceleration for my graphic card under Xorg ?

 - Thanks :)

---

### Post by darkpark on 2005-07-29
Try looking here:

[http://utah-glx.sourceforge.net/](http://utah-glx.sourceforge.net/)

---

### Post by jemt on 2005-07-29
Hi.

Thanks alot. But I'm pretty sure that xorg supports it. Would be great if I didn't haft to install additional software :)

---

### Post by heimo on 2005-07-30
Which driver are you using? In file /etc/X11/xorg.conf search for Driver - there are several sections with this name, look for the one with your cards name* - ie. I have:

 ```
Section "Device"
		Identifier	  "NVIDIA Corporation NV34 [GeForce FX 5200]"
		Driver		  "nv"
		BusID		   "PCI:1:0:0"
EndSection

``` 

You probably should have driver mga. Good source for debugging information is log file: /var/log/Xorg.0.log

[http://www.x.org/X11R6.8.2/doc/mga.4.html]("http://www.x.org/X11R6.8.2/doc/mga.4.html")

I've had several G100/G200 cards and I think those were hardware accelerated, but 3D acceleration either is not available or plainly sucks. But with correct driver, that card should do quite well. :) (I consider it as a classic 2D card.)

*) If you can't find one, find the one that has same identifier line as the Screen sections Device line has.

---

### Post by jemt on 2005-07-30
Hi.

I'm using the 'mga' driver which I also used under Mandrake Linux - as far as I remember. But my card was working much better under Mandrake. To mention an example I could play Tuxracer wich pretty good graphic and all - that's impossible under Ubuntu duo to lack.

I'm also quite sure that it is just a setting that I haft to set some where for xorg. During X configuration under Mandrake I could choose between hardware acceleration or "normal" X. But ok, might have been a kernel/driver thing. So I'm not too sure after all :)

---

### Post by heimo on 2005-07-30
Hmm... ok, so it's about 3D acceleration. Your OpenGL performance is lacking / running on software. I don't know if I remember the commands exactly (I can't verify these easily at the moment), but I think it's glxinfo - run it in terminal. You can also try running glxgears to see how your 3D is working. I'm not even sure that G200 does 3D acceleration, but if you've played tuxracer with it, it probably does.

I'm not sure about these either, but do you have lines like these in your xorg.conf?
 ```

		Load	"glx"
		Load	"GLcore"

```

---

### Post by jemt on 2005-07-30
heimo >

The result from glxinfo is available [here](http://powerzone.dk/results.txt).

I add'ed 'Load	"glx"' and 'Load "GLcore"' to my configuration file. Unfortunately X wouldn't start afterwards.

---

### Post by heimo on 2005-07-30
I just today installed nvidia drivers (and my 3D acceleration now works) on my Breezy Badger and I have no GLcore or dri modules loaded in xorg.conf, but I do have glx.

I get 404 not found on your link.


EDIT:

my module section from xorg.conf:
 ```
Section "Module"
#	   Load	"GLcore"
		Load	"bitmap"
		Load	"dbe"
		Load	"ddc"
#	   Load	"dri"
		Load	"extmod"
		Load	"freetype"
		Load	"glx"
		Load	"int10"
		Load	"record"
		Load	"type1"
		Load	"v4l"
#	   Load	"vbe"
EndSection

```

---

