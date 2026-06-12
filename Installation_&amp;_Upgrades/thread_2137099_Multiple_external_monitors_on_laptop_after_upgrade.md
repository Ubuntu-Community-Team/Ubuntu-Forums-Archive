---
title: "Multiple external monitors on laptop after upgrade from 10.04 to 12.04"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by eanema on 2013-04-19
Hi Folks,

I have a problem. I upgraded my work computer from 10.04 to 12.04 and after a brief issue with grub, I now have my computer up and running. My problem is that when I was running 10.04 The two 24" displays I had connected to the laptop worked fine. I could not have all three displayes up at once, but I don't really care about having my laptop display up when I'm at my desk. In 10.04 I would see all three displays detected in the "Moniters" section but only two of them could be on at once. 

now, in 12.04, I only have 2 screen options, the VGA and the laptop screen - I can't get my second monitor connected through DVI/Display Port to be detected.

xrandr retrieves this information:
```
$ xrandr
Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192
LVDS1 connected 1366x768+1920+312 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+   50.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 298mm
   1920x1080      60.0*+
   1280x1024      60.0  
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```

and I have an Intel graphics card:
```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

```

I added the ppa:ubuntu-x-swat/x-updates repository and upgraded my X-server but still no love. I would really like to get this working... and so would my boss. My productivity is falling! ;)

Thanks for any help :)

FYI, this is a Lenovo T510... if that means something to anyone

---

