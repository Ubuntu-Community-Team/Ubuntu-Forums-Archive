---
title: "No sound after upgrade"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by tripmix on 2008-01-07
well mostly no sound, DTS and AC3 and stuff that pass through spdif still works fine. Iv tried upgrading, downgrading, compiling codecs and playera from source. Not even vlc works and that makes me think it has nothing to do whit codecs at all. But it's very strange, no errors from the players or anything, just silence...

Using Feisty 64bit, alsa snd-intel8x0

I thought it was mp3lib at first but I think Iv ruled that out. Really need help, this is driving me crazy.

---

### Post by tripmix on 2008-01-07
Guess I was a bit unclear. I upgrade to gusty yesterday but my problem remains. I just installed about a week ago and it was working fine in till yesterday when I did a apt-get upgrade. The packages I noticed upgrading was ffmpeg and libaudio1 or something. I don't think any of them are the problem but I'm not sure. Mplayer upgraded and started using mp3lib instead of ffmpeg. But my problem happens to wav and ogg and stuff to, everything except what my receiver/ audio chip can decode. It seams to me as if there is something wrong with the audio system itself. But whit out any usefull logs or other output I lost. Everything acts as if it's working fine. 

This whole thing make me wish I never pushed enter on that stupid apt-get upgrade. If I can't fix this I'll just have to fine some other dist and install again. I have other issues to with this system but nothing that renders it so completely useless as this. This is a media pc so no sound = useless. The sad thing is it seams like such a easy stupid thing to fix.

If anyone has any idea on where to even start looking for this problem it would be helpful as none of my media players, xorg,  dmesg or alsa-utils  produce any useful output at all.

This is where my logs and error messages would be if there where any.

UPDATE: If use -ao alsa:device=spdif I get sound. Guess thats a temporary solution. Anyone know how to make it permanent? Never mind I'll figure it out before you can answer anyway ;P

UPDATE2: It now works by creating  .asoundrc and putting this in it.
pcm.!default { 
type hw 
card 0 
device 1 
}

---

### Post by addisor on 2008-02-23
UPDATE: If use -ao alsa:device=spdif I get sound. Guess thats a temporary solution. Anyone know how to make it permanent?

Was there a permament solution to this?

Can you explain what your asound means? I have much the same problem.

---

