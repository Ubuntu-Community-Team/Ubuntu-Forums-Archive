---
title: "upgrading 4.10 as much as possible?"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by binskipy2k4 on 2005-03-31
can you upgrade 4.10 as far as 5.04?
I like 4.10 and 5.04 the preview and rc wont support my soundcard, which upon reading these forums i'm not the only one.. I dont know what has changed from 4.10 to the new one that left out the sblive audigy2. but thats ok.. so i was wondering will 5.04 final get sbaudigy2 support? if not, can warty be upgraded to say , kde 3.4 and more?
just wondering..
thanks

---

### Post by lao_V on 2005-03-31
If you modify your sources.list to hoary from warty, you should be able to  install  the software that is in hoary repositories (KDE 3.4 is now in main). As long as you don't do dist-upgrade you should be safe.

---

### Post by ubuntu_demon on 2005-03-31
[QUOTE=lao_V]If you modify your sources.list to hoary from warty, you should be able to  install  the software that is in hoary repositories (KDE 3.4 is now in main). As long as you don't do dist-upgrade you should be safe.[/QUOTE]
 I'm sorry but this is a lame advise to give to a newbie :). Mixing two releases without proper thought / apt-pinning is not very safe. Even if you're apt-pinning it's not very safe. You could render your entire system unusable.

You could use warty-backports until you read at the forums that someone got audigy 2 working.

see : 

[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)
[http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)

---

### Post by az on 2005-03-31
You should be able to upgrade from warty all the way to hoary, but still keep an updated warty kernel.  Just make your default grub kernel the warty one.  It will be supported for another year and a half.

This issue is a regression from Warty and you should add your experience to the relevant bug reports.  Please do.

bugzilla.ubuntu.com

---

### Post by kleeman on 2005-03-31
Hmm that's wierd I have a sblive Audigy 2 which works fine on both Warty and Hoary. Do you have a particular variant of Audigy 2? I read somewhere  that some variants don't work with alsa but am pretty surprised that it works in warty but not hoary....

---

### Post by binskipy2k4 on 2005-03-31
well if you know where there's a "HOW TO" to get the sb audigy2 working please link me.. i really relaly like hoary, but 4.10 has my sc working perfectly
5.04 preview and rc wont.. i'm not exactly a wetbehind the ears newbie, but i'm not a power user, so any suggestions would be most appreciated..

---

### Post by kleeman on 2005-03-31
Follow the alsa troubleshooter here starting at step 4:

[http://alsa.opensrc.org/index.php?page=TroubleShooting](http://alsa.opensrc.org/index.php?page=TroubleShooting)

---

### Post by jery_wang2002 on 2005-03-31
[QUOTE=kleeman]Hmm that's wierd I have a sblive Audigy 2 which works fine on both Warty and Hoary. Do you have a particular variant of Audigy 2? I read somewhere  that some variants don't work with alsa but am pretty surprised that it works in warty but not hoary....[/QUOTE]
 Your avatar is cool. Where did you get that?

---

### Post by kleeman on 2005-04-01
I use lyx and they have a great wiki where I picked up some nice new icons:

[http://wiki.lyx.org/LyX/Icons](http://wiki.lyx.org/LyX/Icons)

---

