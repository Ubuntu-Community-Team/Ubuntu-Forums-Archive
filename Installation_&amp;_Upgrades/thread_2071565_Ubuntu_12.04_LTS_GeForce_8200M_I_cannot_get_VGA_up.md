---
title: "Ubuntu 12.04 LTS GeForce 8200M I cannot get VGA up or HDMI"
date: 2012-10-15
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2012-10-15
I also I am trying to get working VGA and HDMI on 12.04 and none of them work.

If I do:

```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768       50.0* 
   1360x768       51.0  
   1024x768       52.0     53.0  
   960x540        54.0  
   840x525        55.0  
   832x624        56.0  
   800x600        57.0     58.0     59.0     60.0     61.0  
   800x512        62.0  
   720x450        63.0  
   720x400        64.0  
   700x525        65.0  
   680x384        66.0     67.0  
   640x512        68.0     69.0  
   640x480        70.0     71.0     72.0     73.0     74.0  
   640x400        75.0  
   640x350        76.0  
   576x432        77.0     78.0     79.0     80.0     81.0     82.0     83.0  
   512x384        84.0     85.0     86.0     87.0     88.0  
   416x312        89.0  
   400x300        90.0     91.0     92.0     93.0     94.0  
   360x200        95.0  
   320x240        96.0     97.0     98.0     99.0  
   320x200       100.0  
   320x175       101.0  


```


lspci | grep VGA

```

02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 8200M G] (rev a2)


```

aplay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

Could you please help?

Thanks

---

