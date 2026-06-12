---
title: "Audio; is it better than in Karmic yet?"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kaldor on 2010-04-26
Karmic is infamous for many audio problems. How's Lucid shaping up for this? I don't want another one of these releases where I need to alter things too often just to listen to music or watch a movie :(

Topic I made in the Cafe:

[http://ubuntuforums.org/showthread.php?t=1460560](http://ubuntuforums.org/showthread.php?t=1460560)

Oh, and only 3 days to go!

---

### Post by gnomeuser on 2010-04-26
I haven't had many audio problems since before Karmic but Lucid has made great advances. Not only has the general stack improved but we now have ppas for testing of upcoming ALSA driver and PulseAudio releases. 

Is it better, yes, it improves on an already really great and flexible system.

---

### Post by dino99 on 2010-04-26
there are many different experience, worst or better, depend on the sound harware.
Myself have not had so much troubles with jaunty or karmic, sound is fine, but on the same machine lucid sound have not work out of the box (fresh install): sound hardware not recognized and bad default installation settings: have had to copy/past default.pa & system.pa from karmic to finally make sound works with lucid :(

---

### Post by Hairy_Palms on 2010-04-26
well, its not perfect by any means, but this is the first "release" where i havent uninstalled pulseaudio after a few days, and my microphone works without removing pulseaudio, so yes id say its better than karmic :)

---

### Post by aceracer24 on 2010-04-26
Stock out of the box, sound works for Lucid as it did on Karmic for me. However, as with Karmic sound randomly distorts and for the life of me, I am still unable to get SPDF to work in 5.1 surround for standard sounds like MP3s. Hell, I would just be happy to get stereo with my sub working. Setting the sound to digital activates the sub but all of the sound comes from only one of the front speakers. 

So to answer your question, I don't believe it is any worse. To determine if it's better or not would greatly depend on what it is you want to accomplish from a fresh stock installed setup. 

One odd thing though, my sound is always muted when it boots up for the first time after a fresh isntall. Not sure why.

---

### Post by dino99 on 2010-04-26
a howto that can help:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by aceracer24 on 2010-04-26
Ok, I am still pretty green when it comes to Linux so excuse my ignorance but how does the link you listed help? The last few distros use Pulseaudio versus ALSA. Now I realize that ALSA still plays a part but uses Pulseaudio as the sound server. I doubt many of those help suggestions would be of much help any more. Again, excuse my ignorance.

---

### Post by ratcheer on 2010-04-26
Audio seems to me to be the same in Karmic and Lucid. The good side of that is that, after applying all the same fixes and workarounds in Lucid that I had done in Karmic, audio is working perfectly. I.e., I already knew what to fix instead of having to search all over kingdom come.

Tim

---

### Post by gnomeuser on 2010-04-26
> **aceracer24 said:**
> Stock out of the box, sound works for Lucid as it did on Karmic for me. However, as with Karmic sound randomly distorts and for the life of me, I am still unable to get SPDF to work in 5.1 surround for standard sounds like MP3s. Hell, I would just be happy to get stereo with my sub working. Setting the sound to digital activates the sub but all of the sound comes from only one of the front speakers. 

So to answer your question, I don't believe it is any worse. To determine if it's better or not would greatly depend on what it is you want to accomplish from a fresh stock installed setup. 

One odd thing though, my sound is always muted when it boots up for the first time after a fresh isntall. Not sure why.

Muted on startup is a fairly typical symptom of a broken driver and/or configuration.

You should first test with the crack of the day audio ppa ([https://edge.launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://edge.launchpad.net/~ubuntu-audio-dev/+archive/ppa)). Then file a bug and add that information to the report.

ubuntu-bug linux should collect the information you need.

---

### Post by aceracer24 on 2010-04-26
> **gnomeuser said:**
> Muted on startup is a fairly typical symptom of a broken driver and/or configuration.

You should first test with the crack of the day audio ppa ([https://edge.launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://edge.launchpad.net/~ubuntu-audio-dev/+archive/ppa)). Then file a bug and add that information to the report.

ubuntu-bug linux should collect the information you need.

Thank you for the information and the ppa. 

When you say "first test with the ...." do you mean by just installing and seeing what happens? Or something more specific? My audio works for the most part. Besides the first boot off of a fresh install when the audio is muted, after that if I leave well enough alone, I have zero audio issues. It is when I try to get 5.1 surround sound through the SPDIF that things get doggy.

---

### Post by gnomeuser on 2010-04-26
> **aceracer24 said:**
> Thank you for the information and the ppa. 

When you say "first test with the ...." do you mean by just installing and seeing what happens? Or something more specific? My audio works for the most part. Besides the first boot off of a fresh install when the audio is muted, after that if I leave well enough alone, I have zero audio issues. It is when I try to get 5.1 surround sound through the SPDIF that things get doggy.

enable the ppa, install the kernel module from the ppa, update your system. Reboot and see if it still happens.

We currently cannot do anything except stereo over SPDIF, yet that is annoying, I too feel the pain of this deficiency.

---

### Post by aceracer24 on 2010-04-26
> **gnomeuser said:**
> enable the ppa, install the kernel module from the ppa, update your system. Reboot and see if it still happens.

We currently cannot do anything except stereo over SPDIF, yet that is annoying, I too feel the pain of this deficiency.

Ahh ok I think you thought that my sound is muted on every reboot/login. This is not the case. The only time it is muted is right after I do a fresh install and login for the first time. After that though the audio is never muted. 

Stereo only over SPDIF is not cool...not cool at all. From what I have managed to read from the internet, it sounds like you can get surround sound...I just have not been able to get it to work. Also seems kind of dumb when you consider Mythbuntu being an HTPC and SPDIF is very common for HTPCs. If not that then HDMI.

---

