---
title: "Changing Kernal Interupt Timer????????"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by kdxrider9262 on 2007-08-16
Hello,

Im trying to run a linux css server....Im using ubuntu-server 6.06 with xfce4 desktop......ANYWAY I can get the server to run fine and everything but I cant push the server past 50 fps......there are some guides about how to make it go further but im a but of a linux n00b and dont understand what they are talking about........I was told from a counter-strike source forum that I need to recompile my kernal to 1000hz.......but I have NO idea how to do that.........HELP>>>

Thanks in advance
Steve

---

### Post by ddrichardson on 2007-08-16
You need to provide at least a link to where you were told this. I can't see any reason to set  an interrupt timer to 1MHz, which would be every 1 ms, and cannot really see without more information why this would significantly speed a servers performance.

Please remember to avoid acronyms and text speak - a lot of us on Ubuntu don't have English as a first language.

---

### Post by kdxrider9262 on 2007-08-16
[http://forums.srcds.com/viewtopic/4953](http://forums.srcds.com/viewtopic/4953)

[http://forums.steampowered.com/forums/showthread.php?t=486424](http://forums.steampowered.com/forums/showthread.php?t=486424)

Sorry, I didn't realize about the english thing

---

### Post by ddrichardson on 2007-08-16
It is generally advised not to build your own kernel in ubuntu, however you do have a specific need.

There are a couple of good guides, one [here]("https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29"), [here]("https://help.ubuntu.com/community/Kernel/Compile") and [here.]("http://www.howtoforge.com/kernel_compilation_ubuntu")

You must be aware however that with a custom kernel you can't post bug reports on it.

The process is fairly straightforward, download the source and the required dependancies (linux-kernel-devel and build-essential), build a menuconfig, select what you need as part of the kernel and as modules and deselect what you don't. Then build and install, adding a new grub entry.

In fact the second link you gave is a pretty good guide, except it doesn't mention the required dependancies.

Keeping your current kernel and its grub entry is essential as there is bound to be a problem with your first attempt.

---

### Post by kdxrider9262 on 2007-08-16
well I thank you for your help but it looks like Im gonna have to stick to server 2003 for my counter strike server needs......I am not experienced enough in linux to do this........but for the record........what do I start with to compile a kernal?? freeBSD? all the guides tell me commands to do but what do I start with?

---

### Post by fredj on 2007-08-17
You start by downloading the kernel headers and source. You must also install the build-essential
package which contains the c++ compiler etc.
The low latency Ubuntu kernel  is a pre-compiled kernel which already contains a 1000hz timer.

---

### Post by kdxrider9262 on 2007-08-18
wow thanks for your help

---

