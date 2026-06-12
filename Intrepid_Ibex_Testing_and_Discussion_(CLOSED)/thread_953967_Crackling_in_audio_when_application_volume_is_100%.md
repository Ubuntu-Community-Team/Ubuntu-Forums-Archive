---
title: "Crackling in audio when application volume is 100%"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SveinT on 2008-10-20
Pulseaudio version: 0.9.10

I just installed fresh install of Intrepid beta and upgraded to latest packages. I was using Hardy before and had no problems then.

After the Intrepid install the sound is very loud and there's lots of noise when playing back sounds. I thought the volume controls was maxed out, as that would give similar symptoms on a working setup. However, they were barely half of max. So I installed padevchooser and started looking for what could be wrong.

The thing that fixes it is reducing the application volume to no more than 60-70%, if any louder the audio will sound really garbled/crackling. Now, the problems is that the volume setting is 100% by default so all new programs I launch sounds terrible. The sliders will occasionally reset also making it unusable. Note that reducing the sound output from e.g. music programs will let me have the sliders at 100%. But programs like pidgin and login/logout sounds are set at a too high level by default (and no option to adjust them).

The positive thing is that I can now have louder output without crackling than before if I adjust all the sliders correctly. Anyways, any help would be greatly appreciated!


Bug report: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/285866](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/285866)

---

