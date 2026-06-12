---
title: "driver installation help..."
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by franpa on 2006-10-13
ok, i got a soundblaster x-fi xtreme gamer soundcard... dunno where to go for drivers for it... (havnt looked yet)

i got a nvidia geforce 6600gt pcie video card and have looked but found no ubuntu or x86 compliant drivers...

pentium 4 3.0ghz ht
p5ld2 standard motherboard
onboard network
onboard usb 2.0
plus other stuff that i cant think of at the moment...


----

bottom line... where do i go to get what i want? and why is it not possible to manualy search for updates to firefox via the help menu?

me = linux n00b :)

---

### Post by Kateikyoushi on 2006-10-13
By following [this guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") you can make your soundcard work.

---

### Post by franpa on 2006-10-13
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

theres no drivers for me :(

where to get drivers for my video card? this is more important to me then the sound at the moment... all i saw on nvidia's website that was close was the IA32 drivers but they are not x86.

---

### Post by Coelocanth on 2006-10-14
> **franpa said:**
> [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

theres no drivers for me :(

where to get drivers for my video card? this is more important to me then the sound at the moment... all i saw on nvidia's website that was close was the IA32 drivers but they are not x86.

Check out the [Drivers](http://www.nvidia.com/object/linux_display_ia32_1.0-8774.html) again. The driver file is named:

NVIDIA-Linux-x86-1.0-8774-pkg1.run

which I think is a good indication they're the x86 drivers.

---

### Post by franpa on 2006-10-14
thanks... what does IA32 stand for then? industry architecture 32?

---

### Post by Kateikyoushi on 2006-10-14
It means [Intel Architecture 32bit.]("http://en.wikipedia.org/wiki/IA-32")

---

### Post by franpa on 2006-10-14
oooh, i was close but no cigar... thanks a ton... if i can use my .net passport on gant or whatever then id like to have someone to talk to to provide live linux support :)

---

### Post by franpa on 2006-10-14
how the hell do i install it... they say type "sh NVIDIA-Linux-x86-1.0-8774-pkg1.run" but i have no clue where to type that... i tried the terminal (i have no clue how to use that as its commands are different to DOS) and it just said no such path/folder.

i saved the driver on my desktop.

-----

ok how do i get to root access? i am the only account on here... how? as it is needed to install it.

---

### Post by Kateikyoushi on 2006-10-14
Then open a terminal type 
```
cd Desktop
```

This changes the directory to your desktop
Now run it.

```
sh NVIDIA-Linux-x86-1.0-8774-pkg1.run
```

---

### Post by franpa on 2006-10-14
ok, i placed it in home and ran it from terminal and it says i need root access... how the bloody hell do i get root access?

give me a step by step method of installing the freakin' drivers... i got it to run... it said it was decompressing it... then it loaded up and said "you must have root access to install this"

i am a linux n00b... i got the disc yesterday for ubuntu linux and this is my first time using it... i am getting pissed at this linux the more i try to do stuff on it... (this is the only linux i have and have ever used)

---

### Post by tseliot on 2006-10-14
> **franpa said:**
> ok, i placed it in home and ran it from terminal and it says i need root access... how the bloody hell do i get root access?

give me a step by step method of installing the freakin' drivers... i got it to run... it said it was decompressing it... then it loaded up and said "you must have root access to install this"

i am a linux n00b... i got the disc yesterday for ubuntu linux and this is my first time using it... i am getting pissed at this linux the more i try to do stuff on it... (this is the only linux i have and have ever used)
Try Method 1 of my guide:
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

---

### Post by Kateikyoushi on 2006-10-14
you can have root access by typing sudo before a command. [Explanation.]("https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29")

So try this.

```
sudo sh NVIDIA-Linux-x86-1.0-8774-pkg1.run
```

Unfortunately I can't give ou a step by step installation guide because I do not have nvidia chip in my machine, sorry.

---

### Post by franpa on 2006-10-14
i am completely lost...

no problemo Kateikyoushi.

---

### Post by franpa on 2006-10-14
ok, sudo worked... (i now know what sudo is) how do i get packages? i need the binutils package in order to install the drivers.

[is it something related to "sudo apt get"? (explanation of thos commands would be appreciated aswell...)]

----------

edit: geez support is slow... unless someone is willing to help me live! then i dont think i will be able to install the damn drivers before tomorrow ends... 

gant (or what ever its called) closes a couple of seconds after logging in and there is no visible error message... why?

---

### Post by franpa on 2006-10-15
below is how you install them... thanks go to aysiu.

- - - - - - - - - - - - - - - - - - - - - - - - - -  -  -  -  -  -  -  -  -

    * How to install Graphics Driver (NVIDIA)

```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
```

    * Should the above not enable the new driver, you can enable it manually by opening the X config file: 

```
sudo gedit /etc/X11/xorg.conf
```
 

    * and replacing "nv" with "nvidia" 

    * reboot linux

    * Enable XvMC by creating the nVidia XvMC configuration file 

```
sudo gedit /etc/X11/XvMCConfig
```

    * Insert the following line into the new configuration file, to tell the players the name of the nVidia XvMC shared library: 

```
libXvMCNVIDIA_dynamic.so.1
```

    * To use XvMC to accelerate video playback, use the following flags. See [[1]] for more details. 

```
xine -V xxmc filename.ts
mplayer -vo xvmc -vc ffmpeg12mc filename.ts
```

---

