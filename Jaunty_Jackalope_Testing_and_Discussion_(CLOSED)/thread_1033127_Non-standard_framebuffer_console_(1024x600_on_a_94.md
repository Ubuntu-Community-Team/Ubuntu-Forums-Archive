---
title: "Non-standard framebuffer console (1024x600 on a 945GME)"
date: 2009-01-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by luke.varnadore on 2009-01-07
I have scoured the net for days now looking for the answer for this. I have an MSI Wind U100 with an Intel 945GME chipset running Jaunty Jackalope, the framebuffer drivers were all commented out in /etc/modprobe.d/blacklist-framebuffer. I tried the intelfb driver and settled on uvesafb with the v86d installed along side of it. I was able to get a better resolution out of the framebuffer but it is still not correct. I understand that kernel-mode switching will be replacing these tools but I know that what I want can be done: 

hxxp://lists.alioth.debian.org/pipermail/debian-eeepc-devel/2008-September/001114.html

All that being said there are package conflicts with 915resolution and the intel driver. If I could use the 915resolution tool I believe I could get away with hacking the framebuffer into 1024x600. But alas, this is not the case. Also, I see options in the manpages for fb.modes and fbset that accommodate non-standard video modes. I can't find enough information to know what these are for. I do have a mode set in fb.modes for 1024x600 created by gtf. Fbset modesetting fails with 

"ioctl FBIOPUT_VSCREENINFO: Invalid argument"

And using the intelfb driver in the grub boot line fails with "cannot acquire agp."

I am in this one for the long haul. Anything that I can do to help this get fixed I will do.

Please let me know if I am missing something here.

---

### Post by cariboo on 2009-01-07
Graphics drivers are quite broken in Jaunty at the moment. There is a new xserver and none of the latest drivers support it yet. I have asked the mods to move this to Jaunty testing and discussion, where you may get better help.

Jim

---

### Post by sdennie on 2009-01-07
Moved to Jaunty discussions

---

### Post by luke.varnadore on 2009-01-07
Please, by all means. Anything will help, I am not assuming anything is "broken". And since this is development, it really doesn't matter. What can I try? This is an interesting topic, the views are jumping fast. Or maybe thats just ubuntuforums.

---

### Post by ShirishAg75 on 2009-01-07
The drivers are indeed broken. The only thing I know is this [http://ubuntuforums.org/showthread.php?t=1024573](http://ubuntuforums.org/showthread.php?t=1024573) 

Frankly, do not know if they would help you or not but you are welcome to give them a try.

---

### Post by luke.varnadore on 2009-01-07
Framebuffer console: fbcon, intelfb, uvesafb.

I am running the newest intel driver for Xorg and it screams, it works absolutely perfectly and with nice speed. I am talking about the usu. black and white F1 - F5 or whatever screens.

I will post a picture when I get home so you guys can see what I'm talking about.

---

### Post by lswb on 2009-01-07
> 
And using the intelfb driver in the grub boot line fails with "cannot acquire agp."


There is a longstanding problem with the intelfb driver in that it is not compiled with the proper flags to force the loading of the intel-agp module that it depends on. So you need to load that module yourself. Beyond that, there are many reports of intelfb not working with lcd/laptop monitors (Never could get it working on my own laptop with Intel 855 graphics)  but maybe you can get past that.

Also I am not certain about JJ but in some other versions of ubuntu you need to load the modules through the initram image so they are available early in the boot process. This link describes how, to try the intelfb driver just substitute it where vesafb is used, and add intel-agp to the list of modules. [http://lwasserm.freeshell.org/ubuntu/fb.shtml](http://lwasserm.freeshell.org/ubuntu/fb.shtml)

As far as setting the resolution to 1024X600, I have only played with the vesafb driver myself so I can't help there. You might find something in some of the links on the website above.

---

### Post by luke.varnadore on 2009-01-15
Look what I found: 

[http://translate.google.com/translate?prev=&hl=en&ie=UTF-8&u=http%3A%2F%2Fm0squito.blogspot.com%2F2008%2F11%2F1024x600-msi-wind-asus-eeepc.html&sl=ru&tl=en&history_state0=](http://translate.google.com/translate?prev=&hl=en&ie=UTF-8&u=http%3A%2F%2Fm0squito.blogspot.com%2F2008%2F11%2F1024x600-msi-wind-asus-eeepc.html&sl=ru&tl=en&history_state0=)

It can be done. That is on Debian, the 915resolution package is unavailable in JJ because of a conflict with the xorg driver. I'm not sure what needs to be done about this but I don't know how I can mimic that behaviour in Ubuntu.

PROBLEM FIXED! All you have to do is enable kernel modesetting in Karmic Koala and VOILA!

---

