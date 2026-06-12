---
title: "Change Monitor Resolution/Refresh Rates in 10.10"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2010-10-11
Just installed Ubuntu 10.10 "Maverick Meerkat".

Install went through smoothly in both my laptop and an old Dell Optiplex GX 270.

Screen looks fine on laptop but terrible on the Dell. It's stuck on Refresh rate of 60Hz and flickers pretty bad. 60Hz is the only rate offered! How can I change the refresh rate to ~65-72Hz like is possible on earlier Ubuntu versions to ease eye strain?

---

### Post by xtremo on 2010-10-11
I need the fix for this one as well.....any help appreciated guys! :)

---

### Post by kansasnoob on 2010-10-11
We'll need to know the exact graphics card model so please post the output of:

```
lspci | grep VGA
```

Also, assuming it was better in a previous version of Ubuntu it might help you to compare the outputs of:

```
xrandr
```

Or you may need to look at "/var/log/Xorg.0.log" to see what driver is actually being used.

---

### Post by cybrsaylr on 2010-10-11
Here's the output kansasnoob:

> bb@bb-OptiPlex-GX270:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)


bb@bb-OptiPlex-GX270:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
DVI-I-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
TV-1 disconnected (normal left inverted right x axis y axis)
bb@bb-OptiPlex-GX270:~$ 


32 bit 10.04 ran fine on this Dell with no flicker after moving to a higher refresh rate than 60Hz.
However 32 bit 10.10 flickers bad and only 60Hz refresh rate is available.


PS:
Just remembered this. Both Firefox and Opera browsers load pages slow again. This seems to happen after every time I upgrade to a newer version of Ubuntu. Suspect it is an IPv6 issue again. Once IPv6 is disabled browsers load pages very fast again. Anyone have the code to correct this issue for 10.10?

---

### Post by kansasnoob on 2010-10-11
You may or may not be effected by this bug:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974)

Are you using the Nouveau or Nvidia driver?

I use Intel and VIA/Openchrome so I'd best leave this to an Nvidia pro :)

> Just remembered this. Both Firefox and Opera browsers load pages slow again. This seems to happen after every time I upgrade to a newer version of Ubuntu. Suspect it is an IPv6 issue again. Once IPv6 is disabled browsers load pages very fast again. Anyone have the code to correct this issue for 10.10?
2 Hours Ago 08:29 AM

It's best to start a new thread for each separate issue.

---

### Post by cybrsaylr on 2010-10-11
kansasnoob,

Not sure if the Nouveau or Nvidia driver is being used.
How can I find out?

Started a new thread on the possible IPv6 issue.

---

### Post by cybrsaylr on 2010-10-12
Bump.

Can anyone help me change refresh rates here in MM?

---

### Post by tatjana on 2010-11-02
I would really like  to know the answer for changing resolution for intel card. More specifically for Intel Corporation 82G33/G31 Express Integrated Graphics Controller. I need to go up to 1440x900 but the maximum offered (which I currently use is) is 1360x768.

---

