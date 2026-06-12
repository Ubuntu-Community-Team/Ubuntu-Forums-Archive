---
title: "CLI = no ~/folders ?"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by KazaRgr on 2011-03-04
hello all,i just finished my CLI (command line install) with openbox as WM (no DE) and thunar for file manager & i just noticed that in my home folder there is NONE of the usual folders (downloads, documents etc..) was that supposed to happen or i epic-failed on something?

ps: if i am supposed to create them myself, can anyone gimme their default names in english? i dont remember all the folders. xD

ps2: the laptop makes a really annoying n loud bEEEP when i cant backspace anymore in terminal or things like that + the monitor has gone really dark after i woke up the monitor for first time, any ideas? :/ may i add that i havent installed most core apps yet (power-manager, etc..)

Thnx in advance,
alex.

---

### Post by KazaRgr on 2011-03-04
/bump & cry :(

---

### Post by urukrama on 2011-03-05
> **KazaRgr said:**
> hello all,i just finished my CLI (command line install) with openbox as WM (no DE) and thunar for file manager & i just noticed that in my home folder there is NONE of the usual folders (downloads, documents etc..) was that supposed to happen or i epic-failed on something?


Nothing to worry about. Just create those folders yourself, either through the file manager of your choice, or from the command line with *mkdir DIRECTORY_NAME*

The beep is normal too. To disable it, follow these instructions: [http://blog.wolffmyren.com/2008/10/20/disable-ubuntu-system-beep/](http://blog.wolffmyren.com/2008/10/20/disable-ubuntu-system-beep/)

---

### Post by KazaRgr on 2011-03-05
thank you mr. urukrama :) your OB guide is also extremely useful.
may i ask and something else, my ubuntu always has the bad habbit to show more ram being used than is really being used, e.g it shows 400mb ram but if u add all the running processes, it goes about half ~200mb :/ is there anyway to fix that so i can know the real amount that is being used?

-- aw aw and something last, there's something wrong with my synaptic, it wont let me write in the "Quick Search" field, which is really annoying and weird o.O

---

### Post by urukrama on 2011-03-06
> **KazaRgr said:**
> thank you mr. urukrama :) your OB guide is also extremely useful.
may i ask and something else, my ubuntu always has the bad habbit to show more ram being used than is really being used, e.g it shows 400mb ram but if u add all the running processes, it goes about half ~200mb :/ is there anyway to fix that so i can know the real amount that is being used?


I don't know how you view your memory usage, but the difference might be in RAM used and cached (which will be higher). You can use the command [FONT="Courier New"]free -m[/FONT] (in a terminal) to get a more detailed view of your actual current RAM usage.

---

### Post by urukrama on 2011-03-06
And as for the Synaptic problem, I suggest you start a new thread for that. Your problem might get more attention that way.

---

