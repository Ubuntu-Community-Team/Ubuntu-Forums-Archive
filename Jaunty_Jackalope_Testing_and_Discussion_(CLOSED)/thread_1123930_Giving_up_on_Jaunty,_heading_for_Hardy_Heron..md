---
title: "Giving up on Jaunty, heading for Hardy Heron."
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by connorh123 on 2009-04-12
Hey guys, I have a lot of problems with sound on a game called Counter-Strike. Here's what happens, I start the game, and usually  a song comes up. Instead of the song, a crackling sound comes up and sound goes away. I'm really getting ticked off with this problem, and if I don't know how to fix it, I'm going back to Hardy Heron, where it worked fine before.

---

### Post by Merk42 on 2009-04-12
Was the functioning Hardy Heron running the same version of WINE?
How do other WINE programs run between the two?
Could this be a classic PulseAudio problem?

---

### Post by connorh123 on 2009-04-12
The wine program I'm using now, is 1.1.8.
The latest version of wine is 1.1.9.
Pulseadio isn't a problem, because it works with everything else, but the game. Hardy Heron runs it fine, 9.04, and 8.10, don't.

---

### Post by ninjapirate89 on 2009-04-12
Don't give up on Jaunty just yet. Remember its not in it final state yet.

---

### Post by connorh123 on 2009-04-12
It's not just Jaunty, it's Ibex too.

---

### Post by FuturePilot on 2009-04-12
..

---

### Post by ninjapirate89 on 2009-04-12
> **connorh123 said:**
> It's not just Jaunty, it's Ibex too.

Oh..............well.

---

### Post by tom66 on 2009-04-12
Just to make sure... In Volume Control everything including PCM is at 100%? Set master volume to what you want. I found that if PCM is at 0% then there is just crackling (not muted).

---

### Post by connorh123 on 2009-04-12
Are you talking about aumix?

---

### Post by nwadams on 2009-04-12
this is due to wine not having support for pulse audio. If you look up pulseaudio wine you will find many solutions. Some ppl say using esd works, some ppl say using padsp as part of the launch command works. I think it really depends on your hardware (it worked out of the box for me...well after i spent like 100 hours making my x3100 work correctly)

---

### Post by gnomeuser on 2009-04-13
Situations like this underline where we need bugs to be filed. The amount of subscriptions is a very clear indicator of where work is needed. It might also indicate areas that we currently don't know about that are problematic.

---

### Post by connorh123 on 2009-04-13
There's no point in filing as a bug, because it has been one. I've seen several other posts about no sound.

---

### Post by KhaaL on 2009-04-13
> **connorh123 said:**
> There's no point in filing as a bug, because it has been one. I've seen several other posts about no sound.

nonsense! if people would think like this then opensource development would stagnate. If you can't find the bug, fill one out and write it's number here, and I assure you it will be looked into by a bugsquad member :)

---

### Post by connorh123 on 2009-04-13
> **nwadams said:**
> this is due to wine not having support for pulse audio. If you look up pulseaudio wine you will find many solutions. Some ppl say using esd works, some ppl say using padsp as part of the launch command works. I think it really depends on your hardware (it worked out of the box for me...well after i spent like 100 hours making my x3100 work correctly)

Pulse was never in Wine in 8.04, and it worked fine. The problem is, if I switch back, the audio might be wrong their too. So I don't know, I'm at a standstill.

---

### Post by nwadams on 2009-04-13
if this is your only complaint about jaunty stick with jaunty and wait for the official release, then we can try to figure out exactly how to make it work. Remember Jaunty is still a beta release and some stuff is bound not to work properly yet.

EDIT: i'm garanteed to have the exact same problem in 10 days too :p

may I ask what kind of hardware you are using?

---

### Post by connorh123 on 2009-04-13
Yes, but again. I had this same problem in Ibex, and that's not a beta. I'm sure their's a solution out there, but I have no idea.
EDIT: I'm using an IBM ThinkPad with Red Hat Linux, however I'm not sure about my video/sound card.

---

### Post by nwadams on 2009-04-13
```
padsp winecfg
```

run that command for me. And then go to sound settings. Just make sure that its activated for OSD (i think). What this command does is it allows audio to go through another sound server that wine supports. 

Then you should either A: be able to play yoru game normally
B: have to append padsp to the command to launch the game

---

### Post by connorh123 on 2009-04-13
My audio is checked for Alsa, and it worked before.

---

### Post by nwadams on 2009-04-13
yes but pulseaudio is not in hardy as far as I know...is it?
if padsp wine ...code to launch game didn't work for you then i'm not sure what to do. Have you reported a bug with wine?

---

### Post by connorh123 on 2009-04-13
Okay, the game works. Now the sound doesn't. Before, the game wouldn't even start, that's progress I suppose. Now for the sound...

---

