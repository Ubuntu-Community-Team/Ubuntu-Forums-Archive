---
title: "RAWR! The new Intel video driver is buggy."
date: 2008-11-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2008-11-27
It works, but only in a not-so-low-graphics mode through BulletproofX.

works completely: xserver-xorg-video-intel 2:2.4.1-1ubuntu11
works somewhat: xserver-xorg-video-intel 2:2.5.1-1ubuntu1

os[Linux 2.6.28-rc5-candela i686] 

distro[Ubuntu "jaunty" 9.04] 

cpu[2 x Genuine Intel(R) CPU T2050  @ 1.60GHz (GenuineIntel) @ 1.60GHz] 

mem[Physical: 995.8MB, 55.8% free] disk[Total: 128.0GB, 72.6% free] 

video[Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller] 

sound[HDA-Intel - HDA Intel]

---

### Post by klange on 2008-11-27
Install libdrm-intel1.
You will find it is quite slow when it actually is working.

---

### Post by Starks on 2008-11-27
> **WindowsSucks said:**
> Install libdrm-intel1.
You will find it is quite slow when it actually is working.

Heh. Unmarked dependency.

---

### Post by Starks on 2008-11-27
Hmmm. New xv output modes. Nice.

But I still want my GEM!

---

### Post by klange on 2008-11-28
> **Starks said:**
> Hmmm. New xv output modes. Nice.

But I still want my GEM!

I just hope the GEM benchmarks that said "30% increase in overall speed, 50% increase in texture speeds" weren't based on this particular release.

**e**: [I reported the unmarked dependency](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/303177).

---

### Post by ShirishAg75 on 2008-11-28
I am guessing this is the reason why my X wouldn't start . 

This is from my /var/log/Xorg.0.log
[http://pastebin.com/f69067ad0](http://pastebin.com/f69067ad0)

Also put my comment on the bug as well.

Update :- I got the login screen but my keyboard was out . So its back to going to recovery, and hoping one of the updates will fix that :)

Seems we need a new Mesa and a new kernel for the circle to complete. I dunno when we will have both these things. 

Also it would be interesting to see how well it works with an ancient integrated graphics chip such as mine. 

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

```

---

### Post by DougieFresh4U on 2008-11-29
> **ShirishAg75 said:**
> I am guessing this is the reason why my X wouldn't start . 






Also it would be interesting to see how well it works with an ancient integrated graphics chip such as mine. 

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

```

I have a working machine,(sound works as well) but things are a bit 'jumpy' and high CPU usage.
```
 lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
 
```

---

