---
title: "LT3103 Front mic strange issues Karmic Koala"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by diffy on 2009-10-06
Hi !

I made some tests with my front mic ( the one up to the screen ) today. I was trying to use my front microphone with skype and... it never worked.
So I try to record something with the Sound Recorder installed by default with Ubuntu, and here it works. I have a lot of noise but I can hear my voice almost clearly.

So I dig a little bit in alsamixer, and PulseAudio parameters but I didn't get something which works with skype.

Then I plug an external microphone on the side of the laptop and there everything works perfectly...

I was wondering if someone could explain my how that front mic is wired to the sound card, and how to use it. The sound card got 2 inputs ? or is it the same input switched between the front mic and the external mic when we plug something in ? 

Tell me if you also have some issues with you're LT3103 or some solutions :) 

Thanks
Diffy

---

### Post by diffy on 2009-10-28
I have the solution,
In the volume manager, the front mic has two levels, left and right. I just put down to 0 the right channel, and put only the left channel to 100%. Now the front mic works

---

