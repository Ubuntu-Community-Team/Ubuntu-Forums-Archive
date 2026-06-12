---
title: "problems with 1920x1200 resolution"
date: 2024-02-14
forum: Installation &amp; Upgrades
---

### Post by ValentynPrumers on 2024-02-14
Dell XPS 9720 laptop. Fresh 23.10 install. Ubuntu correctly selects the 1920x1200 resolution. And everything seems to work. But when I start
dragging windows around i notice a very slight wobbly movement. Its not much,but def isnt smooth.

When i select 1920x1080 the window dragging goes smooth without any wobblyness (lol).

I tried both the Nouveau display driver (installed by default) as several nvidia drivers (535 and 545). But no luck in getting 1920x1200 to
run super smooth.

Video card: nvidia RTX 3050 mobile.

---

### Post by #&amp;thj^% on 2024-02-14
I'm not a Gnome user, but are you sure your card correctly supports that resolution?
```
 xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
eDP connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080    120.21*+ 120.00    96.00    72.03    60.00  
   1680x1050    120.21  
   1280x1024    120.21  
   1440x900     120.21  
   1280x800     120.21  
   1280x720     120.21  
   1024x768     120.21  
   800x600      120.21  
   640x480      120.21  

```
Same card:
```
Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] driver: N/A

```
```
prime-select query
on-demand

```
And are you on a wayland session?

---

### Post by ValentynPrumers on 2024-02-14
```

[FONT=monospace][COLOR=#000000] xrandr -q [/COLOR]
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 16384 x 16384 
eDP-1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 366mm x 229mm 
   1920x1200     59.95*+  47.96   
   1920x1080     59.95   
   1600x1200     59.95  
[/FONT]
```[FONT=monospace]

I am pretty sure the video card ([/FONT] NVIDIA GeForce RTX *3050* )[FONT=monospace] supports this resolution. What do you mean by wayland? 
[/FONT]

---

### Post by #&amp;thj^% on 2024-02-14
Wayland is a new graphics server, to check please show this:
```
inxi -G | grep Display
  Display: x11 server: X.Org v: 21.1.11 driver: X: loaded: amdgpu

```
I'm using "x11" and on Gnome systems there is an option for both.

And yep you do have that resolution 1920x1200.

---

### Post by ValentynPrumers on 2024-02-14
```
 inxi -G | grep Display[FONT=monospace][COLOR=#ff5454]**Display**[/COLOR][COLOR=#000000]: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 23.2.0 driver: X:[/COLOR][/FONT]
``` Something weird is going on. Suddenly i cant select the nvidia drivers anymore in the driver manager. They are 
all grayed out. Only thing selected is: manual installed driver. Previously that entry was "Nouveau driver" and all the nvidia drivers could be selected (which i also did).

---

### Post by #&amp;thj^% on 2024-02-14
What shows with:
```
nvidia-smi
```
also this:
```
apt list nvidia-driver* --installed

```

---

### Post by ValentynPrumers on 2024-02-14
I reinstalled the nvidia driver with:
```
 s[FONT=monospace][COLOR=#000000]udo ubuntu-drivers install[/COLOR] [/FONT]
```[FONT=monospace]

And after that the nvidia drivers were available again. 

