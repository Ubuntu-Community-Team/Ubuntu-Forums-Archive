---
title: "How should i install Ubuntu (and which version) to support my graphics card?"
date: 2017-09-26
forum: Installation &amp; Upgrades
---

### Post by babaliaris on 2017-09-26
Hello!

I'm not new to ubuntu but every time i'm returning to Windows only for one reason: I can't install properly the graphics drivers on Ubuntu! This problem is making me insane every time i install Ubuntu or any other Linux OS.
So i would like your help and if its possible to guide me step by step on how to install Ubuntu and the graphics drivers for my computer (and any other drivers that are required or adjustments). 

My computer spects:

[COLOR=#ff8c00]CPU :[/COLOR] [COLOR=#ff0000]AMD FX(tm)-6350 Six-Core Processor 3.90GHz[/COLOR]
[COLOR=#ff8c00]RAM :[/COLOR] [COLOR=#ff0000]8GB[/COLOR]
[COLOR=#ff8c00]GPU :[/COLOR] [COLOR=#ff0000]AMD Radeon R9 200 Series

[/COLOR]I tried the new version 6.0.4 but i could not install the drivers.

I already read the instructions of the AMD's documentantion on how to install the drivers but i could not make it!
If you can help me step by step i will be very happy :p

---

### Post by QIII on 2017-09-26
Hello!

If you are getting output to your monitor, then there is nothing further to do.  During the install, Ubuntu will determine whether to install Radeon or AMDGPU as appropriate for your hardware.

Cheers!

---

### Post by babaliaris on 2017-09-26
> **QIII said:**
> Hello!

If you are getting output to your monitor, then there is nothing further to do.  During the install, Ubuntu will determine whether to install Radeon or AMDGPU as appropriate for your hardware.

Cheers!
Then why I could not change the resolution? My monitor is full hd 1920x1080 and my GPU supports it, so why in Ubuntu display settings I have only two options? Also, does it support hardware acceleration? I want to try some video games too &#128541;

---

### Post by QIII on 2017-09-26
There could be any number of reasons.

First, let's check to see which driver is loaded.  Please post back the results of

```
lsmod | grep radeon
```

and 

```
lsmod | grep amdgpu
```

That will tell us which of the two driver modules is loaded.

---

### Post by babaliaris on 2017-09-27
> **QIII said:**
> There could be any number of reasons.

First, let's check to see which driver is loaded.  Please post back the results of

```
lsmod | grep radeon
```

and 

```
lsmod | grep amdgpu
```

That will tell us which of the two driver modules is loaded.

```

babaliaris@babaliaris-desktop:~$ lsmod | grep radeon
radeon               1507328  52
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    98304  2 amdgpu,radeon
drm_kms_helper        151552  2 amdgpu,radeon
drm                   352256  8 amdgpu,radeon,ttm,drm_kms_helper

```

```

babaliaris@babaliaris-desktop:~$ lsmod | grep amdgpu
amdgpu               1560576  0
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    98304  2 amdgpu,radeon
drm_kms_helper        151552  2 amdgpu,radeon
drm                   352256  8 amdgpu,radeon,ttm,drm_kms_helper

```

---

### Post by Bucky Ball on 2017-09-27
[This page]("https://help.ubuntu.com/community/RadeonDriver") may give you a few clues. Follow the instructions there and see what results you get. See if it makes things any clearer.

---

### Post by babaliaris on 2017-09-27
> **Bucky Ball said:**
> [This page]("https://help.ubuntu.com/community/RadeonDriver") may give you a few clues. Follow the instructions there and see what results you get. See if it makes things any clearer.

Well i installed the amdgpu-pro but still i can't change the resolution. The output of the installation is:
```

babaliaris@babaliaris-desktop:~/Downloads/amdgpu-pro-17.30-465504$ ./amdgpu-pro-install –y
deb [ trusted=yes ] file:/var/opt/amdgpu-pro-local/ ./
Get:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Ign:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [814 B]
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [814 B]
Get:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg                            
Ign:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg                         
Get:4 file:/var/opt/amdgpu-pro-local ./ Packages [72,4 kB]                  
Hit:5 http://gr.archive.ubuntu.com/ubuntu xenial InRelease                  
Get:6 http://gr.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:7 http://gr.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:8 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:9 http://gr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [633 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [60,2 kB]
Get:11 http://gr.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [605 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62,1 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [49,2 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [69,8 kB]
Get:15 http://gr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [305 kB]
Get:16 http://gr.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [212 kB]
Get:17 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [538 kB]
Hit:18 https://download.sublimetext.com apt/stable/ InRelease
Get:19 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [513 kB]
Get:20 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [172 kB]
Get:21 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [234 kB]
Get:22 http://gr.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5888 B]
Get:23 http://gr.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3328 B]
Get:24 http://gr.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [4588 B]
Fetched 3774 kB in 2s (1583 kB/s)                                     
Reading package lists... Done
E: Invalid operation –y

```

---

### Post by babaliaris on 2017-09-27
I found a temporary solution on the internet. I created this script:

[COLOR=#008000]video.sh[/COLOR] (in my home directory)
```

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DVI-1 1920x1080_60.00
xrandr --output DVI-1 --mode 1920x1080_60.00

```

"1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync was generated using ctv.

So every time i open my computer i need to run ./[COLOR=#008000]video.sh[/COLOR] , but i have to run it manually every time i open my computer.This works nice and sets my resolution to full HD. 
Also the log in screen is always at 1024x768 and i cant change that!!!

What are we going to do now?

---

### Post by Bucky Ball on 2017-09-27
Well, you could try installing arandr, a GUI for xrandr, and see if that offers you that HD resolution. If it does, set your screen up using arandr, save the setting in arandr, reboot and see if it boots to the correct resolution.

Or you could get your script to run at startup, but not absolutely sure how to do that without doing a little experimentation myself as haven't done anything like that in awhile. ;)

---

### Post by babaliaris on 2017-09-27
I just can't understand one thing. Why Ubuntu on installation doesn't take care this for me? And why it is so difficult to fix it &#128541; even experienced users can't help me solve it easily.

---

### Post by QIII on 2017-09-27
Ubuntu likely did take care of it for you, but you forced the installation of amdgpu as well as the Radeon driver that I suspect was installed by Ubuntu.  (I don't know if your hardware is supported by AMDGPU yet.  It is not listed as supported on AMD's website.  However, it is a GCN GPU, so I suspect it will be.  Please see my [blog article]("https://theleftcoastgeek.net/index.php/categories/12-possible-amdgpu-pro-supported-gpus-by-the-end") discussing this.)  I would be surprised to find that the two driver modules are not interfering with each other now.

Let me find out about AMDGPU support and we should be able to blacklist one or the other to see if this can be resolved.

By the way, my GPU is supported by AMDGPU and that is what was installed without a fuss at install time.  I subsequently installed the AMDGPU-PRO overlay without issue.

---

### Post by babaliaris on 2017-09-28
> **QIII said:**
> Ubuntu likely did take care of it for you, but you forced the installation of amdgpu as well as the Radeon driver that I suspect was installed by Ubuntu.  (I don't know if your hardware is supported by AMDGPU yet.  It is not listed as supported on AMD's website.  However, it is a GCN GPU, so I suspect it will be.  Please see my [blog article]("https://theleftcoastgeek.net/index.php/categories/12-possible-amdgpu-pro-supported-gpus-by-the-end") discussing this.)  I would be surprised to find that the two driver modules are not interfering with each other now.

Let me find out about AMDGPU support and we should be able to blacklist one or the other to see if this can be resolved.

By the way, my GPU is supported by AMDGPU and that is what was installed without a fuss at install time.  I subsequently installed the AMDGPU-PRO overlay without issue.

You're probably right about that so i uninstalled amdgpu pro. Anyway there is something wrong with my drivers because i can't run opengl based games. Take a look also at this:
```

babaliaris@babaliaris-desktop:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:c0000000-cfffffff memory:fea00000-fea3ffff ioport:e000(size=256) memory:c0000-dffff

```

---

### Post by babaliaris on 2017-09-28
Also, maybe this will help you a little.

I created a c program using SDL in order to see if it can work correctly with my video drivers.

Code:
```

#include <stdio.h>
#include <SDL.h>


int main()
{

    //Try initializing SDL.
    if ( SDL_Init(SDL_INIT_EVERYTHING) < 0 )
        printf("SDL could not initilize: %s\n\n", SDL_GetError());

    return 0;
}

```


Output:
```

babaliaris@babaliaris-desktop:~/Projects/c$ ./main
SDL could not initilize: No available video device

```

When SDL can't initialize this is probably because there is something wrong with the graphics drivers.

---

### Post by babaliaris on 2017-09-29
Anyway, i deleted ubuntu and windows and i installed arch linux , kde-plasma and ati drivers manually and everything works fine now. OpenGL works. I just had to make a script again to set the resolution with xrandr but its ok since i managed to make the script run on start up when i'm logging in. Thanks for the help.

---

### Post by Bucky Ball on 2017-09-29
All good. Please mark the thread as 'solved' by using Thread Tools at top-right of page.

---

