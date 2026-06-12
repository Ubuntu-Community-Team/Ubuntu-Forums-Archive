---
title: "Grrr, what's up with compiz?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by crispeto on 2009-03-27
I just upgraded my eee 900 to the new Jaunty beta. I had compiz and all it's effects working great for about an hour. I then hooked my eee to an external monitor and after the adjustments to get it to work, I can no longer choose "extra" in the visual effects. When I try it states "desktop effects could not be enabled". Is there anything I can do to get the effects back? Thanks

---

### Post by tommcd on 2009-03-28
A netbook like the eee 900 is not up to the task of running compiz imo. Compiz will not run on graphics cards that the Ubuntu devs do not support. I suspect that the graphics on the eee 900 might be one of them.

Honestly, what is all the fuss about compiz anyway? Doesn't that "wobbly windows" stuff get old after about 5 minutes? For a netbook like yours I would forget about compiz. I prefer fast and lean performance over eye candy any day. This is especially important on a low end computer.
There are reports of compiz running on the eee 900 with older versions of Ubuntu. Perhaps the newest incarnations of Ubuntu and compiz are too much for the eee.

---

### Post by starcannon on 2009-03-28
I have not looked at Jaunty yet, but I can attest to an Asus Eee 701 4g running compiz smoothly on Ubuntu 8.10. Granted it was a fairly basic compiz setup, though I do have the cube w/caps and skydome.

---

### Post by scaine on 2009-03-28
> **tommcd said:**
> A netbook like the eee 900 is not up to the task of running compiz imo. Compiz will not run on graphics cards that the Ubuntu devs do not support. I suspect that the graphics on the eee 900 might be one of them.

Definitely not the case.  As noted earlier, even a 600Mhz Eee 701 can smoothly run compiz effects, like cube, wobbly and ringswticher.  At Jaunty Alpha 4, my 701 was doing just that.  I haven't update it recently though.

> **tommcd said:**
> For a netbook like yours I would forget about compiz. I prefer fast and lean performance over eye candy any day. This is especially important on a low end computer.

If that's your opinion, why did you even bother posting on this thread?  Compiz enhances every aspect of interacting with your PC.  That's my opinion.  As for the low-end, that's where I find compiz often can help, since the CPU isn't driving window movement anymore.  Very few compiz effects hit the CPU hard these days.

@crispeto : What resolution were you running your external monitor at?  I've heard on these forums that compiz struggles (in fact, doesn't work at all) with resolutions over 2048x2048.  If you set your external monitor up as a twin view, high-res, WITH your laptop monitor, that might be causing the issue.  I guess, for the time-being, you could try running gnome-display-properties and removing your external monitor to see if that's definitely what caused it.

---

### Post by Amaranth on 2009-03-28
It isn't compiz struggling, it's your video card/driver.

---

### Post by vredley on 2009-03-28
Try this - first run the fusion-icon. Right click - Select Window Manager - Compiz. This seems to 'half-load' Compiz. Then select 'Normal' under Visual Effects, and the switch from Metacity should be persistent.

Compiz is excellent on my Eee with UXA enabled - for about an hour, after which the system becomes unstable. :(

---

### Post by tommcd on 2009-03-28
> **Amaranth said:**
> It isn't compiz struggling, it's your video card/driver.

That is what I was referring to when I suggested compiz may not be the best thing to run on the eee. You should likely expect a performance penalty with compiz.

---

### Post by vredley on 2009-03-28
> **tommcd said:**
> That is what I was referring to when I suggested compiz may not be the best thing to run on the eee. You should likely expect a performance penalty with compiz.

Funnily enough, Compiz works rather well on the Eee, especially with Hardy. If you don't believe me, get yourself an Eee and give it a whirl. :)

---

### Post by crispeto on 2009-03-28
Well, crazy enough, I just went and hooked up the monitor again and suddenly compiz is working now. All functions are fairly smooth. Not sure what the monitor had to do with it but since I won't be using that monitor much I think all is well. Thanks for all your replies.

---

