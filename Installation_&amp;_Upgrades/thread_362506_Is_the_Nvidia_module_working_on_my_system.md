---
title: "Is the Nvidia module working on my system?"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by pschalkx on 2007-02-15
Hi guys,

This might seem like a strange question: after searching through Nvidia related posts in this forum, I still don't have a clue of whether my Nvidia 6150 is installed and working on my system.
I installed standard 6.10, on a brand new PC with an AMD 64 with 1 GB of RAM and the built in Nvidia 6150.

I did not (yet) tweak the installation, apart from allowing for automatic upgrades. 
Video works fine, no problem after reboots or anything strange. 

However, in looking at how objects move on the screen, it seems to me that may be hardware acceleration is not turned on: you can see windows a they are redrawn on the screen. I don't do games tough.

Synaptic tells me that the Linux restricted modules and nvidia-kernel-common are installed.

How do I know if the NVidia card drivers are installed and properly configured?

Do I need to install different drivers than those that came with the system?

Cheers,

Philip

---

### Post by Sqwishy on 2007-02-15
try running in the terminal.
glxgears -printfps
if it doesn't work you probobly don't have them, and you should get like 4k fps i think

---

### Post by IgnorantGuru on 2007-02-15
If you didn't install the proprietary driver, you're still using the open source driver.  Good enough for most things except 3D games, google earth, etc.

nvidia-glx is the proprietary driver package.

I only get 1500 fps from glxgears.  :(  But I don't have a trendy card.  Nice test though.

---

### Post by pschalkx on 2007-02-17
Hi guys,

I tried the glsgears test and only get 400 fps (so, very sloooowww.
What's the recommended way to install, so that the drivers stay current, even when I let the system get automatic upgrades?

Cheers,

Philip

---

