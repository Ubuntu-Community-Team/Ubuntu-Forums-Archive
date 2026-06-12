---
title: "Lucid sound vvv sad"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by noj91 on 2010-04-10
Hi all been on ubuntu since warty as my main so have had a bit of experience and have just taken the current lucid beta2 live for a test spin and am immediately disappointed,my current desktop is jaunty and for the most part all is well and good.

My current soundcard is an old ICE 1712 chipset (Terratec DMX6 Fire) which should be well supported under linux, however the only output option available is IEC958 which is fine but the headphone out and any of the analogue outs are not available! they all work fine with jaunty!

My second box is windoze with an EMU1820m soundcard/breakout box, to get this working under jaunty I had to compile the latest alsa at the time, but I never got full duplex working well, playback(half duplex)was fine with jack.With lucid I get the no soundcards errors even though lspci shows the creative multimedia controller and lsmod shows all the relevant snd modules loaded by the kernel!

I've downloaded the relevant pulse/alsa utils but after fiddling no joy. alsaconf was a great utility but seemingly now depreciated after the advent of the mighty pulse audio.

In the past I've wrestled for hours to get sound working properly and had always thought it could only get better.I truly appreciate the incredible effort that the open source community has gone to to provide me with a free fully (almost) operational complete operating system,but feel my frustration when it works in jaunty but not in lucid! 

REGRESSION! maybe its the latest alsa, the latest pulse,the latest Ubuntu I dont Know,I wont bother I'll stick with jaunty, suits my purposes.

If anyone has a solution to these issues I'd love to hear ..It's just that I'm tired at banging my head at the same old problems time and time again.

cheers and thank you all (keep up the good work) jon 

ps. posted from lucid lynx beta2 live so I guess networkings fine lol!

---

### Post by Breambutt on 2010-04-10
I haven't tried my DMX 6fire in Lucid but killing PulseAudio pretty much fixed everything with Audiophile 24/96, both are ice1712 cards. I believe it's been laughed and cried over how Pulsu (no typo there) can't handle these popular cards properly.

Additionally, [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63) seemed to do the trick for M2496 without removing PulseAudio if someone swings that way for some bizarre reason.

Edit: [insert FFFFUUUUUUUUUU- face] Ran out of wall sockets, extension cords and router slots, can't try squat right now. Out of curiosity, did the front panel jacks work out of the box in Jaunty? I remember having to fidget around with an .asoundrc file in Hardy Studio, never really tried Intrepid-Jaunty-Karmic.

---

### Post by empty_spaces on 2010-04-10
@ noj91,

what is the output of **aplay -l** ?

---

### Post by ranch hand on 2010-04-10
I am running an Audigy1 card and with the alsa mixer the sound is better under 10.04 than in any back to and including 8.04.  I thought the sound was great in all of them but this is a lot better.

---

### Post by cariboo on 2010-04-10
This is why we have testing before release, make sure you have bugs reports created. The devs can't fix a problem if they don't know about it.

---

### Post by noj91 on 2010-04-11
Thanks guys sorry for the delay in getting back.

[https://bugs.launchpad.net/ubuntu/+s...42/comments/63](https://bugs.launchpad.net/ubuntu/+s...42/comments/63) points the way to sorting the terratec ICE1712 problems especially pulse audio ticket#624. thanks for the links.

aplay -l  yields the same result on the terratec box under both jaunty and lucid, to be expected as the problem seems to be with pulse audio

```
jon@jon-desktopjaunty:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DMX6Fire [TerraTec DMX6Fire], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

On the emu box aplay -l gives no soundcards found...  so I guess its an alsa issue since lspci and lsmod both indicate the hardware is identified and correct modules loaded.

I'll try killing pulse and see what happens but this wont be until next weekend as I will working away from home

Thanks again for your input jon

---

