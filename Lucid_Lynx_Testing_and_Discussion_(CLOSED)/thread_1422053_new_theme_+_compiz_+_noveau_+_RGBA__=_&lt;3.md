---
title: "new theme + compiz + noveau + RGBA  = &lt;3"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nanog on 2010-03-04
This only works on some cards. Go here to see if your card might be supported: 
[http://nouveau.freedesktop.org/wiki/FeatureMatrix](http://nouveau.freedesktop.org/wiki/FeatureMatrix)

The performance of noveau with compiz enabled is really something. Things are so much more cripser and snappier than nvidia. Buh bye nvidia...and don't let the door hit you on your a**.

```


VGA compatible controller		: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)


-OpenGL-
Vendor		: nouveau
Renderer		: Gallium 0.4 on NV86
Version		: 2.1 Mesa 7.8-devel
Direct Rendering		: Yes


```

---

### Post by Atermoon on 2010-03-04
Awesome! Could you share with the rest of us how you got nouveau and 3d working? :p

---

### Post by nanog on 2010-03-04
**Installer beware: this is only for bleeding edge types who are comfortable troubleshooting breakage. **

[https://wiki.ubuntu.com/X/Testing/NouveauEvaluation](https://wiki.ubuntu.com/X/Testing/NouveauEvaluation)

When first enabling compiz jockey sometimes throws off xorg errors and has window decoration problems but issuing this command fixes things:

```
compiz --replace &
```

---

### Post by PRGUY85 on 2010-03-04
> **Atermoon said:**
> Awesome! Could you share with the rest of us how you got nouveau and 3d working? :p

Same question here...and is boot screen working? I switched to Nvidia and got fallback plymouth bluebars. Hope getting 3d on nouveau doesn't give me faulty plymouth.

---

### Post by nanog on 2010-03-04
Plymouth is working. The boot seems a little longer but I have not troubleshooted because I typically use suspend.

---

### Post by PRGUY85 on 2010-03-04
> **nanog said:**
> Plymouth is working. The boot seems a little longer but I have not troubleshooted because I typically use suspend.

Still don't understand how to activate Compiz.  Tried on Desktop Effects and by using compiz replace on terminal but no 3D was activated.

---

### Post by nanog on 2010-03-04
1080p HDTV on a second screen works!

The only problem so far are a few **very** minor bugs (scale minimizes apps etc).

---

### Post by dearingj on 2010-03-04
> **PRGUY85 said:**
> Still don't understand how to activate Compiz.  Tried on Desktop Effects and by using compiz replace on terminal but no 3D was activated.

I've got the same problem; Compiz refuses to run. "Fatal: Software rendering detected.". Aside from that, Nouveau seems to be working perfectly.

---

### Post by nanog on 2010-03-05
You need to follow the instructions in the link I gave. In particular, you need to use the xorg-edgers ppa and edit your xorg to enable the "nouveau" driver. You also need to make sure that the "nouveau firmware" package is installed. Reboot and enable compiz in gconf or issue compiz --replace. Jockey is a bit buggy but I got it to work by ignoring the errors and "keeping the configuration".


This works for my 8400M gs but there is no guarantee that it will work for all nvidia hardware.

---

### Post by PRGUY85 on 2010-03-05
Updated my nouveau driver with ppa files.  Tried compiz --replace, got fatal software rendering error on terminal.  Using Geforce Go 7400.

---

### Post by nanog on 2010-03-05
> got fatal software rendering error on terminal

I got that error previously but it started working after a recent set of updates.

---

### Post by PRGUY85 on 2010-03-05
> **nanog said:**
> I got that error previously but it started working after a recent set of updates.

So...for now just sit tight and wait for it to fix on it's own? I have sudo compiz --replace as a startup command.

---

### Post by dearingj on 2010-03-05
> **nanog said:**
> You need to follow the instructions in the link I gave. In particular, you need to use the xorg-edgers ppa and edit your xorg to enable the "nouveau" driver. You also need to make sure that the "nouveau firmware" package is installed. Reboot and enable compiz in gconf or issue compiz --replace. Jockey is a bit buggy but I got it to work by ignoring the errors and "keeping the configuration".


This works for my 8400M gs but there is no guarantee that it will work for all nvidia hardware.

I initially didn't have an /etc/X11/xorg.conf file. I first tried copying & pasting from the link you provided (adding nothing else to the file), and then tried generating a new file using ```
sudo Xorg -configure
sudo nano ~/xorg.conf.new # Making sure that nouveau was specified
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
```

No change either way.

My card is identified as > 01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by Atermoon on 2010-03-05
That's the same wiki page I followed a couple of days ago on one of my Kubuntu installs. 2D was faster than ever but any attempt to activate compositing led to a complete system freeze.

Oh what the hell I'm going to try it on my main install too! :D

---

### Post by nanog on 2010-03-05
Here is my xorg.conf:

```
Section "Device"
	Identifier "8400M"
	Driver "nouveau"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by Atermoon on 2010-03-05
> 
[LIST=1]
[*]If you currently are using the -nvidia binary  driver, it will need to be removed.  Use System > Administration >  Hardware Drivers to deactivate it. 
[*]Reboot
[/LIST]
...

3. Black screen and monitor goes to sleep.

I should probably do the same, it's 7:15 am here and I haven't slept at all but damn, this is way too much fun.

---

### Post by Atermoon on 2010-03-05
No luck, compiz just won't run with nouveau for me, falls back to metacity. Added the [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) too and saw shadows under the panel after login but that was pretty much it - my system locked up.
My card is nVidia 6800XT btw. Switching back to the nvidia driver on my main install and going to add another one for nouveau testing only.

---

### Post by dichtbijzee on 2010-03-05
IT WORKS!

yippie, but its actually a bit to slow on my dualhead 2704*1050.
but everything is better then the nvidia binary driver.

edit:

I have found out what my problem was. in the link given it says to add the xorg egders nauveua ppa, but you actually need the whole xorg edgers ppa for mesa with gallium update. gallium is needed for compiz.

---

