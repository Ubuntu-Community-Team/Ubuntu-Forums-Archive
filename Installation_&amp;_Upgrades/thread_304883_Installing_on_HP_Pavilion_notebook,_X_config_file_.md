---
title: "Installing on HP Pavilion notebook, X config file error"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by kerzane on 2006-11-22
The CD boot fails to launch X.

The Error is as follows:

"

Unable to locate/open config file

xf86AutoConfig: Primary PCI is 1:5:0

"

then there is the details of a failed getconfig command.

Then

"

Fatal server error:

Cannot run in framebuffer mode. Please specify bus IDs   for all.

Any help will be greatly appreciated.

regards,
Eoin.

---

### Post by kerzane on 2006-11-22
Ok, maybe more info is needed.

I reboot my computer with the cd in.
I arrive at the ubuntu menu and select "Start or install Ubuntu"
It begins to boot, seems to get pretty far, things are flying down the screen with "[OK]"s on the right hand side.
Then after a while, the screen goes blank with a flicking cursor in the top left hand corner.
This persists for a time (10-20 seconds) and then some error messages build up on the screen (I have unfortunately forgotten these).
Then screen goes bluey and I get a colouredy dialog box of sorts telling me X failed to launch.
It gives me the option of seeing the output of the X operation, which tells me the stuff in the previous post.
It then brings me back to the text screen with the error messages, at which point I have to press CTRL+ALT+DEL to undo the whole process and exit Ubuntu. It shutsdown succesfully.

Is my CD just faulty?

Any help would be great, thanks alot.

Regards,
Eoin.

---

### Post by kerzane on 2006-11-22
Now I have a CRC error!!

Ok,

turns out I was making a very stupid error. Was trying to boot the 32-bit distribution on my AMD64 chip. I assume that's where my error came from.

However, now that I'm being far cleverer and booting the correct 64-bit distribution, I'm ot getting half as far as I was.

I get to the initial menu, select boot Ubuntu, and then it begins.
As soon as the little green dots are finished running across the top of the screen I get:

"
Decompressing Linux...done.
Booting the kernel.

[   33.936006] PCI: Cannot allocate resource region 7 of bridge 0000:00:4.0
[   33.936049] PCI: Cannot allocate resource region 8 of bridge 0000:00:4.0
[   34.312447] crc error
[   34.312254] Kernel panic - not syncing: VFS: Unable to mount roots fs on unknown wn-block(1,0)
[   34.313296]
"

I tried to see if this problem has ocurred for otheer people,
it seems related to the issues discussed at:

[www.colug.net/pipermail/colug432/2006-September/003467.html](www.colug.net/pipermail/colug432/2006-September/003467.html)

and

[http://www.ubuntuforums.org/archive/index.php/t-186115.html](http://www.ubuntuforums.org/archive/index.php/t-186115.html)

Please help me out. I can't think of what I can do. I can provide any necessary info.

Regards,
Eoin.

---

### Post by kerzane on 2006-11-23
](*,) 

Please guys,

I really need some help with this. Somebody out there must know the solution to this problem or at least have an idea. If not, somebody just tell me it's hopeless and I'll try another distribution.

Eoin.

---

