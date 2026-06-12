---
title: "Sound doesn't work after botched 8.10 upgrade."
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by longboarder543 on 2008-11-04
I started the upgrade from 8.04 to 8.10 using the update manager, and walked away from my laptop. My wife later unknowingly closed the laptop lid during the install, causing the system to suspend. When I went to check on it a few hours later, the machine was hung with the lcd off but I could tell it was still on. After a couple of minutes, I shut down the machine. Upon reboot, X wouldn't load. I'm assuming it only got part of the way through the upgrade. I rebooted into the recovery mode (one of the 3 grub options, can't remember it's exact name), and ran the dpkg option. At that point, it seemed to pick up where it left off and complete the install. I now have an *almost* fully-functional Intrepid install it seems, but my sound is not working. I've checked the sound settings in Administration and it seems to be set correctly (ALSA). My laptop is a Dell Inspiron 2200. Sound has worked fine for the last several versions of Ubuntu. I'll post any logs anyone needs if you ask. Thanks in advance, longboarder543

---

### Post by forest.r on 2008-11-04
I may be having the same problem. Can your computer make any sound at all? Mine can't. HELP US PLEASE!

when i test my sound setting i get an error saying "gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback."

---

### Post by jellyfisharepretty on 2008-11-04
I have no sound as well right after upgrading to 8.10.  Sound was working flawlessy with my Audigy 2 card in 8.04.

UPDATE : For me, going into volume control applet and *unchecking* Audigy Analog/Digital Output Jack restored sound.

Now, if I could just find why my volume down keyboard key opens new firefox windows, I will be all set...

---

### Post by forest.r on 2008-11-04
[QUOTE=]Now, if I could just find why my volume down keyboard key opens new firefox windows, I will be all set...[/QUOTE]

Try editing your keyboard shortcuts (system>preferences>keyboard shortcuts). Maybe you can fix it that way.

---

### Post by jellyfisharepretty on 2008-11-04
Yeah, thanks forest.r, I was precisely looking at that.  However I disabled the open browser key, and purposefully set my volume down key to volume down, but to no effect.

I am now investigating whether it is the KeyTouch utility that I had in Hardy that is causing the problem.

But I don't want to hijack this thread into a keyboard problem, when it is really about a sound problem.

---

### Post by forest.r on 2008-11-04
Try this Longboarder, switch **everything** to OSS from ASLA. That should fix just about everything but the sound in flash objects. I got this information from [this thread]("http://ubuntuforums.org/showthread.php?t=965057"), hope that helps.

---

### Post by nutnub on 2008-12-03
Hey, I saw your post. And... though I may be a complete newbie to all of this Ubuntu stuff, I think I may have found a solution.

What worked for me is right clicking the volume control applet on the bottom taskbar(I believe that's what it's called). Then, open up "Master Volume Control." What happened for me is the PCM thing (I don't know what that is) was set to zero, which cancelled out my sound for some reason. When you boost up the bar, it should fix everything up.

Send back if this worked for you! :D

Best of luck,
Joe

---

### Post by sambarusty on 2008-12-03
I found that stupid thing pops down at random times, so be aware.  I had the same issue a few weeks back and on and off since, I go there and turn it back up and I am ok.  Not sure why it keeps moving, Obviously I am not touching it.

---