[/FONT]```
[FONT=monospace]

[/FONT][FONT=monospace][COLOR=#000000]+---------------------------------------------------------------------------------------+ [/COLOR]
| NVIDIA-SMI 535.154.05             Driver Version: 535.154.05   CUDA Version: 12.2     | 
|-----------------------------------------+----------------------+----------------------+ 
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC | 
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. | 
|                                         |                      |               MIG M. | 
|=========================================+======================+======================| 
|   0  NVIDIA GeForce RTX 3050 ...    Off | 00000000:01:00.0 Off |                  N/A | 
| N/A   42C    P3              N/A /  30W |      7MiB /  4096MiB |      0%      Default | 
|                                         |                      |                  N/A | 
+-----------------------------------------+----------------------+----------------------+ 
                                                                                          
+---------------------------------------------------------------------------------------+ 
| Processes:                                                                            | 
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory | 
|        ID   ID                                                             Usage      | 
|=======================================================================================| 
|    0   N/A  N/A      1143      G   /usr/lib/xorg/Xorg                            4MiB 
[/FONT]
```[FONT=monospace]
[/FONT][FONT=monospace]
[/FONT]```
[FONT=monospace][COLOR=#000000]Listing... Done [/COLOR]
[COLOR=#18b218]nvidia-driver-535[/COLOR][COLOR=#000000]/mantic-updates,mantic-security,now 535.154.05-0ubuntu0.23.10.1 amd64 [installed] [/COLOR]
[COLOR=#b26818]N: [/COLOR][COLOR=#000000]There is 1 additional version. Please use the '-a' switch to see it[/COLOR]

[/FONT]
```[FONT=monospace]


[/FONT]

---

### Post by #&amp;thj^% on 2024-02-14
So Now is it a bit smoother?

---

### Post by ValentynPrumers on 2024-02-14
No, But then i opened nvidia settings and selected performance mode instead of on demand. Reboot and now it suddenly runs smooth.

```

[FONT=monospace][COLOR=#000000]+---------------------------------------------------------------------------------------+ [/COLOR]
| NVIDIA-SMI 535.154.05             Driver Version: 535.154.05   CUDA Version: 12.2     | 
|-----------------------------------------+----------------------+----------------------+ 
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC | 
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. | 
|                                         |                      |               MIG M. | 
|=========================================+======================+======================| 
|   0  NVIDIA GeForce RTX 3050 ...    Off | 00000000:01:00.0 Off |                  N/A | 
| N/A   43C    P8               4W /  30W |    258MiB /  4096MiB |      0%      Default | 
|                                         |                      |                  N/A | 
+-----------------------------------------+----------------------+----------------------+ 
                                                                                          
+---------------------------------------------------------------------------------------+ 
| Processes:                                                                            | 
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory | 
|        ID   ID                                                             Usage      | 
|=======================================================================================| 
|    0   N/A  N/A      1167      G   /usr/lib/xorg/Xorg                          117MiB | 
|    0   N/A  N/A      1605      G   /usr/bin/ksmserver                            1MiB | 
|    0   N/A  N/A      1607      G   /usr/bin/kded5                                1MiB | 
|    0   N/A  N/A      1608      G   /usr/bin/kwin_x11                            40MiB | 
|    0   N/A  N/A      1642      G   /usr/bin/plasmashell                         27MiB | 
|    0   N/A  N/A      1666      G   ...c/polkit-kde-authentication-agent-1        1MiB | 
|    0   N/A  N/A      1946      G   ...86_64-linux-gnu/libexec/kdeconnectd        1MiB | 
|    0   N/A  N/A      1958      G   /usr/bin/kaccess                              1MiB | 
|    0   N/A  N/A      1962      G   ...-linux-gnu/libexec/DiscoverNotifier        1MiB | 
|    0   N/A  N/A      1995      G   /usr/bin/dolphin                              1MiB | 
|    0   N/A  N/A      2055      G   ..._64-linux-gnu/libexec/kf5/kioslave5        1MiB | 
|    0   N/A  N/A      2061      G   /usr/bin/systemsettings                      25MiB | 
|    0   N/A  N/A      2110      G   /usr/bin/konsole                              1MiB | 
+---------------------------------------------------------------------------------------+



```
[/FONT]

---

### Post by #&amp;thj^% on 2024-02-14
Nice Good job...and the smi return looks better as well

Plus I see your on Kubuntu and not Gnome, hence the "Xwayland v: 23.2.0 driver: X:"

That should now also read differently...with:
```
inxi -G | grep Display
```

---

### Post by ValentynPrumers on 2024-02-14
Thanks for your help!

---

### Post by #&amp;thj^% on 2024-02-14
You did the heavy lifting, and glad to be of help

---

