---
title: "Major 9.10 upgrade problems!!"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by teamsuperoxide on 2009-12-06
Hi everone,
these problems have probably been addressed and solutions post elsewhere but my internet is so slow (problem #2) on this site I haven't the patients to search for them.

Here's where my problems started. I upgraded from 8.04 to 9.10 over the past couple of days, following the instructions provided by Ubuntu. I decided to upgrade in the (foolish?) hope that the built-in microphones on my laptop (dell inspiron 1512) and eject button would begin to work. However, now the eject button works but almost nothing else doesn't! 

Here are my current problems:

1# Built in webcam not working (hardware not detected). It worked in all other versions.

2# Internet extremely slow! Supposedly this is a known bug of 9.10, where is the fix?

3# media buttons (the play, skip, volume buttons) don't work. They worked up until 9.04.

4# Built-in microphone not working (never worked)

5# Wine was installed and running well in 8.04 but now its disappeared. Attempts to install new version (following wineHQ instructions) have failed, the installer tells me to repair the original packages but I can't find them.


As you've probably guessed I'm a major linux noob so please make any solutions as basic as possible to follow.

Any help will be greatly appreciated.

PS: Alternatively, where can I find instructions on downgrading back to 8.10 (everything worked great then)?

---

### Post by teamsuperoxide on 2009-12-06
I've seemed to have solved the the internet problem by following the instructions of post #13 at [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

---

### Post by teamsuperoxide on 2009-12-06
weird...... now the webcam works.... and wine installed on the 3rd attempt.......

Anyway, if anyone can direct me on how to fix problems #3 and #4, I'd be much obliged :-)

---

### Post by mionescu on 2009-12-06
Can you provide more details? Do you have a laptop or a desktop? What model? What is your soundcard? Did you try to install the padevchooser and/or pavucontrol packages? I found them very helpful in setting the sound/microphone settings.

---

