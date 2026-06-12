---
title: "system beep is just an anoying bzzzz"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by snivek on 2009-10-21
What I believe is a system beep is just a staticy bzzz sound coming from my PC speakers.  I get this when I backspace in a terminal with nothing to delete or if I am tabbing something out that has multiple possibilities.  I have also noticed it in a web browser when trying to delete the url when there are no characters left to delete. 

If I execute modprobe pcspkr then I no longer get any sounds for those events.  Which I find funny because I typically rmmod pcspkr or blacklist it to remove the normal system beep.

Ubuntu 9.10
Dell Latitude E6400

--Kevin

---

### Post by novafluxx on 2009-10-21
> **snivek said:**
> What I believe is a system beep is just a staticy bzzz sound coming from my PC speakers.  I get this when I backspace in a terminal with nothing to delete or if I am tabbing something out that has multiple possibilities.  I have also noticed it in a web browser when trying to delete the url when there are no characters left to delete. 

If I execute modprobe pcspkr then I no longer get any sounds for those events.  Which I find funny because I typically rmmod pcspkr or blacklist it to remove the normal system beep.

Ubuntu 9.10
Dell Latitude E6400

--Kevin

I need to disable this, please tell me exactly how to do this!

---

### Post by wojox on 2009-10-21
Step 1

Open up a Terminal and type:

sudo alsamixer

Now using your left/right arrow keys navigate over to PC Beep and press M on your keyboard, you'll see MM appear under the volume bar, this basically means it's been muted now press Esc to exit.

Step 2

Now run the command:

sudo alsactl store

This will basically save the changes you made.

---

### Post by novafluxx on 2009-10-21
> **wojox said:**
> Step 1

Open up a Terminal and type:

sudo alsamixer

Now using your left/right arrow keys navigate over to PC Beep and press M on your keyboard, you'll see MM appear under the volume bar, this basically means it's been muted now press Esc to exit.

Step 2

Now run the command:

sudo alsactl store

This will basically save the changes you made.

OK, that much I did know...I thought PulseAudio would make that process a little different...thank you!

---

