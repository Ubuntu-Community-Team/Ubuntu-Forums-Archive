---
title: "[SOLVED] Compatible NVidia driver not found after updates in Intrepid"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Zachx65 on 2008-09-24
Hi, first post here. Hopefully it's in the right place. 

I've got an HP Slimline s3123w which I had been dual booting Vista/Hardy Heron. About three days ago I upgraded to Intrepid, and everything was running smoothly. I booted up tonight, opened update manager and saw there were about 350 updates, so I let them install and then rebooted. Came up with an error

```
(++)log file /var/log/xorg.failsafe.log
(++)using config file: /etc/x11/xorg.conf.failsafe
(EE) Failed to initialize GLX extension (Compatible NVidia X driver not found
```

Video card is GeForce 6150 LE
I had/have driver 177 installed, tried activating it, and nothing happens.

I hope I provided enough information, thanks!

---

### Post by Zachx65 on 2008-09-25
> **Zachx65 said:**
> Hi, first post here. Hopefully it's in the right place. 

I've got an HP Slimline s3123w which I had been dual booting Vista/Hardy Heron. About three days ago I upgraded to Intrepid, and everything was running smoothly. I booted up tonight, opened update manager and saw there were about 350 updates, so I let them install and then rebooted. Came up with an error

```
(++)log file /var/log/xorg.failsafe.log
(++)using config file: /etc/x11/xorg.conf.failsafe
(EE) Failed to initialize GLX extension (Compatible NVidia X driver not found
```

Video card is GeForce 6150 LE
I had/have driver 177 installed, tried activating it, and nothing happens.

I hope I provided enough information, thanks!

Hate to make my second post a bump of my first, hopefully there are more people viewing now than when I originally posted.

---

### Post by F for Fragging on 2008-09-27
Hi, I've been doing a lot of searching around the forum because I had the same problem with Intrepid. I have two boxes, one with a NVIDIA 7800 GT GPU and one with a NVIDIA 7600 GPU which didn't load the closed source NVIDIA drivers, even though I had the driver package 177 installed.  I didn't find any solution, but in the end I managed to get it working this way:

[LIST=1][*]Open Synaptic, search for packages with the name "nvidia", make sure that only *nvidia-glx-177* is installed together with it's dependencies.
[*]Open *System &#8594; Administration &#8594; NVIDIA X Server Settings*. On my box it detected that the NVIDIA driver wasn't in use – the open source "nv" driver was – and told me I had to enter *sudo nvidia-xconfig* in a terminal if I remember correctly.
[*]Do so, and it will modify the configuration file */etc/X11/xorg.conf*. I was running without an xorg.conf file, so I didn't back up the old one.
[*]Then enter in a terminal the command *gksudo gedit /etc/X11/xorg.conf*, which will open xorg.conf in gedit. Comment out the line *Load "type1"* by placing a # in front of that line. Elsewhere on the forums here I read that was necessary to get it working, but I'm not sure because I didn't try it without commenting out that line.
[*]Now restart, and everything should be working O.K. If you open *System &#8594; Administration &#8594; NVIDIA X Server Settings* now it shouldn't complain about the NVIDIA driver not being loaded, and Compiz should work.[/LIST]
All I know is that I managed to get it working this way, I'm not sure if this will work for you at all. Another solution could be to do a clean install with one of the latest daily builds of Ubuntu 8.10, or the beta which will be released on 2 October. Hopefully when you do a clean install, the NVIDIA GPU will be automatically detected and it's driver automatically downloaded and installed.

---

### Post by Zachx65 on 2008-09-27
> **F for Fragging said:**
> Hi, I've been doing a lot of searching around the forum because I had the same problem with Intrepid. I have two boxes, one with a NVIDIA 7800 GT GPU and one with a NVIDIA 7600 GPU which didn't load the closed source NVIDIA drivers, even though I had the driver package 177 installed.  I didn't find any solution, but in the end I managed to get it working this way:

[LIST=1][*]Open Synaptic, search for packages with the name "nvidia", make sure that only *nvidia-glx-177* is installed together with it's dependencies.
[*]Open *System &#8594; Administration &#8594; NVIDIA X Server Settings*. On my box it detected that the NVIDIA driver wasn't in use – the open source "nv" driver was – and told me I had to enter *sudo nvidia-xconfig* in a terminal if I remember correctly.
[*]Do so, and it will modify the configuration file */etc/X11/xorg.conf*. I was running without an xorg.conf file, so I didn't back up the old one.
[*]Then enter in a terminal the command *gksudo gedit /etc/X11/xorg.conf*, which will open xorg.conf in gedit. Comment out the line *Load "type1"* by placing a # in front of that line. Elsewhere on the forums here I read that was necessary to get it working, but I'm not sure because I didn't try it without commenting out that line.
[*]Now restart, and everything should be working O.K. If you open *System &#8594; Administration &#8594; NVIDIA X Server Settings* now it shouldn't complain about the NVIDIA driver not being loaded, and Compiz should work.[/LIST]
All I know is that I managed to get it working this way, I'm not sure if this will work for you at all. Another solution could be to do a clean install with one of the latest daily builds of Ubuntu 8.10, or the beta which will be released on 2 October. Hopefully when you do a clean install, the NVIDIA GPU will be automatically detected and it's driver automatically downloaded and installed.

Cool, I'll keep this saved in my inbox in case something else goes wrong. I actually had three driver packages installed 173, 177, and another earlier one. When I tried activating 177(which was recommended), nothing happened. So I installed and activated 173 which seems to have fixed things.

---

