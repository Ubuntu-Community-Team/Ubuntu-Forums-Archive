---
title: "ugh...PulseAudio a pile of crap (more Hardy facepalms)?"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by HangukMiguk on 2008-04-27
Wow, I remember flipping out hoping PulseAudio would be better (or comparable) to ALSA during install.

I guess I was right, because my sound server now seems to only be able to handle one program doing sound.  Firefox ran a sound, and now Pidgin refuses to play any sounds, which it was before Firefox ran.

This is getting ridiculous.  I'm starting to debate moving to DesktopBSD based on Hardy.

---

### Post by factotum218 on 2008-04-27
No, no. Pulse audio isn't a pile of crap in its self. It is just a result of all the praise Fedora received for implementing it. Team Ubuntu felt like only an Ubuntu dev can and plopped it in just to sort of say "there, we have it to, yay us!"
I would go with what you have planned. Check out *BSD. Of course you must realize that IT IS NOT LINUX. Don't worry you will be told over and over again. Yes, it has a shell and runs gnome/kde/xfce/many linux apps/ but the directory structure is different.

If it doesn't work out for you, check out either Debian or Slackware. They are both quite fun. And, well, that is where I am headed in the next day or two. Might opt for slackware first to see how it goes. If not, back to trusty ol' Debain it is.

---

### Post by HangukMiguk on 2008-04-27
So, let me get this straight, Canonical just threw Pulse on top of Hardy with no real attempt at implementation just to say "OMGPULSEZORS!" and left us with the problems?

Any way it's fixable on my end?

Meh between the fact that I can't mount my external and my sound problems, this does like the excuse I need to switch around again.

---

### Post by citizenc on 2008-04-27
I had the same problem.

Solved it by going back to the ALSA sound mixer:

System -> Preferences -> Sound

On the "devices" tab, ensure that the ALSA driver is enabled for everything. (It probably says "auto detect" right now.)

---

### Post by HangukMiguk on 2008-04-27
> **citizenc said:**
> I had the same problem.

Solved it by going back to the ALSA sound mixer:

System -> Preferences -> Sound

On the "devices" tab, ensure that the ALSA driver is enabled for everything. (It probably says "auto detect" right now.)

Ok, that got my sounds working again.  Now on to my mountpoints...

Thanks.

---

### Post by Lagos on 2008-04-29
im having the same problem. changed to alsa. now i can hear pidgin sounds but totem still wont play audio and results in an error saying the sound system is busy.

---

### Post by MemoryDump on 2008-04-29
I strongly believe pulse was improperly released... lack of documentation and proper pre-installed configuration tools... especially for newer users.. yes pulse is aparently really good... however it's a huge learning curve for many... I know for myself personally.. I had high expectations.. and if it weren't for these forums I would have given up by now ;)

---

### Post by a7j_72 on 2009-11-20
Wow... fast forward about a year... in 9.10studio. 

I love pulse's feature in which I could run simultaneously 2 sound cards and choose which apps run in which 1...  

I still hear all this "pulse audio is crap" talk, I have yet to see that side of it. Maybe its just good luck and good hardware choices on my part... 

Just a note for everyone... Pulse is a thing of beauty (once you get it running smoothly) ;p

---

### Post by Elktro on 2009-12-25
And I still say that pulse audio is crap, although I think there has been progress to better. But I still have to run killall pulseaudio to run a number of programs like Audacity, Skype or MythTv to name few.  

Pulseaudio might have fabulous little features but for most users they don't mean anything. Most are, however, extremely annoyed if a new sound server breaks a working program, regardless does the problem actually lay in the new sound server or not.

---

