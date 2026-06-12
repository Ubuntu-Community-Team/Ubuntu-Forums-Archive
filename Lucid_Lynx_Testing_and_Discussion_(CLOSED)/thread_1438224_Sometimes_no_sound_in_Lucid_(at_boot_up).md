---
title: "Sometimes no sound in Lucid (at boot up)"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by svaens on 2010-03-24
It is weird, 

Sometimes, when I boot up, the sound is fine. Normal. There. Even GREAT! as my inbuilt microphone is detected. 

Sometimes when I boot up, there is NO sound. 
The speaker symbol on the panel looks mute.
When I click on it, the level is up. Doesn't matter where I put the slider. the symbol looks mute. 

So I go into the sound preferences to see what is there;

interesting... 

Output Tab:
Dummy Output (stereo). 

Input Tab:
no devices displayed. 

What should I do about this guys? Wait patiently? Or file a bug report ?

Anyone else see this kind of thing ?

---

### Post by cactaur on 2010-03-24
Hello svaens!

This looks an awful lot like pulseaudio is unable to lock the sound card. Maybe you might want to try using ```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

If pulseaudio isn't there, you might want to check out the workarounds [here]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Another%20process%20locking%20the%20sound%20card") for problems in Karmic. It might have lingered through the release. If not there are also a bunch of other potential problems on that page you might want to check out. If not, you might want to consider filing a bug. Good Luck!

---

