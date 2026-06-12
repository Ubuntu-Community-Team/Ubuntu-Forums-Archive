---
title: "Alsa Mixer"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cggaret on 2010-02-22
I'm using an emu10k2 card and trying to record from the "Line Live Drive" source.  Using gnome-alsamixer I check the "Record" checkbox under the "Line Live Drive" fader and it has no effect.  The other record checkboxes seem to be working fine, with the "Capture" checkbox causing the horrid feedback loop that I expect it to.  If I select the Multi-Channel device in jackd I can record using the "Line Live Drive" input which is then shown as inputs 11 and 12.  So, the hardware is working.  Alsa seems to be working, but the gnome-alsamixer doesn't seem to be doing it's job.  Does anyone else have a SB Live! that they can confirm this with?  If it is confirmed, whom should I file the bug report with?

---

### Post by ranch hand on 2010-02-23
I do not have a SBLive card.  I do have an Audigy1 card.

If this would be of help to you I will need some kind of instruction on how to do what you want.  Haven't got a clue.

It is too bad my son doesn't follow this forum as he does record stuff.  He also has the Audigy1 card though.

---

### Post by cggaret on 2010-02-26
Update:  I can get things working using the curses based mixer in a terminal.  I can't get anything to turn on using the recording buttons in gnome-alsamixer.  So this is a gnome-alsamixer problem only.

---

### Post by seeker5528 on 2010-02-26
Are you selecting something in alsa-mixer that you are not selecting in gnome-alsa-mixer?

If it seems like gnome-alsa-mixer is not showing you everything you can go to 'Edit --> Sound Card Properties' and select the thing you want displayed.

Later, Seeker

---

