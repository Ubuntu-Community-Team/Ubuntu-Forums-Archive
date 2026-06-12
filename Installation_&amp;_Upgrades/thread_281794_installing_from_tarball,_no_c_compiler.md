---
title: "installing from tarball, no c compiler"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by malfist on 2006-10-21
I was tring to install a program from it's tarball (it didn't offer a .deb or any other type of packaging) and I ran into a problem. ./configure reported no acceptable c compiler in $PATH 
I did echo $PATH and it reported it as being: /usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
For some reason I don't think that is meant as a path to gcc or anything like that.
What do I do? gcc is installed.

edit: also, when I type make install and make it says unknown bash 'make'

---

### Post by raul_ on 2006-10-21
That's weird. Do u have the gcc package installed on synaptic?

---

### Post by matthew on 2006-10-21
Install the package "build-essential" as well as "linux-headers-<your current kernel>" where you find the kernel headers for the kernel version you are running.

---

### Post by malfist on 2006-10-21
"Install the package "build-essential" as well as "linux-headers-<your current kernel>" where you find the kernel headers for the kernel version you are running."
What do you mean? GCC is installed. This is not a .deb so I can't run 'build-essential' and like make and make install it is not a recognized bash command. The first thing I did was check for GCC in the package manager. The program I'm trying to install is not in any of the repositories.

---

### Post by raul_ on 2006-10-21
But can u compile other programs or u haven't tried it?

---

### Post by malfist on 2006-10-21
I have compiled other programs but not on this machine. I recently reinstalled 5.10 because of network problems, but GCC is installed.

---

### Post by matthew on 2006-10-21
You are trying to install a piece of software from source. That means that it has to be compiled or "built." To do this there are several tools needed, not just the gcc compiler. All these tools are bundled together in an Ubuntu package called "build-essential." The way to install the software you want to install is to first use the Ubuntu repositories and install the tools you need so that you can build or compile the new software.

Open a terminal and type```
sudo apt-get install build-essential
```and enter your password when prompted. That should take care of you. If it does not, then install the headers for the kernel you are running currently by doing```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by malfist on 2006-10-21
You second line didn't work, was I supposed to replay uname with something? I'll try that in just a second.
I tried to configure it again and got:
checking for gtk+-2.0 >= 2.4 libpanelapplet-2.0 >= 2.0 gstreamer-0.8 gstreamer-gconf-0.8... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.4 libpanelapplet-2.0 >= 2.0 gstreamer-0.8 gstreamer-gconf-0.8) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


But as far as I can tell I have gtk2.0, atleast under package manager I have a much of gtk2 items selected and installed (engines, etc).

---

### Post by matthew on 2006-10-21
> **malfist said:**
> You second line didn't work, was I supposed to replay uname with something? I'll try that in just a second.No, just type this in a terminal...make sure you use ` (at the top left next to 1 on my keyboard) and not ' (next to enter on my keyboard). You can just cut & paste this in a terminal using ctrl-c to copy and ctrl-shift-v to paste in the terminal

```
sudo apt-get install linux-headers-`uname -r`
```Again, this particular step may not have been necessary anyway unless you are compiling a kernel module for a specific piece of hardware. Since you weren't specific on what you are trying to build I just thought I would cover that base.

> **malfist said:**
> I tried to configure it again and got:
checking for gtk+-2.0 >= 2.4 libpanelapplet-2.0 >= 2.0 gstreamer-0.8 gstreamer-gconf-0.8... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.4 libpanelapplet-2.0 >= 2.0 gstreamer-0.8 gstreamer-gconf-0.8 ) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

But as far as I can tell I have gtk2.0, atleast under package manager I have a much of gtk2 items selected and installed (engines, etc).I would also suggest you look at the list the error message is giving you and try installing the exact packages it names and see if that helps. In the meanwhile, it might be helpful to tell us precisely what you are trying to install.

---

### Post by malfist on 2006-10-21
istream-0.01
It's an internet radio streamer, I was haveing difficulties getting Totem and Rhythmbox to work with streaming music but I figured it out finally.

No, I'm not touching the Kernal, that's beyond me for the time being.

---

### Post by malfist on 2006-10-21
Bloody Depenadancy Hell!

Edit: My give up.

---

### Post by matthew on 2006-10-22
> istream-0.01Sorry it didn't work for you. I will note (hopefully to encourage you a little bit) that the version number of this program tells me it is the first-ever release designed solely for testing by people who know what they're doing...and that these releases rarely work well. In the 0.01 release only the basic framework tends to be implemented with lots of features missing or buggy. Anyway, don't feel too bad that you couldn't get it working (and I'm glad to hear you figured out a different way to tune in streams...you're probably better off anyway), the software probably wouldn't have worked well at this stage even if you had done everything perfectly.

---

### Post by malfist on 2006-10-22
I had noticed the version number after I downloaded it. Oh-well

---

