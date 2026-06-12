---
title: "need help getting black screen"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by lobokun on 2006-06-10
ok im new at this so hopefully anyone can help me cuz im getting really frustrated. =\
well i installed ubuntu 6.06 or tried too. i followed this instrcutions step by step 
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
for dual booting. everything when ok until i finished partitioning the HD. you know when after u partition your HD either manually or auto you get to the last part where everything is downloading to your computer. first bar which was installing the base system went ok. second bar which was configuring apt when ok as well. but when it got to the last bar which was select and install software when it went about 58% my screen went black with like 2 white bars. i thought it was normal so i waited about an hour an nothing so i tried to hit esc, enter and stuff. nothing. anyways i tried installing like 2 times and it stopped at 60% and the black screen came up. plz help me ><

---

### Post by kagashe on 2006-06-10
[QUOTE=lobokun]ok im new at this so hopefully anyone can help me cuz im getting really frustrated. =\
well i installed ubuntu 6.06 or tried too. i followed this instrcutions step by step 
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
for dual booting. everything when ok until i finished partitioning the HD. you know when after u partition your HD either manually or auto you get to the last part where everything is downloading to your computer. first bar which was installing the base system went ok. second bar which was configuring apt when ok as well. but when it got to the last bar which was select and install software when it went about 58% my screen went black with like 2 white bars. i thought it was normal so i waited about an hour an nothing so i tried to hit esc, enter and stuff. nothing. anyways i tried installing like 2 times and it stopped at 60% and the black screen came up. plz help me ><[/QUOTE]
I was facing this problem and solved it.
Try this command at "boot:" prompt.
install debian-installer/framebuffer=false

I don't remember exactly how I reached "boot:" prompt but it was by fressing one of the "F" keys.

kagashe

---

### Post by lobokun on 2006-06-10
hmm ok thanx hopefully this fixes my problem ..

---

### Post by pbrockway2 on 2006-06-11
Thanks kagashe - I had the same problem and the framebuffer setting was
effective in allowing the installation to complete.

I was using kubuntu alternate CD and, as lobokun described, about 60% of 
the way through the "select and install software" process (while xserver is 
being configured) I ended up with a screen with nothing but two "block" 
cursors; one on the lefthand side and one in the middle, both 1/3 of the way 
down the monitor.

You get at the boot settings by pressing F6 at the first screen.

---

