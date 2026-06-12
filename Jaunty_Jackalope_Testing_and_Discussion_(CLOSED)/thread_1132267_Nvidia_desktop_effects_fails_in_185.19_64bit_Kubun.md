---
title: "Nvidia desktop effects fails in 185.19 64bit Kubuntu"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by caryb on 2009-04-21
For the last week I have lost my desktop effects, I'm running the prop 185.19 driver that worked perfectly for a week then failed after a xserver update. Does anyone else have this problem? I have a Quadro NVS 140M card in my T61 laptop.
Thinks I have done so far. Restored the xorg.conf to vanilla. When I check jockey for prop drivers it says there are none for my system? I have attached the error screen for your perusal and any help would be appreciated

Cary

---

### Post by Zorael on 2009-04-22
With a vanilla xorg.conf you'll need to enable the proprietary driver. If jockey doesn't suggest it, you could do it manually, or with the nvidia-xconfig utility if that one's still present in newer drivers.

```
Section "Device"
	Identifier	"Configured Video Device"
	**Driver		"nvidia"**
EndSection
```

Again, not sure if nvidia-xconfig still exists.
```
$ sudo nvidia-xconfig -d 24
```

---

### Post by caryb on 2009-04-22
I double checked my xorg.conf & it was set to Nvidia, I enabled the logo & it suggests its using the Nvidia driver & to clinch the deal I can fire up the Nvidia X server settings tool & it says I'm using 185.19 driver. I rechecked my settings in the display settings & when I select use desktop effects it comes up with the dialog box I posted above. I checked that I was using opengl compositing manager & that is set to default. 

Now I'm lost:confused:

Cary

---

### Post by mainalisuyog on 2009-04-22
Use synaptic to remove all nvidia packages, then get the latest nvidia drivers from nvidia website. You have to patch it first. Look around in forums for a way to patch the driver. That is how i got it to work on my pc.

---

### Post by ronacc on 2009-04-22
try using fusion.icon to enable compiz instead of display settings .

---

### Post by caryb on 2009-04-22
Tis KDE doesn't use Compiz but kwin:(


Cary

---

### Post by ronacc on 2009-04-22
sorry , since I use gnome I didn't know that .

---

