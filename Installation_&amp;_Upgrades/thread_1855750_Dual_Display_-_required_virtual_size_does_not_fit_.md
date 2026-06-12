---
title: "Dual Display - required virtual size does not fit available size"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by SushiAddiction on 2011-10-06
I just installed 11.10 rc and I changed my ATI settings (dual monitor) and after reboot I cant use dual monitor any more

It seems the "Display" app in ubuntu wont allow me to use dual monitors. I get the error 

"required virtual size does not fit available size: requested=(2304, 768), minimum=(320, 200), maximum=(1280, 1280)"

and because I can't get both monitors active (except mirrored) I can't use dual display in ATI ccc

EDIT>
                 Update. not exactly sure what caused it but the problem was xorg.conf
  seems the old xorg.cofg was renamed to xorg.conf.dist-upgrade-201110070100
 and the new xorg.conf only had in it
 
```

Section "Screen"
 Identifier    "Default Screen"
 DefaultDepth    24
EndSection
 Section "Module"
 Load    "glx"
EndSection
```

so I restored the old xorg.conf and everything works.

---

### Post by ppatalano on 2011-10-19
Just upgraded and the same exact thing happened. This kind of stinks.

---

### Post by ppatalano on 2011-10-19
First, in terminal you need to:

```
gksudo amdcccle
```

Then, head over to display manager -> multi display

Select Multi-display desktop with display(s)

Apply this and restart. It worked for me.



via
[http://blog.jvc26.org/2011/09/29/multimonitor-ubuntu-oneiric-fglrx](http://blog.jvc26.org/2011/09/29/multimonitor-ubuntu-oneiric-fglrx)

---

### Post by taddygrrr on 2011-10-21
After upgrading to 00, dual monitor support was OK with my 2 1920x1200 monitors rotated. I noticed that the mouse tracking was slow over Chrome. So, I did the additional drivers install of the ATI proprietary driver.  Mouse tracking was full speed, but now I only had one display mirrored. I didn't have a backup xorg.conf in my /etc/X11.  The xorg.conf was bare.  Running Catalyst Control Center would exit without asking me to apply changes.  Mofifying the xorg.conf file to have a Display subsection with a larger virtual size, followed by running CCC worked for me.

Section "Screen"
	Identifier "Default Screen"
	Device     "Default Video Device"
	DefaultDepth     24
	SubSection "Display"
		Virtual   2400 1920
	EndSubSection
EndSection

CCC wrote out an a full xorg.conf file and all is well now.

---

