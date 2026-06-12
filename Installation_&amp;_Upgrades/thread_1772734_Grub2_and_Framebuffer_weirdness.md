---
title: "Grub2 and Framebuffer weirdness"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by Gideon on 2011-06-01
Been having alsorts of weird issues, and a couple of frustrations.

Firstly, the hardware setup. Radeon HD 5770, 22" Asus lcd monitor, 1680x1050 resolution.

The big problem I have is that grub, and then the rest of the framebuffer afterwards, are all shifted about an inch and a half to the right, so there's a big gap to the left of the screen, and everything trails off the right, and I can't get this to behave.

Even worse, I checked grub's vbeinfo command, and apparently there are no widescreen resolutions (1680x1050 for this, or, when I do it, 1280x800 for my laptop) supported. Now, I know for a fact a number of people have got these resolutions working, both on grub, and in framebuffer, and all of them basically say "I plugged the details into /etc/defaults/grub, and it just worked." I can't persuade it to work. 

The question then becomes, if the basic fb that grub is now using can't support them, is there one that can, and if so, how do I get grub itself to use it, rather than having the menu one way, and the later scroll another. 

I was hoping that fixing the resolution issue would fix the offset issue.

---

