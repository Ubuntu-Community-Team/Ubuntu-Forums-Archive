---
title: "Disabling NVidia Powermizer"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mrphd on 2009-04-17
In intrepid I was able to disable the nvidia powermizer by adding:

```
options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"

```

to the file, /etc/modprobe.d/options

I did this because I was getting black screen flashes whenever powermizer changed performance levels.

In jaunty RC this options file does not exist. Does anyone know how i can impose this setting, as the black flashes are driving me crazy!...

thanks,

---

### Post by SketchyClown on 2009-04-17
If you are using a laptop you might find this thread useful:

[http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

This little tutorial allows you to set the Power Mizer to always be at Level 3 430/400 Mhz when the computer is on AC power, but reverts back to auto when on battery.

Works flawlessly on my laptop with 9600M.

---

### Post by pferraro on 2009-04-17
> **SketchyClown said:**
> If you are using a laptop you might find this thread useful:

[http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

This little tutorial allows you to set the Power Mizer to always be at Level 3 430/400 Mhz when the computer is on AC power, but reverts back to auto when on battery.

Works flawlessly on my laptop with 9600M.

This is a bit hacky IMO.  It works by leveraging a quirky nvidia-settings behavior that forces the gpu to full power for several seconds when nvidia-settings is loaded.  Ideally you shouldn't have to burden your cpu with unnecessary load in this way.  Here's what's worked for me (using the latest 185.19 beta):

Add the following option to your xorg.conf file under the device section:
```
Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
```

This places the gpu in max perf mode when on AC, and reverts to gpu scaling on battery.

---

### Post by SketchyClown on 2009-04-17
> **pferraro said:**
> This is a bit hacky IMO.  It works by leveraging a quirky nvidia-settings behavior that forces the gpu to full power for several seconds when nvidia-settings is loaded.  Ideally you shouldn't have to burden your cpu with unnecessary load in this way.  Here's what's worked for me (using the latest 185.19 beta):

Add the following option to your xorg.conf file under the device section:
```
Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
```This places the gpu in max perf mode when on AC, and reverts to gpu scaling on battery.

Sounds like your offer does exactly the same thing. Except with a different approach.

The end result seems exactly the same.

**EDIT:** I've tested ***pferraro's*** option and confirm it works. The end result is exactly the same as the tutorial. GPU temps are fine. I have removed the hack from the tutorial and decided to leave the xorg hack in place.

---

### Post by pelle.k on 2009-04-17
I recommend you read this. the web page does a good job at explaning what the options actually do.
[http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/)
A couple of examples;
>     *** on battery - max power saving, on AC - max performance**

          "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x1"

    *** on battery - max power saving, on AC - adaptive strategy (my favorite)**

          "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3"

    *** on battery - adaptive strategy, on AC - max performance**

          "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"

    *** adaptive strategy for any power source**

          "PowerMizerEnable=0x1; PerfLevelSrc=0x3333"


Every number apart from PerfLevelSrc= are specific to your GPU though, **so dont copy the exmaples verbatim and expect it to work**, but read the link i provided.

---

