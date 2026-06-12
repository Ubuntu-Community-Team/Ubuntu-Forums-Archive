---
title: "Graphics Driver Selection Issue (Nvidia)"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jeggen on 2010-04-10
System has a NVIDIA Quadro FX 570M graphics card on a HP 8510w.

I had been using the proprietary Nvidea driver but wanted to try out the nouveau driver since the Nvidea one does not support the Gnome brightness controls, which is hard on battery life.  I have used smartdimmer but would want something that is integrated into gnome.

Now I am stuck in some sort of limbo.
In System -> Admin -> Hardware Drivers I have three options listed
[LIST]
[*]Nvidia accelerated graphics driver v 173
[*]Nvidia accelerated graphics driver (version current)
[*]nvidia riva/tnt/geforce
[/LIST]

I assume that the last one, is the nouveau driver.
When I select each one the first (173) says it is not activated.  Nvidia current says "a different version of this driver is in use" and the riva/tnt/geforce says "this driver is active but not currently in use."

If I try to activate nvidia current the system says that installation failed.  (Attached is zip of /var/log/jockey.log)  After attempting to activate it the system then says that nvidia current "this driver was just disabled, but is still in use."  When I restart the listing goes back to its previous state (nvidia current has different version in use.)

Then I tried disabling the nvidia riva/tnt/geforce driver and restarting.  Now this driver says it is not activated, but nvidia current is active w/ different version.  So I tried activating this one to see if restart would switch to this driver, but no luck.  After activating and restarting I get the same list as originally.

I also tried editing xorg.conf to the nouveau settings but then could only boot into low graphics mode.
```
Section "Device"
Identifier "n"
Driver "nouveau"
EndSection

```

Working xorg.conf is:
```
Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```


Any suggestions would be appreciated.  I would at least like to know what driver I am using, but even more so would like integrated brightness control.

---

### Post by Breambutt on 2010-04-10
Nevermind.

---

### Post by dino99 on 2010-04-10
> **jeggen said:**
> System has a NVIDIA Quadro FX 570M graphics card on a HP 8510w.

I had been using the proprietary Nvidea driver but wanted to try out the nouveau driver since the Nvidea one does not support the Gnome brightness controls, which is hard on battery life.  I have used smartdimmer but would want something that is integrated into gnome.

Now I am stuck in some sort of limbo.
In System -> Admin -> Hardware Drivers I have three options listed
[LIST]
[*]Nvidia accelerated graphics driver v 173
[*]Nvidia accelerated graphics driver (version current)
[*]nvidia riva/tnt/geforce
[/LIST]

I assume that the last one, is the nouveau driver.
When I select each one the first (173) says it is not activated.  Nvidia current says "a different version of this driver is in use" and the riva/tnt/geforce says "this driver is active but not currently in use."

If I try to activate nvidia current the system says that installation failed.  (Attached is zip of /var/log/jockey.log)  After attempting to activate it the system then says that nvidia current "this driver was just disabled, but is still in use."  When I restart the listing goes back to its previous state (nvidia current has different version in use.)

Then I tried disabling the nvidia riva/tnt/geforce driver and restarting.  Now this driver says it is not activated, but nvidia current is active w/ different version.  So I tried activating this one to see if restart would switch to this driver, but no luck.  After activating and restarting I get the same list as originally.

I also tried editing xorg.conf to the nouveau settings but then could only boot into low graphics mode.
```
Section "Device"
Identifier "n"
Driver "nouveau"
EndSection

```

Working xorg.conf is:
```
Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```


Any suggestions would be appreciated.  I would at least like to know what driver I am using, but even more so would like integrated brightness control.

you are not alone, and some devs are working on already  #-o

---

### Post by mc4man on 2010-04-10
I find it very simple to switch from nvidia-current to nouveau and back again using update-alternatives. (don't think I ever have opened "Hardware Drivers - to initally use nvidia-current just simply - 
sudo apt-get install nvidia-current
sudo nvidia-xconfig
reboot

To switch back to nouveau from nvidia-current using the alternatives see here
[http://ubuntuforums.org/showthread.php?t=1423210](http://ubuntuforums.org/showthread.php?t=1423210)

To switch back I use the same except don't mv the xorg, run sudo nvidia-xconfig instead

---

### Post by jeggen on 2010-04-10
I did and noticed that the nvidia current is listed twice.  Wonder if that is part of the problem.

```
There are 2 choices for the alternative gl_conf (providing /etc/ld.so.conf.d/GL.conf).

  Selection    Path                                Priority   Status
------------------------------------------------------------
  0            /usr/lib/nvidia-current/ld.so.conf   9700      auto mode
  1            /usr/lib/mesa/ld.so.conf             500       manual mode
* 2            /usr/lib/nvidia-current/ld.so.conf   9700      manual mode

Press enter to keep the current choice[*], or type selection number: 
```

I had to run the commands on this post:
[http://ubuntuforums.org/showthread.php?t=1423210](http://ubuntuforums.org/showthread.php?t=1423210)

When I try to run nvidia-xconfig i just get command not found.  
```
sudo: nvidia-xconfig: command not found
```
Is this part of a package?

---

### Post by jeggen on 2010-04-10
BTW - that worked to switch... now I remember why I went back to the Nvidia drivers: nouveau drivers result in a black screen after resuming from standby, so I just have to restart after every suspend.  Brightness control or standby/resume?  Hopefully it will be a both/and rather than an either/or someday soon!

---

### Post by MarkieB on 2010-04-11
no longer participating in ubuntuforums.org

---

### Post by wit on 2010-04-12
Same problem here on HP laptop. Getting a lil' bit frustrated...

---

### Post by TunaCanTommy on 2010-04-12
Same problem here with a desktop running a nVidia GeForce 6200 ((NV44).
I found some relief by black-listing nouveau, at least until the Jockey issues get worked out.

Edit: Looks like my problem got fixed with a Jockey update this morning (4/12). I now have a "green-button" in Jockey saying the Nvidia Current driver is installed and working. I took Nouveau off black-list. Rebooted three times and everything seems to be working OK.  Checked Nvidia Settings and it shows 195.36.15 is installed.

---

