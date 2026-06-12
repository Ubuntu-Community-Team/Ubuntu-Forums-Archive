---
title: "xgl install gone wrong, is there a way to recover?"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by Johnnyboyct on 2006-06-18
Hey guys totally new to unix, tried to follow the xgl tutorial for nvidia here and I cant get to the kubuntu login. All this after finally figuring out the wireless driver thing :(

Anyways, It starts, does all the oks, then shows the kubuntu logo and does nothing :( BTW I installed ubuntu, then installed kde and it worked, then restarted after the xgl thing and nada :(

Is there a way to restore my configuration from before? 

EDIT: just noticed it says postix failed...

Thanks alot, John

---

### Post by LKRaider on 2006-06-18
Did you try running:
```
sudo dpkg-reconfigure kdm
```

What config files did you alter? Was it only **gdm.conf-custom**? If yes, just rename that file to gdm.conf-custom.xgl and gdm should be back to the default behaviour.

---

### Post by Johnnyboyct on 2006-06-18
Well I dont know if thats going to help anymore :( 

I tried to do 
sudo apt-get remove kdm 
and the for gnome.

Now it starts up to a black screen lol

I tried to apt-get install them, but no luck... Ill wait for advice this time lol


Thanks :)

---

### Post by Johnnyboyct on 2006-06-18
Ok so after the restart of that, it now says:
GDM:Xserver no found: /usr/bin/xgl:0 :0 - fullscreen -ac -accel glx:pbuffer -accel xv:fbo -auth /var/lib/gdm/:0 xauth -nolisten tcp vt7 error command could not be execured please install  the xserver or correct gdm configuration.

---

### Post by LKRaider on 2006-06-18
It is trying to load Xgl. Remove or rename the /etc/gdm/gdm.conf-custom file and try again.

---

### Post by Johnnyboyct on 2006-06-18
:( tried that, now I get ee problem parsing config file, fatal server error: no screens found :(

Any ideas?

---

### Post by joscar on 2006-06-18
it sounds to me like you should rename your backup /etc/X11/xorg.conf.backup or /etc/X11/xorg.conf~  to  /etc/X11/xorg.conf . in essence you will be restoring the default  xorg config.

---

### Post by Johnnyboyct on 2006-06-19
That worked! Thanks, Im back in gnome now. Ive tried it 3 more times lol Heres what I have in my xorg.conf
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection
It says to comment out "GLcore" , I dont have that, is that why?

Thanks alot!

---

