---
title: "Problem installing Xubunto for an old Toshiba satellite"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by alessandro.aresi on 2006-08-26
Hi all,

i've got a problem in installing xubuntu on a old toshiba satellite.
I can run xubuntu from livecd, but the screen resolution is 640x480. 
I try to install xubuntu anyway, i cannot use the visual installation procedure (the six windows) becouse I'm not able to click on the bottom below  the windows. 
I've tried also to install ubuntu server but I've a lot of problem to the sturtup of the kernel, in particoulr the sistem rebout contineously without boot anything.

If someone has an idea.

thanks
ale

---

### Post by az on 2006-08-26
> **alessandro.aresi said:**
> Hi all,

i've got a problem in installing xubuntu on a old toshiba satellite.
I can run xubuntu from livecd, but the screen resolution is 640x480. 

That's because you do not have enough video memory to use the maximum resolution at the maximum color depth.  The solution is to reconfigure X to only use 16-bit color (or even 15-bit).

You can then get 800x600.  (depending on your model, maybe 1024x768 if it supports it)

> **alessandro.aresi said:**
> 
I try to install xubuntu anyway, i cannot use the visual installation procedure (the six windows) becouse I'm not able to click on the bottom below  the windows. 
I've tried also to install ubuntu server but I've a lot of problem to the sturtup of the kernel, in particoulr the sistem rebout contineously without boot anything.

If someone has an idea.

thanks
ale

The server kernel does not work on a 386, only 686 or better.  You would have better luck using the alternate cd.

---

### Post by alessandro.aresi on 2006-08-26
thank's for answer.

bat why puppy, or DSL works and xubuntu not, and were can I find the alternate cd?

thanks
ale

---

