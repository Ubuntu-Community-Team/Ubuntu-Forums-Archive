---
title: "No Sound after login"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by knavarathna92 on 2009-04-17
Hey guys,
I'm running Ubuntu 9.04rc and have a sound problem in which I originally had no sound.  After some troubleshooting I was able to get the sound that plays when the login screen appears (the drumbeats).  After I log in, No sound plays BUT I can still hear faint pops and hisses for the login sound.  After this, no sound plays at all (music, flash, etc...).

I know there are a lot of issues with ubuntu 9.04 and my intel HD-audio ICH8 soundcard but from the people who posted so far they're missing all of their sound so maybe my issue is different?  Really confused, any help would be appreciated.

---

### Post by sonicb00m on 2009-04-17
log out and in again. sometimes i have this problem and pulseaudio doesn't initialise.

---

### Post by Julian Lewis on 2009-04-17
I ran this script, AlsaUpgrade-1.0.x-rev-1.16.sh. Go google for it down load the tar file, extract the above script. sudo it with option -di

This will do a complete re install of alsa. It works for my 9.04 acer, on 8.10 and 8.04 and fixed loads of sound problems.

---

### Post by Julian Lewis on 2009-04-17
here is the link

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by knavarathna92 on 2009-04-17
that did it, thanks a bunch :-)

---

