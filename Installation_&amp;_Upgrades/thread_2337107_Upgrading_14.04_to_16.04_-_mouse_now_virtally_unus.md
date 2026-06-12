---
title: "Upgrading 14.04 to 16.04 - mouse now virtally unusable"
date: 2016-09-14
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2016-09-14
I upgraded today and have had system errors reported.

Now the mouse is behaving erratically, stopping and starting, sometime unresponsive to clicks.

I am using it left handed and in it's settings it shows as right handed. Changing the setting has no effect.

---

### Post by makem2 on 2016-09-14
I remembered changing mouse properties as shown on page 4 of this thread I followed some while ago to change mouse settings to left handed. I repeated the install of the file .Xmodmap and it re-appeared complete with its previous setting. The mouse is so far working correctly again.

[URL="https://ubuntuforums.org/showthread.php?t=2328815&highlight=makem"]https://ubuntuforums.org/showthread.php?t=2328815&highlight=makem


[/URL]

---

### Post by #&amp;thj^% on 2016-09-14
Good job ;)... I was going to remind you of that.

---

### Post by makem2 on 2016-09-14
Well it is not a full success I am afraid.

I am using Gimp to manipulate an image and the mouse becomes unusable again. I am unable to drag for example. The mouse seems to work for a few seconds and then hesitates, stops moving and stops being able to scroll.

There is obviously something deeper than that setting. I am wondering about mouse driver.

I noticed that when I re-booted to see if that made a difference, the machine seemed very slow restarting and the border around the screen when Grub comes up hesitated before fully drawing the rectangle.

Edit: Outside of Gimp, the mouse performs normally and quickly.

---

### Post by #&amp;thj^% on 2016-09-14
I see that at times myself in gimp... and have a decent powered system.
Then most of the time just works smoothly.
```
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB 
           clock speeds: max: 2600 MHz 1: 800 MHz 2: 800 MHz 3: 1400 MHz
           4: 1900 MHz
Graphics:  Card: NVIDIA GF106 [GeForce GTS 450]
           Display Server: X.Org 1.18.4 driver: nvidia
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTS 450/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 370.28

```
But in trusty everything was smooth and crisp. No lags.

---

### Post by makem2 on 2016-09-14
I see.
Iwas wondering if it maybe the mouse driver which had been changed.

---

### Post by makem2 on 2016-09-14
> **1fallen said:**
> I see that at times myself in gimp... and have a decent powered system.
Then most of the time just works smoothly.
```
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB 
           clock speeds: max: 2600 MHz 1: 800 MHz 2: 800 MHz 3: 1400 MHz
           4: 1900 MHz
Graphics:  Card: NVIDIA GF106 [GeForce GTS 450]
           Display Server: X.Org 1.18.4 driver: nvidia
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTS 450/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 370.28

```
But in trusty everything was smooth and crisp. No lags.

Is there a single command which gives that information?

---

### Post by makem2 on 2016-09-14
I found:

```

makem@ssdTOSH:~$ cat /proc/cpuinfo | grep vendor | uniq
vendor_id    : GenuineIntel
makem@ssdTOSH:~$ cat /proc/cpuinfo | grep 'model name' | uniq
model name    : Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz
makem@ssdTOSH:~$ lscpu | grep -i mhz
CPU MHz:               2400.093
CPU max MHz:           3000.0000
CPU min MHz:           500.0000
makem@ssdTOSH:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 61
Model name:            Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz
Stepping:              4
CPU MHz:               1865.062
CPU max MHz:           3000.0000
CPU min MHz:           500.0000
BogoMIPS:              4788.98
Virtualisation:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              4096K
NUMA node0 CPU(s):     0-3
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap xsaveopt dtherm ida arat pln pts
makem@ssdTOSH:~$ cat /proc/cpuinfo | grep 'processor'
processor    : 0
processor    : 1
processor    : 2
processor    : 3
makem@ssdTOSH:~$ 


```

---

### Post by #&amp;thj^% on 2016-09-14
> **makem2 said:**
> Is there a single command which gives that information?

Sorry I was taking a nap...lol
inxi will do that.
If not installed already..you can use 
```
sudo apt install inxi
```
Very light weight && more info for inxi: [http://www.binarytides.com/inxi-system-information-linux/](http://www.binarytides.com/inxi-system-information-linux/)
For the command that I used to show what you see is
```
inxi -CG
```
C=CPU info
G=Gpu info
Fxz=Whole system info

---

### Post by RobGoss on 2016-09-14
Is this a wireless mouse you're using? when I first started using Ubuntu I had problems with my wireless mouses so I switch to a wired mouse and it seem to fix what ever was wrong

I still use my wireless mouse on the machine that was giving me problems with the wireless mouse so I think it might have been something that need to be updated over time it seem to get sorted out on it's own

I try searching the forums for answers for this issue and could not really fine the correct answer

---

### Post by makem2 on 2016-09-14
Well, I have just been using a web page to download recorded
iPlayer programs and the mouse really was a pain. Almost a waste of time trying.

It id a wireless mouse with which I never had any problem (except left/right handedness), until this upgrade. It has to be related to that.

---

### Post by makem2 on 2016-09-14
> **1fallen said:**
> Sorry I was taking a nap...lol
inxi will do that.
If not installed already..you can use 
```
sudo apt install inxi
```
Very light weight && more info for inxi: [http://www.binarytides.com/inxi-system-information-linux/](http://www.binarytides.com/inxi-system-information-linux/)
For the command that I used to show what you see is
```
inxi -CG
```
C=CPU info
G=Gpu info
Fxz=Whole system info

Ah, a nap is allowed ;)

I will try inxi thanks.

---

### Post by makem2 on 2016-09-14
```

makem@ssdTOSH:~$ inxi -CG
CPU:       Dual core Intel Core i7-5500U (-HT-MCP-) cache: 4096 KB 
           clock speeds: max: 3000 MHz 1: 2400 MHz 2: 2400 MHz 3: 2400 MHz
           4: 2402 MHz
Graphics:  Card-1: Intel Broadwell-U Integrated Graphics
           Card-2: NVIDIA GM108M [GeForce 930M]
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.02hz
           GLX Renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2)
           GLX Version: 3.0 Mesa 11.2.0
makem@ssdTOSH:~$

```

I just had a terrible job trying to copy that output with the mouse sticking.

I need to go back if that was possible. Or maybe a reinstall as I cannot put up with this.

Edit: Just went to look at page 1 of this thread and eventually could get the mouse over 2 to return but was unable to select it! 30 seconds or so later the mouse was active again and I could select page 2. Took another 30 secounds to save the edit.

---

### Post by makem2 on 2016-09-14
Installed the Nvidia driver instead of the open source one. Ran software updater which complained of being unable to install anything. Suggested a partial re-install to fix things after an incomplete upgrade. Did that but no effect on mouse. Still feel its driver related because when the mouse stops moving the scroll wheel works. Can;t submit this post now :(

---

### Post by makem2 on 2016-09-15
Well it seems to have been a dodgy USB port.

I changed the mouse, batteries and finally USB ports today. Only changing the port made a difference. So far so good, I have a usable mouse again.

I do notice that the dongle seems loose when plugged into that particular port and I only used that port just before the upgrade.

---

