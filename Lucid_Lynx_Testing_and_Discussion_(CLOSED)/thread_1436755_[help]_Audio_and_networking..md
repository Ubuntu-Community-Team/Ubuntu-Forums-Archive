---
title: "[help] Audio and networking."
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by godslam on 2010-03-23
I've got two problems; actually more.

Ubuntu 10.04

First one is that I'm a Linux n00b. Besides this though, my audio doesn't work at all and I'm not sure how to fix this. I've looked through many topics on here, but they all lead me down the same path and I find that I would have to make a topic about it to get something going.

Second actual problem is that I've managed to bridge my network, but evertime I restart my computer, I have to go to terminal and type

```
route add default gateway <default gateway IP address>
```

This isn't a huge issue, but I'm sure it's easily solved. Thanks for any help that I receive. =)

---

### Post by lisati on 2010-03-23
Just to clarify, which version of Ubuntu are you using? (You've posted your query in a section of the forum devoted to a version of Ubuntu that hasn't officially been released yet.... :D)

---

### Post by godslam on 2010-03-23
Oh, sorry. I am using Ubuntu 10.04; Lucid Lynx. I know it hasn't been officially released, but I would really like to use this version for now. Using it while it's buggy may be kinda dumb, but the more problems I run into, the more I can get used to having problems with it; then I can fix whatever other problems I run into more easily.

---

### Post by godslam on 2010-03-23
Sorry to bump this, but I'd really like some help. If it also helps, I have "SB X-Fi Xtreme Audio CA0110-IBG" as my on-board sound. I read that there was problems with this before, but then they went away. So I'm confused as to why I'm still having trouble.

---

### Post by dino99 on 2010-03-23
Lot of people have sound issues, and devs are working on, especially some Alsa and pulseaudio problems.

But on your side you can grab some info by looking at:

.Xsession-errors (hidden file)
system -- admin -- log viewer

then it's good to know if your sound chipset is recognized: go to system -- pref -- sound, and watch hardware tab ( if you cant open sound properties or the chipset is not loaded, well here is the problem)

An other way is to find your_chipset+linux blog/wiki/forums/bugs with google. If you cant go ahead, ask a question onto launchpad.

to know what Lucid recognize, into console: aplay -l

---

### Post by godslam on 2010-03-24
> **dino99 said:**
> Lot of people have sound issues, and devs are working on, especially some Alsa and pulseaudio problems.

But on your side you can grab some info by looking at:

.Xsession-errors (hidden file)
system -- admin -- log viewer

then it's good to know if your sound chipset is recognized: go to system -- pref -- sound, and watch hardware tab ( if you cant open sound properties or the chipset is not loaded, well here is the problem)

An other way is to find your_chipset+linux blog/wiki/forums/bugs with google. If you cant go ahead, ask a question onto launchpad.

to know what Lucid recognize, into console: aplay -l

I see two things in the hardware tab:

"HD48x0 Audio" and "[SB X-Fi Xtreme Audio] CA0110-IBG".

I can't use HD audio because it doesn't like to work through HDMI correctly. As for optical, I can't do that either because I just don't have that option. So the SB X-Fi is what I'm basically forced to choose, but it has so many different "Profiles" that I can choose from, that I try them all and get nothing. I make sure everything's unmuted and I check "alsamixer" and still I find nothing that can even give me a step in the right direction. I feel like I'm screwed and will have to wait, but I'd really rather not. I'm thinking about trying to find an old sound card or something. =/

---

