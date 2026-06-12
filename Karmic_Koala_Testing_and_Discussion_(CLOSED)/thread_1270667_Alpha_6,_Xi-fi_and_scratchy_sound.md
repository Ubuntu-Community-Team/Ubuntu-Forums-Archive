---
title: "Alpha 6, Xi-fi and scratchy sound"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Visceral Monkey on 2009-09-19
My x-fi works, out of the box, for which I'm great-full for..however, when I load up a game like nexuiz or watch a youtube video the sound is scratchy and kind of tinny. Could this be related to the much maligned pulse audio? Anyone have a fix for this?

---

### Post by dext on 2009-09-19
> **Visceral Monkey said:**
> My x-fi works, out of the box, for which I'm great-full for..however, when I load up a game like nexuiz or watch a youtube video the sound is scratchy and kind of tinny. Could this be related to the much maligned pulse audio? Anyone have a fix for this?

what version of Pulseaudio are you using? cause 0.9.17 was buggy, 0.9.18 should fix these issues, but i would suggest filing a Bug report

---

### Post by Visceral Monkey on 2009-09-19
> **dext said:**
> what version of Pulseaudio are you using? cause 0.9.17 was buggy, 0.9.18 should fix these issues, but i would suggest filing a Bug report

I'm up-to-date on Alpha 6 so I'm assuming it's the latest and greatest.

Edit: I take that back, I am runing 0.9.17 but don't see a 0.9.18 to upgrade to in synaptic.

---

### Post by dext on 2009-09-19
> **Visceral Monkey said:**
> I'm up-to-date on Alpha 6 so I'm assuming it's the latest and greatest. well i get the same problems in F12 an have filed a bug, if you dont file a bug against it it will not get fixed

---

### Post by Visceral Monkey on 2009-09-19
> **dext said:**
> well i get the same problems in F12 an have filed a bug, if you dont file a bug against it it will not get fixed

I was wrong about having the most current, but I can't find 0.9.18.

---

### Post by dext on 2009-09-19
> **Visceral Monkey said:**
> I was wrong about having the most current, but I can't find 0.9.18.
Ubuntu Devs probably have it in PPA or wherever building it, it just came out thursday or friday

---

### Post by PmDematagoda on 2009-09-19
> **Visceral Monkey said:**
> I was wrong about having the most current, but I can't find 0.9.18.

It was only released yesterday, so you will need to wait until the Ubuntu developers can package the new version of pulseaudio. If you are desperate, you could install it yourself, but I don't know the steps in order to do that properly.

Release announcement for 0.9.18 is [here]("http://pulseaudio.org/milestone/0.9.18").

---

### Post by Visceral Monkey on 2009-09-19
> **PmDematagoda said:**
> It was only released yesterday, so you will need to wait until the Ubuntu developers can package the new version of pulseaudio. If you are desperate, you could install it yourself, but I don't know the steps in order to do that properly.

Release announcement for 0.9.18 is [here]("http://pulseaudio.org/milestone/0.9.18").

It's annoying but not so much that I'll risk doing it myself. I'll just keep an eye out for a ppa package.

---

### Post by PRGUY85 on 2009-09-20
When will they allow us to use Digital Input from the Front Drivebay of X-FI platinum?

---

### Post by dext on 2009-09-20
> **PRGUY85 said:**
> When will they allow us to use Digital Input from the Front Drivebay of X-FI platinum?
i suggest you ask the pulseaudio devs that

---

### Post by dext on 2009-09-21
do this in Terminal **alsamixer -c0** an raise your Volume an you should get sound

---

### Post by Squonk07 on 2009-09-21
I'm running Alpha 6 and it seems about an hour ago a bunch of PulseAudio updates were pushed through the Update Manager. According to Synaptic, these should be what you're looking for.

I wasn't aware that PulseAudio would support the X-Fi at all. It has been such a long time since I looked at Linux support for this chip that I had pretty much figured it would never happen. I might have to install the final version of Karmic on my music production rig and give it a whirl. :)

[CENTER][ATTACH]129252[/ATTACH][/CENTER]

---

### Post by Nullack on 2009-09-21
Im still getting scratchy audio on my creative audigy 2 soundcard.

---

### Post by mohi on 2009-09-22
pulseaudop 0.9.18 is now in 9.10 repos now but the problem gets worse for me! no audio at all! :-/

---

### Post by dext on 2009-09-22
> **mohi said:**
> pulseaudop 0.9.18 is now in 9.10 repos now but the problem gets worse for me! no audio at all! :-/

did you follow this post [http://ubuntuforums.org/showpost.php?p=7982697&postcount=11](http://ubuntuforums.org/showpost.php?p=7982697&postcount=11)

---

### Post by far_star on 2009-10-04
I am having scratchy sound using my X-fi. Some update did this because when I first installed Alpha5 this was not an issue. Particularly, this problem is in the left-front channel. 


All updates have been applied. Anyone else having this issue ?

---

### Post by OliW on 2009-10-11
Still having this problem. I swear it went away for a while but it's back. And just as annoying.

---

