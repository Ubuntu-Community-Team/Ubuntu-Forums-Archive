---
title: "Dapper, Edgy, Feisty - none of them will install!"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by yzord on 2007-06-19
Well, I certainly hope someone can help me. None of the past three livecd discs have worked for me.

Specs:
AMD 2800+
MSI K8T Neo
7600GT (AGP)
20" Dell
300GB SATA, 200GB IDE, 120GB IDE

As soon as the boot sequence is finished (ie. all the modules have loaded and it switches to the live desktop), the screen becomes a garbled mess (with various ghost images of what was in the video cache). I hear the startup sound from ubuntu, and then it crashes. Obviously (?) it's a video card problem - but I specifically bought this damn card because everyone and his uncle told me that Nvidia was more reliable in Linux!!! I used to have an ATI 9700 which is now long gone.

No amount of cajoling has ever made a difference. I've tried: Safemode (all discs), setting the VGA res to any and all, taking out xforcevesa from the safemode install, nosplash -quiet to see if any other modules are dying (nope). Nothing works. I've succesfully installed from all three as well (on other computers/laptops), so I'm certain it's not disc-related problems (I've also done disc checks anyway, with no issues).

I've avoided the Alternate install, because I can't be sure if it'll ever work with this freakin' card!
Any suggestions would be greatly appreciated.

---

### Post by dabl on 2007-06-19
Make sure your BIOS is current.  This problem may or may not be video related.  Here's what I turned up on that motherboard -- some of the items listed could explain a problem completing the boot sequence:

[http://www.planetamd64.com/lofiversion/index.php?f33.html](http://www.planetamd64.com/lofiversion/index.php?f33.html)

---

### Post by dabl on 2007-06-19
Check out this thread: [http://ubuntuforums.org/showthread.php?t=459433](http://ubuntuforums.org/showthread.php?t=459433)

Maybe installing the xserver-xorg-video-intel package will fix it (of course, you've got to get to a text login to run apt-get ....).

---

### Post by yzord on 2007-06-19
Thanks for your responses, Dabl.
The BIOS is already updated as far as it can go, so I don't think that's it. As well, most of the problems seem more related to memory issues (ie, RAM problems) or use of the Promise SATA controller (I don't use it). As far as RAM is concerned, I prime95 the crap out of my computers for at least a couple of days before I begin using it, so I'd know if the RAM was flaky.

As for your second post, the examples in that thread have to do with laptops running the Intel 965GM integrated video chipset. In my case, I have an Nvidia 7600GT card - not Intel, so it doesn't apply. Doubly so, in that I can't even get it to the point I could try installing anything!

Every other computer I have has been converted, except the one I use the most! [/irony]

---

### Post by longlegs on 2007-06-21
Hi,
I have observed that ubuntu from 6.06 to 7.04 pays no attention to the resolution selected on the first install screen and further that all default to the highest resolution the video card can handle, regardless of the monitors capability. The result is that if you just installed a Nvidia card with hi performance, using a monitor not so high, then the screen is garbled. You may be able to  boot to to safe mode and set the max resolution down to what your monitor can handle by editing the /etc/X11/xorg.conf file. This will limit the resolution and perhaps get rid of the garble. 
Good luck
longlegs

---

