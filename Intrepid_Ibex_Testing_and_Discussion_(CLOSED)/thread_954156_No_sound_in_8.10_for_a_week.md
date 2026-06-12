---
title: "No sound in 8.10 for a week"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mojoguy on 2008-10-20
For about a week now I've been without sound on 8.10.  First symptoms were that sound would stop working after several hours of computer use.  It would play fine at first, but after a spell, all "normal" sound was replaced by a static-sounding hissing and popping noise.

After some updates, no I get no sound at all.  Anything that normally plays sound instead plays a very faint static and popping noise.  

No idea how to research this.  Any suggestions?  

FWIW: This is on a Dell 1505 originally purchased with Ubuntu pre-installed.  Though I'm now running 8.10, the hardware should all work with Ubuntu (and indeed has worked with Ubuntu for over a year).

---

### Post by davidcrew on 2008-10-21
Does the sound work on vista or any other operating system? It may be a hardware failure :_(

---

### Post by Av8or1ab on 2008-10-21
I am having the same issue and sound works fine in vista. I have also been using ubuntu 8.04.1 in a dual boot system and the sound has been acting as described above. I have a Dell E1705 with the Intel HDA audio device and a P945 chipset.

---

### Post by lindude on 2008-10-22
I have the same prob, no sound. Worked fine in 8.04:-(
Also Skype seems to work in headset mode if I choose hedset from the sound settings

---

### Post by legatek on 2008-10-22
This happened to me a couple of times and resetting my X session (Ctrl-Alt-Backspace) fixed it.

---

### Post by scragar on 2008-10-22
It's a pulse audio problem by the sounds of it, sounds like pulse is being used by something(flash proberly), and isn't disconnecting like it should, easiest fix is to just kill pulse off:
```
killall pulseaudio
```

---

### Post by mojoguy on 2008-10-23
> **scragar said:**
> It's a pulse audio problem by the sounds of it, sounds like pulse is being used by something(flash proberly), and isn't disconnecting like it should, easiest fix is to just kill pulse off:
```
killall pulseaudio
```

Mmmm...this is happening continually, despite multiple reboots over several days.

---

### Post by mojoguy on 2008-10-23
Interesting developments.  I went to System->Preferences->Sounds and changed the playback option in Sound Events and Music and Movies from "Autodetect" to to one of the HDA Intel STAC92xx Analog (OSS) options and sound worked for a few moments...right up until I tried to watch a YouTube video...  Then it stopped working (back to snap-crackle-n-pop).  Tinkering with the Sound Preferences thereafter did nothing to return it.

---

### Post by Sef on 2008-10-23
Moved to Ibex forum.

---

### Post by mojoguy on 2008-10-23
And yet further developments...

OK.  I got it working.  For how long, I don't know.  But I did the following:

Right click the speaker in the top menu-bar->open volume control.  The Volume control opens.

The PCM levels were turned all the way to the bottom.  I turned them all the way to the top.  Voila!  Sound works.

---

### Post by phorgan1 on 2008-10-25
No joy for me, all my levels are up, nothing's muted, the right driver is loaded (same one that worked fine in Hardy), but no sound.  I really wish I'd waited a bit to upgrade to Ibex.

Patrick

---

### Post by jbg7474 on 2008-10-25
Today I discovered that my volume buttons on my Dell D620 are controlling the PCM level instead of the master level.  The graphic that pops up when you hit a volume button also seems to be slaved to the PCM level instead of the master.  I upgraded from Hardy earlier this week.  Yesterday I had no sound (just a crackling) and discovered that it was because my PCM level was all the way down.  Yesterday, my volume buttons were controlling the master level.

I think it's possible that something has gotten mixed up in a standby (as it's a laptop, I standby often), or maybe one of the updates messed it up.

Edit: discovered on my Sound preferences that PCM was selected for keyboard control instead of Master.  Changing it to Master made everything work right.  Now, did I do that inadvertantly or did something change it for me?  Hmmm...

---

