---
title: "is there any way to increase the resolution for netbook?"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by fakhrul12 on 2011-01-04
i`m using Ubuntu 10.10 on my HP mini netbook.
and i find its really hard to manage my works with a little space available.

I`ve already seached the internet for a solution to increase the screen resolution but the links is down.
So I`m wondering is there anyone here with a better solutions and perhaps, a links for me to try it out.

thanks in advance

---

### Post by dino99 on 2011-01-04
goto menu: system prefs screen, and check driver activation too: system admin additional driver

---

### Post by darkhelmetchris on 2011-01-04
This is interesting.  I have a netbook that is 1024x600 native resolution, and I have sometimes wished it to be more, even if it's not native and would be scaled.  ...maybe...

I found this:
[http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/](http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/)
but I have not yet tested it.  I will post the results of my test later.

---

### Post by darkhelmetchris on 2011-01-04
Okay, I didn't feel like using the whole script.  I was more interested in the real commands to do this job.  So, I found that "xrandr" is at the heart.  I have successfully scaled my screen on my desktop (I have not yet tried the netbook, but I'm sure the results will be similar)

First, we need to know what our active device is:
```
~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
...
...

```
from that I see that "CRT2" is my active device.

Then I did this:
```
~$ xrandr --output CRT2 --scale 1x1.1
```
and got a squished screen.

This restored me back to normal:
```
~$ xrandr --output CRT2 --scale 1x1
```

...or you might just try the handy script in that link.  I think you'll find the test to be quite interesting.  The trick will be to find the right combination on a netbook to give you a scale you can live with.  Mine was a little ugly, but it did work.  Other values might be more interesting.

---

### Post by darkhelmetchris on 2011-01-04
As a guess, you might try:
```
~$ xrandr -s 1024x768
```
and then
```
~$ xrandr --output CRT2 --scale 1x1.28
```
(where CRT2 is replaced with your active device)

I think that would give you a scaled 1024x768 showing on a 1024x600 screen... maybe... just have to test on my netbook

---

### Post by darkhelmetchris on 2011-01-04
Success! (for me anyway)

My Acer Aspire One D250 netbook has a native resolution of 1024x600, and I was able to get a resolution of 1365x768 (a 16:9 aspect ratio scaled/faked) with this command:
```
~$ xrandr --output LVDS1 --mode 1024x600 --scale 1.333x1.28
```
Note that this is NOT a 1-to-1 image, it will be ever so slighty off aspect.

If you want 1-to-1 aspect you can get a resolution of 1311x768 with this command:
```
~$ xrandr --output LVDS1 --mode 1024x600 --scale 1.28x1.28
```

And then to get back to normal:
```
~$ xrandr --output LVDS1 --mode 1024x600 --scale 1x1
```

(these tricks didn't work on my regular workstation and monitor, but they worked well on my LCD for my netbook)

That worked for me.  Hope you have fun!

---

### Post by fakhrul12 on 2011-01-04
heu mister...pardon for my question..but its a no go for my netbook....
can you explain step by step for me to try this one out?

a script is really....ugh...i didnt even know how to use it

---

### Post by darkhelmetchris on 2011-01-04
Sure, we can do that.  It works great on my netbook, giving me a scaled "higher" resolution.  Let's start off with this..

What is the output of your:
```
~$ xrandr
```

You should see something like:
```
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0* 
   1360x768       51.0     52.0  
...
...

```

---

### Post by rfrayer on 2011-01-06
> **darkhelmetchris said:**
> Success! (for me anyway)

My Acer Aspire One D250 netbook has a native resolution of 1024x600, and I was able to get a resolution of 1365x768 (a 16:9 aspect ratio scaled/faked) with this command:
```
~$ xrandr --output LVDS1 --mode 1024x600 --scale 1.333x1.28
```Note that this is NOT a 1-to-1 image, it will be ever so slighty off aspect.

If you want 1-to-1 aspect you can get a resolution of 1311x768 with this command:
```
~$ xrandr --output LVDS1 --mode 1024x600 --scale 1.28x1.28
```And then to get back to normal:
```
~$ xrandr --output LVDS1 --mode 1024x600 --scale 1x1
```(these tricks didn't work on my regular workstation and monitor, but they worked well on my LCD for my netbook)

That worked for me.  Hope you have fun!



man you are purely awsome!!!!!!!!!

---

### Post by rfrayer on 2011-01-06
would be nice if ubuntu used that natively on remix...or remove remix and make a standard ubuntu acrer edition that uses it lol

---

