---
title: "Hate to do it, but I can't get sound working either"
date: 2005-02-22
forum: Installation &amp; Upgrades
---

### Post by yerch on 2005-02-22
I'm sure y'all must get tired of helping people with sound problems, but I've scoured this board (and everything else I can find) a hundred times and can't figure out how to get sound working in Ubuntu.  My fear is that now that I've tried everything suggested for everyone else I've made a worse mess than if I'd never tried at all.

I have a Turtle Beach Santa Cruz sound card.  I also have some kind of SoundMax onboard card that I disabled (at least in Windows - don't know if that makes a difference) - yet I get no sound from anywhere.  I think I've been pretty thorough in checking to make sure nothing is muted.  But beyond that I can't tell if Ubuntu recognizes my sound card and/or if it is installed properly.  

I've tried everything.  Please help!

---

### Post by kassetra on 2005-02-22
[QUOTE=yerch]I'm sure y'all must get tired of helping people with sound problems, but I've scoured this board (and everything else I can find) a hundred times and can't figure out how to get sound working in Ubuntu. My fear is that now that I've tried everything suggested for everyone else I've made a worse mess than if I'd never tried at all.

I have a Turtle Beach Santa Cruz sound card. I also have some kind of SoundMax onboard card that I disabled (at least in Windows - don't know if that makes a difference) - yet I get no sound from anywhere. I think I've been pretty thorough in checking to make sure nothing is muted. But beyond that I can't tell if Ubuntu recognizes my sound card and/or if it is installed properly. 

I've tried everything.  Please help![/QUOTE]

Ok, first of all, it's very possible your onboard sound is still active if you didn't disable it in the bios.

So now let's take our first look see:
Open a terminal (Applications->System Tools->Terminal) and type this command:
 ```
lspci
``` 
Now look through the list that zooms up for Multimedia audio controller and tell me what it says just to the right of those words.

---

### Post by yerch on 2005-02-22
There are two entries for Multimedia Audio Controller:

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 05)

0000:02:0a.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

I, of course, have no idea what either of those mean.  Thanks for replying.  Hopefully we can get this sorted out.  I feel like I've come a long way with Ubuntu already and if I can make it make sound I'll be pleased as punch (well... if I could just get my fan to stop running - but that's for another day.)

Thanks,
Eric

---

### Post by goedson on 2005-02-22
[QUOTE=yerch]There are two entries for Multimedia Audio Controller:

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 05)

0000:02:0a.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

I, of course, have no idea what either of those mean.  Thanks for replying.  Hopefully we can get this sorted out.  I feel like I've come a long way with Ubuntu already and if I can make it make sound I'll be pleased as punch (well... if I could just get my fan to stop running - but that's for another day.)

Thanks,
Eric[/QUOTE]

Have you tried running alsaconf and have it detect and configure your soundcard?

---

### Post by scoon on 2005-02-22
Hey there, 

The Cirrus Logic is your santa cruz.  Disable the onboard sound in your bios.  Then you should start to hear some sound. 


scoon

---

### Post by yerch on 2005-02-22
This is ultra-dumb, but what is my bios and how do I get there to disable the on-board soundcard?

Thanks,
yerch

---

### Post by yerch on 2005-02-23
Ok, I have managed to somewhat dislodge my head from my bum, found out what BIOS was, got into it, and disabled the onboard sound.

Now when I type lspci only the Cirrus comes up next to Multimedia Audio Controller.  this feels like a big step forward.  However, not a peep comes out of the computer.  

I have not been able to find or run anything called alsaconf.  I have an alsaconf-base, but I can't seem to get to it or make it do anything.  

Any helpful insights are still greatly appreciated.  I think I'm close.

Thanks,
yerch

---

### Post by scoon on 2005-02-23
Hey there, 

Open up a terminal and type alsamixer.  That will allow you to adjust the different levels which will get you your sound. 


scoon

---

### Post by yerch on 2005-02-23
So close now I can hardly stand it!!!

I do have some sound.  I can get sound to come out of the front two speakers, but the system attached to the rear speakers remains silent.  I've played with everything I can think of.  Any additional suggestions?

Thanks to all for all your help.  It has been very helpful and very kind.  

Thanks again,
yerch

---

### Post by scoon on 2005-02-23
Hey there, 

Go here for some ideas: [http://www.alsa-project.org/](http://www.alsa-project.org/)

Hopefully things have changed but I used to have that card and the cirrus chipset was closed source and surround really only worked in windows.  With some tweaking I could get surround to work w/ xmms but that was it.  As a result of that, I purchased a Creative audigy2 zs.  Hopefully, things have changed now. 


scoon

---

