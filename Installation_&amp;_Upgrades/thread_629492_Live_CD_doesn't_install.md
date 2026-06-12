---
title: "Live CD doesn't install"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by rtrdom on 2007-12-02
Attempts to use live CD fail. History: first computer;  Had to change motherboard. New motherboard. Although same Intel P4 part nr.used to order new board, required
a change of RAM from DDR to DDR2 because of slots on board. DDR would not fit.
Had removed hard drive with only Ubuntu installed so I could send second computer
to grandson. First computer, with new motherboard, new RAM, new processor (Intel
P4) upon attempts to boot yields following errors:
(with Intel new board disc in CD drive) [24.607304] crc error; [24.608516] Kernel Panic -
not syncing: VFS: Unable to mount root fs on unknown block (0,0).
(with Live CD in CD drive) [550.504181] crc error; [550.505510] Kernel Panic - not syncing: VFS: uable to mount root fs on unkown-block (104,1)
     Any other hard drive works properly with live CD. All harddrives would let me install
Windows if I proceded all the way thru the install. It is only this one harddrive, with
several weeks work and in Ubuntu, that does not let me in. I have been to several
places and they say change several things...first,  one must be able to get to the software, in order to change it.
     Can anyone help? You may direct mail if you wish.
      After post above, tried changing keyboard...was using Gateway. New keyboard is Microsoft. I get the same error only the numbers at the front 
change to: [28.184578] and [28.185904]. I have no idea what the problem could be unless there is something in Ubuntu that identifies the motherboard/ram
hardware combination and if it changes, refuses to install back to the same harddrive.

  PROBLEM SOLVED!. Out of 4 new ram "sticks" one was the same but different. It had
printed on it the same kind, frequency and all. However, it was not the same as the other three. Changing to one exactly like the other three solved the problem.

---

### Post by Pumalite on 2007-12-02
Do md5sum on your iso, burn new CD at 4x in good quality CD-R media

---

### Post by rtrdom on 2007-12-02
Thanks pumalite but problem is not CD. Same CD installs on other machines, without
errors.
I appreciate the idea though.

---

### Post by Pumalite on 2007-12-02
Post the complete specs and let's see if we can help you.

---

