---
title: "Sound not working in clean install of Ubuntu 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Kushal S. Pandya on 2010-10-14
Hello everyone,

I've made a clean install of Ubuntu Maverick in my Acer Aspire 4930 laptop previously running 10.04 (absolutely fine). I ran Maverick in live session but sound didn't worked and, I thought installing it physically on drive might make it work. But after installation, it didn't worked. I ran ```
lspci -v | less
``` and found that my sound is detected and, I got following information.

```


00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 013e
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at 98800000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


```

I found somewhere on the web about similar problem, and as per solution shown in the thread, I added ```
options snd-hda-intel model=ref
```
at the end of file ```
/etc/modprobe.d/alsa-base.conf
```. But, still sound is not working at all. After installation, Update manager showed Kernel update, so updated to that as well, but nothing seem to work. Please, help me out...................... :(

---

### Post by g01an on 2010-11-22
without being an expert, I recommend to check on alsa modules installation. i've google it a little and no specific tutorial helps to determine the problem. I see that some fox lost sound after updating the kernel, some, just like me had sound not working after install and so on. 

basically the solution is keep your drivers up-to-date. i've checked in synaptic for all sound components and after choosing all that seem to be related to ALSA (except dev, including backports - aren't probably related) that wouldn't affect other components problem was solved. But that meant installing more then 83 packages :D. 

however some seem more related than others like: 
 libesd-alsa0
 alsa-tools-gui
 lib32asound2
 libasound2
 libasound2-plugins
 libclalsadrv1
linux-backports-modules-alsa-2.6.32-25-generic (note i have linux-2.6.32.25-generic installed)

+ might improve or be related / but not that sure

 libesd-alsa0
 libao2

+ these were also installed, but don't know if I have chosen them or they were installed before:
 
 linux-sound-base
 
 + this must defintely be checked:
 pulseaudio

Apart from these , I have installed some plugins, mixers, players and of course, the packages' above dependencies.

Could you please experiment and single out if one of  lib32asound2,  libasound2,  libasound2-plugins does the job? (before installing the rest that is; for my peace of mind or others that run into this).

Thanks, let us know.

---

### Post by efflandt on 2010-11-22
For model=**ref**, what did you fill in for **ref**?  That usually refers to a specific model if you are having trouble with use of headphone jack not knocking out the speakers on a laptop. [http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD)

What shows up in Hardware and Output tabs of Sound Preferences?

What devices show for **aplay -l** and in **alsamixer**?

---

### Post by Kushal S. Pandya on 2010-11-23
> **g01an said:**
> without being an expert, I recommend to check on alsa modules installation. i've google it a little and no specific tutorial helps to determine the problem. I see that some fox lost sound after updating the kernel, some, just like me had sound not working after install and so on. 

basically the solution is keep your drivers up-to-date. i've checked in synaptic for all sound components and after choosing all that seem to be related to ALSA (except dev, including backports - aren't probably related) that wouldn't affect other components problem was solved. But that meant installing more then 83 packages :D. 

however some seem more related than others like: 
 libesd-alsa0
 alsa-tools-gui
 lib32asound2
 libasound2
 libasound2-plugins
 libclalsadrv1
linux-backports-modules-alsa-2.6.32-25-generic (note i have linux-2.6.32.25-generic installed)

+ might improve or be related / but not that sure

 libesd-alsa0
 libao2

+ these were also installed, but don't know if I have chosen them or they were installed before:
 
 linux-sound-base
 
 + this must defintely be checked:
 pulseaudio

Apart from these , I have installed some plugins, mixers, players and of course, the packages' above dependencies.

Could you please experiment and single out if one of  lib32asound2,  libasound2,  libasound2-plugins does the job? (before installing the rest that is; for my peace of mind or others that run into this).

Thanks, let us know.



Hi, thanks for your response, by the way I've solved sound issue many days ago (Geeks can't tolerate imperfection... ;-) ) But before that, I filed bug in launchpad, you can have a look at [_this_]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/661340") thread which also includes solution that I did.

---

