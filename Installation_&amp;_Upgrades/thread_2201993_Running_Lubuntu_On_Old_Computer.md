---
title: "Running Lubuntu On Old Computer"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by Rutherford_Hayes on 2014-01-26
I have successfully deleted the previous OS and burned Lubuntu 13.10 on a CD, before installation I checked the CD for errors. I have apparently successfully installed Lubuntu 13.10 twice.

When starting up the computer I'm given two choices of OS's: Ubuntu or Ubuntu 13.10. Ubuntu leads to a frozen screen with the bottom 1/4 black and the top 3/4 light blue with four small, distorted Lubuntu logos stretched towards the upper right, below each logo are four dots. Ubuntu 13.10 leads to a frozen solid black screen with a green bar across the top.

How can I run this successfully?

---

### Post by Bashing-om on 2014-01-26
Rutherford_Hayes; Hi !

Graphics driver issue ?
If you are running Nvidia or ATI graphics, Try this:

At that grub menu screen, "normal" kernel highlighted, press the 'e' key for edit mode;
boot parameters screen -> arrow down and across to the terms "quiet splash" and insert also the term "nomodeset" - with out the quotes-
key combo ctl+x to continue the boot process,

Do you now boot to a GUI ? login and 
Additional drivers -> install the recommended driver.

Other makers cards have similar boot parameters to disable the kernel's mode setting permit the installation of alternate drivers.


[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by mörgæs on 2014-01-27
R_H, when jumping to a new thread it would be a friendly gesture to post a closing remark in the old one so people there are not wasting their time.

People answering in the new thread would appreciate if you brought relevant information along from the old one, for example the hardware in question.

---

