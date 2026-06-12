---
title: "Ubuntu crashed, unbootable. where to recover data from"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by minimustangs on 2010-01-14
Last night my install of Ubuntu 9.10 crashed. Multiple attempts to recover fail. I caould get to the login screen but then I would get one of two errors. One was something to do with GNOME not loading or configuring Power.." something". I cold get by that, but then a notice came up that evolution -alarm - notify wasn't working or something like that.

No matter about all of that, I did a parallel install and recovered all my files. What I would like to try is to run evolution from the first install partition to make Evolution perform a backup so I can save my emails.

Wheree does the actual eveoltuion "executable" sit on a partition? I'm I can launch the copy of Evolution on the messed up partition, I might have a chance at saving my email. Alternatively, where are the files for eveolution email stored?

Thanks

---

### Post by Kevbert on 2010-01-14
Evolution data is stored in a hidden folder in your home directory, so for me it would be /home/kevin/.evolution (note the '.' means it's hidden).

---

### Post by minimustangs on 2010-01-14
Thanks Kevin, replacing the .evolution folder works flawlessly.

Now to wipe this drive and re-install Ubuntu clean

Thanks again.

Steve

---

### Post by minimustangs on 2010-01-16
Well I'm up and running, no loss of data. What an episode though.

- The install I was using was a 9.04 install that I later upgraded to 9.10. I didn't seem to suffer problems with audio or USB that others were reporting. 

- I started having problems about a week ago after a regular series of updates.

- after recovering my data, did a fresh install of 9.10. Slow, poor graphics, stuttery mouse, USB very slow. I wiped system and backleveled to 9.04

- 9.04 runs smooth, no USB issues, no audio issues, No Issues.

I don't recommend that anyone run 9.10 until those issues get corrected. I'm back to 9.04 and amvery happy with system performance. Everything seems good... Flash ( after some tweaking), MP3's, TV off the web....

OH yeah almost forgot...under 9.10 wireless internet was flakey, problematic. Under 9.04 it works like a charm.

As for my original mail issue, SOLVED.

Steve

---

