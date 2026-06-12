---
title: "no sound!!!! help!!!!!!!"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by fremantle on 2010-04-24
absolutely no sound output on lucid lynx (alpha, beta, rc)

i have sigmatel cmajor audio on a dell d600

the sound preferences dont detect any output sound driver,

---

### Post by dino99 on 2010-04-24
install gnome-alsamixer and check its settings

can follow this howto: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
                       [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

related links:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532310](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532310)
[http://ubuntuforums.org/showthread.php?t=750407](http://ubuntuforums.org/showthread.php?t=750407)
[http://alsa.opensrc.org/index.php/Category:Troubleshooting](http://alsa.opensrc.org/index.php/Category:Troubleshooting)

---

### Post by imedina on 2010-04-24
Thanks fremantle. It worked!
My problem was on alsamixer settings speaker option was mute. :(

---

