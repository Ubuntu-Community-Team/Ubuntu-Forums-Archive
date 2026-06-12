---
title: "Ubuntu Jaunty and Soundblaster X-FI"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gabriel2007 on 2009-03-13
Hi everybody

Does anybody know how to make this card work ??????????? it is not detected by the system 

:popcorn: waiting till somebody answers me and thanks !

---

### Post by cariboo on 2009-03-13
I have asked the mods to move this to the appropriate place, where you will get help with your problem.

Jim

---

### Post by overdrank on 2009-03-13
Moved to Jaunty Jackalope Testing and Discussion

---

### Post by keenish27 on 2009-03-18
No luck figuring this one out yet?

---

### Post by kj74 on 2009-03-18
Download crappy drivers form Creative site and install. You're going to have lots of problems. First thing to do is remove pulseaudio if you want to try. I doupt there will ever be even half decent linux drivers x-fi.

---

### Post by keenish27 on 2009-03-18
Ok, I downloaded the 64bit drivers....decompressed them and followed the read me.  It basically said to navigate to the source directory and then do the following in the terminal.

```

sudo make
sudo make install

```

Anyway I did that and still no sound.  Also in "sound" under system > preferences the only device I have to select from is "Playback: Null Output (PulseAudio Mixer).

What am I doing wrong?

---

### Post by milio1401 on 2009-03-18
i read somewhere you have to install alsamixergui,and then install the  creative drivers then reboot, it worked for me,by the way i'm using  ubuntu intrepid ibex  64-bit version.give it a try.):P

---

### Post by keenish27 on 2009-03-18
> **milio1401 said:**
> i read somewhere you have to install alsamixergui,and then install the  creative drivers then reboot, it worked for me,by the way i'm using  ubuntu intrepid ibex  64-bit version.give it a try.):P

I just did that...no deal =(.  Do I need to get rid of pulse audio or something?  This is just a little frustrating cause it is the only thing not working.

Thanks for your help.

EDIT: I just noticed that kj74 said I needed to remove it...however when I try to remove pulseaudio it tells me I need to remove ubuntu-desktop.  Isn't that one kind of important?

---

### Post by Reiger on 2009-03-18
Check:
[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)
[http://ubuntuforums.org/showpost.php?p=6369503&postcount=148](http://ubuntuforums.org/showpost.php?p=6369503&postcount=148)

That's how I got my PCI-e X-Fi to work.

---

### Post by keenish27 on 2009-03-18
> **Reiger said:**
> Check:
[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)
[http://ubuntuforums.org/showpost.php?p=6369503&postcount=148](http://ubuntuforums.org/showpost.php?p=6369503&postcount=148)

That's how I got my PCI-e X-Fi to work.

Thanks soooo much!  My card had a subsystem of 44....it works!

---

