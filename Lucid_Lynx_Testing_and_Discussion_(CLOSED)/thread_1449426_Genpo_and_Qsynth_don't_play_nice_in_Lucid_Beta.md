---
title: "Genpo and Qsynth don't play nice in Lucid Beta"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pdxken on 2010-04-07
Worked fine in Karmic.
Genpo connected to Qsynth through qjackctl.
Qsynth has cinema_organ_cf102.sf2.

This organ soundFont basically has a set of fonts with vibrato on and off using bank 0 and bank 1 respectively.

If I try to use bank 1 it works until a stop (voice) is turned off in genpo. If I then activate another stop that channel in qsynth then goes blank instead of assigning the new stop to that channel. Also the sounds that should come from bank 1 are actually bank 0 sounds.

Bank 0 works fine.
It seems that Qsynth version 0.3.5 won't recognize bank 1 anymore. version 0.2.5 in Karmic worked just fine in this respect. Genpo is same version as Karmic version 0.9.8

This sounds confusing even to me but had a tough time wording it.

Has Qsynth 0.3.5 picked up a bug or has it changed to be more midi correct?
Is bank 1 allowed in midi?

GM seems to have banks 0,8,9,16,128 or somesuch.

Confused. Ken.

---

