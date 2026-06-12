---
title: "No audio in VirtualBox after upgrade to 11.04?"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Tygre on 2011-05-05
Hello fabulous Ubuntu comunity!

As a relatively recent adopter of Ubuntu, and Linux in general, first let me say thank you for the innumerable problems that a quick visit to these forums has solved for me in the past!

I now have a new problem, which I have not yet been able to solve via forums. (maybe my forum-fu is weak?)  

I just upgraded to 11.04, and apart from an initial freakout because I didn't realize why all my settings were borked*, I haven't had any difficulties...  until today.  I ran my virtual WinXP machine (VirtualBox) to watch some streaming Netflix, and the sound didn't work.  Sound still works under Ubuntu just fine.  No idea why it didn't survive in my virtual machine.

I noticed when I started that it said there was an upgrade for the VirtualBox software, so I did that, but that didn't fix it either.  I'm using PusleAudio for the Host Driver and ICH AC97 for the audio controller on my virtual XP machine.  These worked before the upgrade, now...  not so much.  I tried switching the driver to ALSA and the controller to SoundBlaster 16 (and other different available combos, etc), to no avail. 

Does anyone have any ideas?

Thanks!

* It turns out that crap pile, Unity, did away with all my nice custom panel layouts and configs and replaced them with something ugly, unwanted, and non-intuitive. I'm using "Ubuntu Classic" now because Unity is horrible.

---

### Post by pi.boy.travis on 2011-05-17
> **Tygre said:**
> Hello fabulous Ubuntu comunity!

As a relatively recent adopter of Ubuntu, and Linux in general, first let me say thank you for the innumerable problems that a quick visit to these forums has solved for me in the past!

I now have a new problem, which I have not yet been able to solve via forums. (maybe my forum-fu is weak?)  

I just upgraded to 11.04, and apart from an initial freakout because I didn't realize why all my settings were borked*, I haven't had any difficulties...  until today.  I ran my virtual WinXP machine (VirtualBox) to watch some streaming Netflix, and the sound didn't work.  Sound still works under Ubuntu just fine.  No idea why it didn't survive in my virtual machine.

I noticed when I started that it said there was an upgrade for the VirtualBox software, so I did that, but that didn't fix it either.  I'm using PusleAudio for the Host Driver and ICH AC97 for the audio controller on my virtual XP machine.  These worked before the upgrade, now...  not so much.  I tried switching the driver to ALSA and the controller to SoundBlaster 16 (and other different available combos, etc), to no avail. 

Does anyone have any ideas?

Thanks!

* It turns out that crap pile, Unity, did away with all my nice custom panel layouts and configs and replaced them with something ugly, unwanted, and non-intuitive. I'm using "Ubuntu Classic" now because Unity is horrible.

I'm having this issue as well. Linux, BSD, Windows, and Mac OS X virtual machines all have no sound. I suspect it has something to do with the way the new VirtualBox interfaces with the new version of Pulseaudio. If I find a solution, I'll post it here.

---

### Post by fafarafa on 2011-05-25
Had the same problem,

Reinstalled Guest Additions on my XP virtual machine, and everything works fine.

Lorcan

---

### Post by pi.boy.travis on 2011-05-27
> **fafarafa said:**
> Had the same problem,

Reinstalled Guest Additions on my XP virtual machine, and everything works fine.

Lorcan

Whoops, I forgot about this thread! Updating Guest Additions seems to fix the issue.

---

