---
title: "No sound on Dell Inspiron 1525 after upgrade to 8.04"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by gavinjb on 2008-04-29
Hi,

I recently upgraded my Inspiron from 7.10 to 8.04 and like a lot of people I have no sound.  Below I have listed what I have tried.

I followed the instruction here [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade) and where before I had no sound card I now have one listed (though in LiveCd I have Master, PCM & Front in Volume Control and from HD Boot only have PCM, Live Cd gives me sound)

I have compared the alsa-base files from my HD to the LiveCd and they are identical but no joy.

```

aplay -l
**** List of PLAYBACK Hardware Devices ****

```

```

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

```

Error Message when trying to test sound card in System/Prefs/Sound
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument

```

With the error I get and the differences in Volume Control my thought is that it is trying to use a wrong driver, but then my knowledge of Linux at this level is very limited so I am probably wrong, anyone with any ideas.

Thanks,



Gavin,

---

### Post by phrawzty on 2008-04-30
Hi,

I also had no sound after the 7.10 -> 8.04 upgrade on my Inspiron 6400.  I followed the instructions available at the Ubuntu Community documentation, and it solved the problem :
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Specifically, the steps outlined under the "Alsa Driver Compilation / Using alsa-source" section.  After following the instructions noted, then rebooting, i had sound again !

---

### Post by gavinjb on 2008-04-30
Thanks, got it to work in the end, I decided that as I had tried so many things I would restore Dells image and upgrade again, I then followed the instructions in Dells wiki (see my original post) and sound now works :)

---

