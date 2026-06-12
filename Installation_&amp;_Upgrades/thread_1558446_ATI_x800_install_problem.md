---
title: "ATI x800 install problem"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by john_mc on 2010-08-22
Hey all,

I have been trying for some time now to get the dual screen on my linux machine - ubuntu 10.04 server with GUI installed.

I have tried using my ATi 9600 and now trying with a newer card, ATI X800 but have been unsuccessful following guides and posts on the net.

I have tried going to the software centre under application and isntalling what I believe are the fglrx drivers but no dual monitors.

I when to the ati website and download the ati-driver-installer-9-3-x86.x86_64 by selecting Desktop > X??? > linux x86 from the menus. This doesn't install after suing ./ati-driver-installer-9-3-x86.x86_64 as it the install stops on ./default_policy.sh does not support version.

When my computer boots i get the picture on my TV but have never seen anything in hardware drivers and don't seem to have the file xorg.conf as located in /etc/x11/xorg.conf.

Any help?

---

### Post by john_mc on 2010-08-22
Ok I'm lost

At present i have no xorg.conf file in /etc/x11. . . should I?

The synaptic package manager shows installed:

X.Org X server -- AMD/ATI Radeon display driver
utility to control ATI Radeon backlight functions on laptops
X.Org X server -- ATI Mach64 display driver
Identifiers supported by the ATI graphics driver
GNOME user interface and desktop integration for driver management
user interface and desktop integration for driver management

Are any of these stopping me installing the driver I download from ati.com - ati-driver-installer-9-3-x86.x86_64 - which gives error "./default_policy.sh does not support version."

I don't care what driver i need or if the additioanl effects don't work but I do need the tv out to work. Any help????????

---

### Post by ljrmorgan on 2010-08-22
I have an x800xl and it worked out the box - the card is no longer supported by the fglrx drivers and uses the open drivers built in to the kernel instead.

To clarify - does it work with one of your monitors? Have you tried going to system > preferences > monitors and setting up dual monitors there? You shouldn't need to muck around with xorg configs I don't think.

---

### Post by john_mc on 2010-08-22
I hooked up up the monitor from my windows XP machine and it does works as a clone. When looking under system > preferences > monitors I then have 1 unknown monitor but no option for an extended desktop. Is there some way to configure this?

I really want my TV to run off my linux machine through the SVid port. Any ideas on how i can do this?

Cheers for the reply as I have 2 posts up and little reponse at the moment.

---

### Post by ljrmorgan on 2010-08-22
Do you see a checkbox labelled "Same image in all monitors" and a "Detect monitors" button? Try hitting the button, see if it finds the screen. If it does make sure the "same image in all monitors" box is not ticked, then you should have an extended desktop (I think).

Are you trying to have one monitor connected through DVI/VGA and then hook up a TV through the SVid port to use as a separate monitor?

---

### Post by john_mc on 2010-08-22
Primarily i want one monitor connected via the VGA port and the TV connected via the S-Video port. I get picture on both when oading but then then the TV goes blank and the monitor is fine.

With two monitors connected, one via VGA and the other DVI then I get the same picture on both. When checking the monitors box as advised I have the "same image on all monitors" is disabled/greyed out out beside the detect monitors button.

I am completely lost lost here mate.

---

### Post by ljrmorgan on 2010-08-22
Ugh, ati.

With the two monitors connected did you click the "detect monitors" button? That might "un-grey" the option.

I had a quick look for the tv thing - most of the results are quite old and are about the old fglrx driver, I'm not sure how you'd get it working.

If it works when loading that would suggest that the problem lies with X - not the card/kernel. (It works until X starts, basically. If you try switching to a virtual terminal (Ctrl+Alt+F1 will get you there, Ctrl+Alt+F7 will get you back) - you might get something on the TV then. I'd try the stuff below first though!)

Have you tried googling for tv out and radeon? I found this which might help: [http://www.x.org/wiki/radeonTV](http://www.x.org/wiki/radeonTV)

It mentions running these commands in a terminal to get it working dynamically:
```

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xrandr --output S-video --set tv_standard ntsc

```

If these work then I'd follow the steps it suggests to get it working statically too. I don't have a tv near by, so I can't try this out - good luck!

---

### Post by john_mc on 2010-08-22
Cheers mate, I tried the code and got an error: Cannot find output "S-video". Going to try the link you dropped me as I hadn't come across it in googling the problem.

Would I have more luck hunting out my Nvidia G6800GT card for a TV out?

---

### Post by ljrmorgan on 2010-08-22
> **john_mc said:**
> Cheers mate, I tried the code and got an error: Cannot find output "S-video". Going to try the link you dropped me as I hadn't come across it in googling the problem.

Would I have more luck hunting out my Nvidia G6800GT card for a TV out?

You might need to change the Xorg config - the site I linked to might tell you how to go about it. I think when I searched I looked for radeon driver tv out.

You probably would be better off with the nvidia card - the open source ati drivers are pretty ropey, at least for these cards, I can't suspend or hibernate my PC successfully and I'm pretty sure that's down to the ati drivers. Let me know how it goes!

Did you try the virtual terminal thing?

---

### Post by john_mc on 2010-08-24
Work kept me busy so didn't have a chance to respond,

Iswitched on my linux box and it loaded fine with out have to hold shift and boot of a different kernel so guessing installing other drivers solved that. One problem solved.

The virtual desktop works with my 19" monitor connected but when doing Alt+Ctrl F1 with the TV connected too - both screen just remain black.

I am thinking that I will go buy a cable to run the TV of the DVI port as I just remembered that the TV has a PC port. I will let you know ho it goes. 

I may buidl another PC and give the Nvidia card a go - lost a bit of faith in linux. I will keep posting in case someone has insight or it helps someone.

---

### Post by ljrmorgan on 2010-08-24
Good luck with it all, and try not to lose faith! I understand where you're coming from, and I have similar moments myself - I've had this card for years, if you think things don't work now, just imagine what they were like then! It isn't really a linux problem though, or at least it isn't there fault - windows doesn't support these cards either, they rely on third party drivers. ATi don't make decent drivers for linux (not for our cards anyway) and they also don't release the specifications needed for the kernel people to make good open source drivers. NVidia have always been better, and I think ATi are getting there, finally, but it's pretty frustrating.

Still, the DVI cable ought to work, I wish I knew more about it. I would suggest maybe posting another topic in the Multimedia & Video forums and mention the card and "S-video" or "Tv out" in the title - you might get help from some people that know what they're talking about!

All the best,

Louis

---

