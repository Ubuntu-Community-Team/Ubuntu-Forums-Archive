---
title: "Executable unable to find libGL"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by patman0623 on 2011-11-15
I've just upgraded to 64 bit. I'm hoping to run an executable (it's not open source... I only have access to it in binary form). But it's giving me an error message I didn't receive on my 32 bit install:

```
error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

What can I do to install libGL? Also, I realize it may not work given that I'm running a 64-bit installation, and it's a 32-bit executable.

---

### Post by patman0623 on 2011-11-16
Did I post this in the wrong section? I'm not getting any responses, and I'd like to know where to post it if so.

---

### Post by patman0623 on 2011-11-21
bump?

---

### Post by MG&amp;TL on 2011-11-21
I am not entirely sure if 32-bit will run on 64-bit at present. I will google.

Secondly, install synaptic:

```
sudo apt-get install synaptic
```

The launch it and search for: "libGL"-this should work for any missing library, just chop the .so off the end.

---

### Post by patman0623 on 2011-11-21
> **MG&TL said:**
> "libGL"-trhis should work for any missing library, just chop the .so off the end.

I don't understand. Please clarify. 

There are a ton of libgl's.

---

### Post by azmyth on 2011-11-21
sudo apt-get install apt-file
apt-file update
apt-file search 'libGL.so.1'

Then install the package that it says you need. Could be more than 1. I usually install until the program runs.

---

### Post by MG&amp;TL on 2011-11-21
> **patman0623 said:**
> I don't understand. Please clarify. 

There are a ton of libgl's.

There is likely only one libgl(nothing).

If the program again complains of a missing library, search for it in synaptic without the .so file extension.

---

### Post by patman0623 on 2011-11-21
OK, I've located what I need. It's in ia32libs. However, it's in /usr/lib32/mesa/, and the system evidently isn't checking for .so's in that directory. What is the .so shared repository so that I can create a link?

> There is likely only one libgl(nothing).Actually there isn't. FYI.

---

### Post by MG&amp;TL on 2011-11-21
One of the places is /lib. My mistake, usually there is only one, and then a few libXYYYYYYYY. :)

---

### Post by patman0623 on 2011-11-21
> **MG&TL said:**
> One of the places is /lib. My mistake, usually there is only one, and then a few libXYYYYYYYY. :)Thanks a lot! Unfortunately, the program still won't run: error while loading shared libraries: libgtkglext-x11-1.0.so.0: wrong ELF class: ELFCLASS64

It looks like sudo apt-get install libgtkglext1 only installs a 64 bit version in /usr/lib, and ia32libs does not have a version. I will have to reboot and run it on another version of Ubuntu. :(

---

### Post by MG&amp;TL on 2011-11-22
:( Sorry I can't help more. 

Perhaps your software vendor will allow you to obtain a 64-bit version.

---

### Post by shervinemami on 2012-10-22
Sorry to bring back an old thread, but I also had a program (VirtualBox) saying that the file "libGL.so.1" is missing. In my case I solved the problem by upgrading the packages  "libgl1-mesa-glx" and "libgl1-mesa-dev" using Synaptic Package Manager. I  didn't even have to logout :-)

This was caused because I was in the middle of changing my graphics configuration, I had completely removed the default "nouveau" graphics driver from my system (containing an nVidia Optimus GPU) and I switched to the "intel" driver without hardware acceleration.

---

### Post by wildmanne39 on 2012-10-22
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

