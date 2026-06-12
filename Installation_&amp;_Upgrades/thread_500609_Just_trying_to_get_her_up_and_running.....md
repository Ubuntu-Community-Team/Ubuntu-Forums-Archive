---
title: "Just trying to get her up and running...."
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by buildsomethingcrazy on 2007-07-14
I have a problem. I had linux running fine after I resolved a XServer problem by using "mesa" or something of that effect video driver for my ATI 9250 card. It worked fine and I read on some bulletins that I should download xorg-driver-fglrx as my driver for my video card. Well, I downloaded the updates  for Ubuntu and "xorg-driver-fglrx" driver and now I am getting the same problem with XServer that I had. I tried uninstalling xorg-driver-fglrx and loading mesa back but it still won't work... Help

! :mad: !

---

### Post by buildsomethingcrazy on 2007-07-14
Help...

---

### Post by merlinus on 2007-07-14
Press "Esc" when prompted to display the grub boot menu, boot into recovery mode, login...then enter:

(or Ctrl-Alt-F1 to get to prompt)

sudo dpkg-reconfigure xserver-xorg

Select "vesa" for your video driver.

Then:

startx

or reboot...

-merlin

---

### Post by buildsomethingcrazy on 2007-07-14
I tried that it doesn't work. I even tried reinstalling and doing it..

I can't think of the problem.

---

### Post by merlinus on 2007-07-14
Just to be clear --

You were able to select "vesa" as the video driver from the option screen in:

sudo dpkg-reconfigure xserver-xorg

Then typed

startx

and then???

-merlin

---

### Post by buildsomethingcrazy on 2007-07-14
> **merlinus said:**
> Just to be clear --

You were able to select "vesa" as the video driver from the option screen in:

sudo dpkg-reconfigure xserver-xorg

Then typed

startx

and then???

-merlin

Well, I typed in "sudo dpkg-reconfigure xserver-xorg" and used vesa as my driver. Get through the whole reconfigure screen and then reboot. Goes to the loading screen and then a black screen where it seems to be loading things than a blue screen with weird letters everywhere saying "Xsever failed to load"

---

### Post by merlinus on 2007-07-14
Instead of rebooting, can you type in

startx

after going through the reconfiguration.

-merlin

---

### Post by buildsomethingcrazy on 2007-07-14
> **merlinus said:**
> Instead of rebooting, can you type in

startx

after going through the reconfiguration.

-merlin


No, let me try that. I'll be back on to tell you the results in 5 mins.

---

### Post by buildsomethingcrazy on 2007-07-15
Okay, I figured out the **_REAL_** problem. It was a stupid one, in fact I am embarresed to post it but, I was telling it to find my video card at PCI: 0:2:0... When really it's PCI: 2:9:0. It loaded up just fine however, I have a little problem still if that. I think maybe it's because I am using the vesa drivers. When I start it starts fine but, for about six seconds it's black and white than POP!... Colour. Is there a fix for that or should I not even worry untill I get the real ATI drivers?

---

### Post by merlinus on 2007-07-15
Sounds like a success!  Wait until you install the correct drivers for your video card.

-merlin

---

### Post by buildsomethingcrazy on 2007-07-15
Awesome, now I need to goto the networking section to see how to get my dial up running.

:)

Thanks

---

