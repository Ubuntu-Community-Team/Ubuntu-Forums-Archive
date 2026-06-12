---
title: "Beeping / Buzzing through mic input?"
date: 2018-05-20
forum: MINT
---

### Post by RallyDarkstrike on 2018-05-20
Hi all! I just finished putting together a PC from old parts I had  laying around to put Mint on for a family member to borrow for the time  being (Intel Core 2 Quad, 8GB RAM, Radeon HD4000 series video card).

All works perfectly, but I've noticed from testing it that the mic input  has a VERY noticeable and annoying buzzing/beeping sound constantly  which just won't do as this person uses Skype a lot to talk to  relatives. It does this through the front OR rear mic inputs and also  does it regardless of what mic I am using (I tested it with 2 different  mics)..

Link to a sample with me talking as a reference to how loud the beeping/buzzing is:
[https://drive.google.com/open?id=1GSJku ... 8qHZXRgrGH]("https://drive.google.com/open?id=1GSJkuC6A0hZj2Heh9U6PrG8qHZXRgrGH")

I've thought it might be a grounding issue...some of the screws for the  motherboard were a bit loose (not 'falling out' loose, but loose enough I  could gently tighten them a bit more without them being overtightened).  I also looked at the rear I/O Shield for the mobo and most of the tabs  on that are touching the board other than 3 or 4 out of the many.

This motherboard was previously in a different case with a different  power supply) running Windows 7 and there were no issues there.

Anybody have any suggestions or thoughts on how to fix the issue? Thanks so much!!!

---

### Post by #&amp;thj^% on 2018-05-20
Well this has not happened to me since 12.04, but what helped me here was to:
Open your terminal, and enter:
```
alsamixer
```  
And reduce the "Mic Boost and Internal "Mic Boost" (I set mine to a Zero value)
And after many hours of trying to figure out why this happened, it turned out for my setup that the microphone input is looped into my speakers.
Good Luck!

---

### Post by RallyDarkstrike on 2018-05-20
Thanks for the suggestion, but I believe I had tried that already! :(

---

