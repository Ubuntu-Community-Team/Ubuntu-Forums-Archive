---
title: "why does ubuntu STILL have problems with nvidia 6800gs?"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by had3z on 2007-02-05
i have a 6800gs on my pc, and i can't install ubuntu from a live cd because the image is scrambled. evan in safe graphics mode
kubuntu live cd works fine in safe graphics mode, but everything else is scrambled

why won't it work? i read the forums, and traced the problem to changing one "nv" into "vesa" in xorg.config file or something. why isn't something this trivial fixed? it's causing the users a lot of trouble, quit x, type some command line, change the parameter, restart x, bleah. i like ubuntu (installed it on my old duron), but i'm too lazy to do this hack in order to install it on my pc

oh, and my monitor - a samsung 959nf is not listed in the list. and it was among the best back in it's age, still beats many other lcd's or crt's

---

### Post by jd65pl on 2007-02-05
Try using the alternate install disk, this will give a command line install removing your problem with your graphics card.

---

### Post by reiki on 2007-02-05
As an nVidia user I have to say I agree that the driver install is still very lumpy. I realize that the proprietary stuff is left out of a basic install for a reason, but getting the latest driver SHOULD not be an issue. I've done it 3 times now and you'd think I'd learn. But each time I find myself rebooting, finding a text-only login screen, having to dpkg-reconfigure, still having problems, rebooting, editing xorg.conf, enabling the nvidia driver (nvidia-xconfig), still having issues, .... it's getting old. 

I know... "why don't you just use *this* tutorial?" or "why don't you just use *that* tutorial?"

Problem is there are too many tutorials in too many unofficial places. Not that they aren't good. People spend time on this stuff and many have done a nice job, but a google search finds way too many that are not relevant. I wanted to install the nvidia driver for Edgy.... not Dapper. Search through the google results to weed out the irrelevant ones. Lately I installed Kubuntu Edgy. Having not played with Kubuntu in the past I found LOTS of tutorials for Ubuntu but not for Kubuntu. You sorta have to guess your way through because the Ubuntu instructions reference stuff not IN Kubuntu. I got through it, but a new person with no previous experience would not get through it. I can darn near guarantee that.

And a graphics driver should be easy. VERY easy. 

Don't even get me started on Flash, w32codecs, ......  

If we want to see more people using Ubuntu (or ANY linux variant for that matter), then the simple stuff needs to be simple.

---

### Post by had3z on 2007-02-05
> Don't even get me started on Flash, w32codecs, ......


those are one thing, drivers and flash, the community has to wait on companies, but this is a simple choose driver x or driver y.
that one line makes installing ubuntu a mess, going through forums, reading lots of crappy advice, and than going into command line to fix stuff. after that, try expaining it to average joe that linux is better than windows

it's not a good first impression. the first time this happened to me i threw away the cd (about one year ago). only now i thought about trying ubuntu again, and finding out WHY it doesn't work. others may not give ubuntu another try

---

