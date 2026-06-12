---
title: "Get Orange thick lines instead of desktop"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by kanolsen on 2010-05-03
I just upgraded to jaunty from karmic, and everything worked fine until I restarted. Now I see the purple ubuntu logo for a second then I get just orange thick lines instead of the desktop. It seems like there's five old brown/orange desktops crammed into one. 

I have a Nvidia N7600GS graphicscard which I haven't gotten to work in 3d mode since 9.04. 

Hope anybody can help
Thanks in advance
Kanolsen

---

### Post by quixote on 2010-05-04
When you say you "upgraded to jaunty (9.04) from karmic" and then mention the purple screen, you probably mean you upgraded to lucid (10.04) from karmic (9.10)?  The boot process fails at the point where it starts the graphical windowing system, so it's a graphics driver issue.

Assuming you're using lucid, I'd try searching for "Nvidia N7600GS Lucid Ubuntu" (without quotes) to see what solutions other people have come up with.

I had to move to a computer with an Nvidia Quadro NVS 135M, and Lucid worked on it out of the box.  They use a new open source driver now, called "nouveau", which for me works much better than the actual nvidia drivers.  There's more about it [here]("http://nouveau.freedesktop.org/wiki/UbuntuPackages").

---

### Post by kanolsen on 2010-05-05
I am truly sorry for confusing more than helping. 

I meant that I have upgraded to the newest version 10.04.

Thank you, will check up and hope I get it to work.

Kanolsen

---

