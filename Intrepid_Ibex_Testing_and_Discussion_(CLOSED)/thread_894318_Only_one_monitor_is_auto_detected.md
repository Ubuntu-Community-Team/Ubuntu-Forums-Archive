---
title: "Only one monitor is auto detected"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wiscalico on 2008-08-19
Hi.

For some reason Ubuntu never was able to auto detect both my monitors.
It seems to only find the monitor connected to the analog output.
Now I installed Ibex to see if it was fixed with the latest version of X but still no luck.

I have an Nvidia graphics card with 2 video outputs (1x analog and 1x digital). This is what lspci finds:

```
lspci |grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
```

I've gotten it to work by configuring the xorg.conf by myself but I would like Ubuntu to be able to do this by itself. So if this is a bug I could use som help. I've reset the xorg.conf by issuing:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

After that I added the following line to the Device section:

```
Driver "nvidia"
```

If I don't force X to use the Nvidia driver my monitor only shows noise and thus is unusable.


I have 2 displays but X only detects the one on the analog output:

```
xrandr -q
Screen 0: minimum 320 x 240, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0*    51.0  
   1280x960       52.0  
   1152x864       53.0     54.0     55.0     56.0  
   1024x768       57.0     58.0     59.0  
   960x600        60.0  
   960x540        61.0  
   840x525        62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0  
   800x512        72.0  
   720x450        73.0  
   680x384        74.0     75.0  
   640x512        76.0     77.0  
   640x480        78.0     79.0     80.0     81.0  
   576x432        82.0     83.0     84.0     85.0  
   512x384        86.0     87.0     88.0  
   416x312        89.0  
   400x300        90.0     91.0     92.0     93.0  
   320x240        94.0     95.0     96.0
```

Any idea how I can debug this further?

---

### Post by MaX on 2008-08-19
You need to force the driver

---

### Post by wiscalico on 2008-08-19
> **MaX said:**
> You need to force the driver

How is that done?

---

### Post by RAOF on 2008-08-19
You want to enable TwinView.  nVidia doesn't support xrandr1.2, which does it multi-head stuff.

A simple
```

sudo nvidia-xconfig --twinview

```
should suffice.

---

### Post by TheMono on 2008-08-19
Yep, the joy of using a non-open source driver. Not to judge, I do it myself!

However, Nvidia's nvidia-settings has quite a nice display configuration thing. if you run in a terminal:
sudo nvidia-settings 
that will give you plenty to play with. As non-open stuff goes, Nvidia's configuration utilities are pretty good.

---

### Post by wiscalico on 2008-08-20
> **RAOF said:**
> You want to enable TwinView.  nVidia doesn't support xrandr1.2, which does it multi-head stuff.

Ah thanks... didn't realize xrandr isn't supported.

---

### Post by MaX on 2008-08-20
> **wiscalico said:**
> How is that done?

I assumed you knew since you wrote that yourself :)

Writing Driver "nvidia" in xorg.conf forces X to use that driver.
And as the others said, you probably want twin-view.

---

### Post by drjimmy42 on 2008-08-21
This definitely explains what I'm seeing.  I had the same problem where xrandr would only see the default output and not the other ones from my docking station.  

So quick question:

With my old t43p with the open source ATI cards, xrandr was a champ.  It noticed my two external monitors and I wrote a script to disable the laptop screen and enable the other two when I docked and the opposite when I undocked.  It was amazingly good. Almost like having a mac :-)

now with my new T61p and the binary nvidia driver, compiz works well, resume suspend is fine, but this xrandr thing means that I can't do the dynamic monitor switching like I used to. 

I know I can use nvidia-settings to turn on twinview and save it in my xorg.conf file permanently, but is there any way to switch it from single laptop to dual external and back dynamically?

thanks a lot.

---

### Post by TheMono on 2008-08-21
Not... Really. That I know of.

The way I used to do it in pre randr2 days was to have two xorg.confs and switch them via a script. But this requires restarting X each time.

I think with Nvidia you'll have to do things the windows way - ie, open a gui every time you want to change something.

---

