---
title: "Need help inserting a processor - Have questions"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by ClientAlive on 2011-06-26
I managed to get the pins pretty well straightened out, I think, with this thin fillet knife I have. I'm just not sure how perfect they have to be (they're pretty good though). I wanted to try putting it back in the mother today but there's a few things I'm not sure about. What I'm wondering is:

(1) I see what almost looks like a little piece of lint in there but if I look close I'm starting to wonder if it isn't a little jumper. I can't quite tell what it is or if it's supposed to be there. Apart from that there are four, spots, rectangular and very small, that I can see the plastic underneath. These are clearly part of how it's made. Then there's that other thing. Blowing on it does not dislodge anything and I can't see well enough to really see what it is. (I'm not blind but I do wear glasses - lol).

(2) I want to be sure I insert it in the right direction. I thought that using those 4 rectangular spots on the bottom (compared to ones I see inside the socket) could help me do that but I'm not sure it's really the preferred method.

(3) There is a little bar next to the socket on the mother. I'm assuming that down (parallel to the mobo) is locked - I don't see how it could be any other way but want to be certain.

(4) I wonder if it is better to power up without the heat sync on there just long enough to see that everything is installed and working correctly before putting them on. Doing that won't burn it out in the blink of an eye? That heat sync is what I think killed me on those pins yesterday. I think it nailed me when I pulled it off of there since the processor was not in the socket when I looked but was stuck to the bottom of the heat synk. Then again, the machine would not power up right before I took it out again like that - so I did something wrong when I inserted it too.


Any help would be greatly appreciated. I've never done a project like this before so I'm not sure about some of the details and I want to get it right this time.

---

### Post by dFlyer on 2011-06-26
Hopefully you didn't zap the cpu. It will only fit in one way. Do not force it. You can test it without the heat sink, but only test it. Do not run it very long as you can cook it and do more damage.

---

### Post by doas777 on 2011-06-26
Buy a magnifying glass. you will need it. while you are at radio shack, get some small probes as well. make sure that lint is supposed to be there. contaminants on the chip die can cause the chip to flare and burn up. 

when you are done straightening pins, lift the bar, align the chip with the socket, and drop it in gently. if it doesn't just drop into place under gravity, you still have pins to straighten. usually cpus and sockets have a corner marked, so match up those corners.usually its a gold dot or a triangle, that is not on any other corner.

the heatsink question depends entirely on the chip you have. if its an AMD, or more than  100w, do not run it without a heatsink.
the bios load phase of boot is one of the hottest periods in a CPUs lifetime (well hopefully) because none of the bios power management code is loaded yet, and everything is running at the max the hardware will support.

---

### Post by ClientAlive on 2011-06-26
Here's what I know about the chip:

> 
I don't know a whole lot about how to identify the socket but I can give you what I can find if it helps. If it's not the right info just let me know and I'll find the right info for you.

 Here's what's printed on the chip (just as it appears:

<line 1> AMD64
<line 2> AMD ADA3400DAA4BY
<line 3> LBBWE 06026(or G?)PMW
<line 4> Z881766A61180

 And, along another side it says, copyright 2001 AMD (with the copyright symbol though).

 The mobo might be an ATI IXP 450?? That's what one larger chip on it says. That chip is roughly, maybe 3 centimeters (7/8 inch) and is square.

 I found a specs page online at hp. It is the right name and model and the picture of the mobo on that page looks almost identical except, I think some of the chips on it are not precisely identical. It's possible the one I have is either older or newer than what's in the spec sheet? I don't know.

[http://h10025.www1.hp.com/ewfrf/wc/d...roduct=1843604](http://h10025.www1.hp.com/ewfrf/wc/d...roduct=1843604)


doas777 your right about the little gold triangle in one corener. I hadn't noticed that before. I don't have a magnifier or $ for one but I would like to get one sometime soon. One of those round ones with the florescent light around the outside edge and on a n arm that mounts to the desk - that would be perfect for things like this I think.

---

### Post by ClientAlive on 2011-06-26
Amazingly, I got er'!! Fires up, now just to see that all the other hardware is ok and I can install, well, Xen would be nice, but I think I'll test run a small linux distro first.

Thanks guys.

:popcorn:
-------------------

Edit:

> **dFlyer said:**
> Hopefully you didn't zap the cpu. It will only fit in one way. Do not force it. You can test it without the heat sink, but only test it. Do not run it very long as you can cook it and do more damage.


Funny thing - you look like one of my old college profs (if that's really your picture). He wasn't in Texas when I had him though. Pretty sure his name was Gary too though. Wierd!

---

