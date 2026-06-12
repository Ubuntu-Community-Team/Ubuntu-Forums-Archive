---
title: "Python and locales screwed up?"
date: 2010-01-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-01-07
I've been getting a slew of different error messages regarding improper locales and Python over the past few days as I upgrade my packages and run certain programs.

Am I alone?

---

### Post by dagrump on 2010-01-07
I was getting  some odd stuff too. I got ticked & copied my apt cache, source list, & generated a package list with synaptic & reinstalled.
Took about an hour, now I'm waiting for some updates to see if the odd ball stuff was from updates the night before last.
I didn't notice any of locale not set errors during the reinstall though. So it was most likely fixed, & my old dumb butt just did a reinstall for nothing.

---

### Post by Starks on 2010-01-07
I had done a root format and reinstall last night for unrelated problems. This issue persisted though.

---

### Post by dagrump on 2010-01-07
Well, I just noticed the ppa's I've been using were not in the source list I had saved in /home, so I reloaded them & updated. I no longer see any error messages.
I did delete .gdesklets from /home & haven't reloaded it so that might bring my issues back? But, for the moment I'm going stop as I want to watch the Texas vs Bama game. Guess I'll see what happens with the next round of updates & then reload gdesklets & see if that breaks it.

---

### Post by ranch hand on 2010-01-07
The latest glibc update seems to have fixed this problem for all my installs.

---

### Post by dino99 on 2010-01-08
yes problem have gone now with latest glibc packages. Clean your cache, update and it should be good then.

Previously a command line solved this problem: locale-gen --purge ( no more needed)

---

