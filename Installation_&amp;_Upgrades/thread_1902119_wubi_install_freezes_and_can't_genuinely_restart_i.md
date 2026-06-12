---
title: "wubi install freezes and can't genuinely restart install"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by BMEdwards37 on 2011-12-30
Hey guys, got a Toshiba NB505 today and tried to install Ubuntu via wubi. The first time i tried to install it, it froze at amd64, i assume, because i can only have the 32 bit version. adding --32bit to the target skips the problematic amd64 file but just moves on to a different one that gets stuck. No matter how many times i uninstall/redownload wubi, i've deleted a wubi text file from my temp folder, i just can't get the wubi install to start fresh. Whenever i start it it just picks up where i left off, even though if you look in the newly created Ubuntu file, there isn't as much there as the progress bar would suggest.

Anyone know how i can make wubi forget its previous progress? I think my problem would be solved that way.

---

### Post by BMEdwards37 on 2011-12-30
Not really "solved" per se, but i just downloaded the iso separately and reran wubi with the iso in the same folder. Installed properly, it was the download itself that wubi was having trouble with so i just bypassed it and did it myself.

---

