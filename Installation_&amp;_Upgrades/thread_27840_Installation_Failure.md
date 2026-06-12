---
title: "Installation Failure"
date: 2005-04-17
forum: Installation &amp; Upgrades
---

### Post by CArnifexpuer on 2005-04-17
Wow.  I'm incredibly frustrated right now so I'll try to stay away from linux-hating.  Several problems occured that resulted in my re-installation of Windows on my should-have-been-ubuntu partition just to run Windows on my other partition.  I'm sorry that I haven't done a better job of documenting errors, but here goes.

CPU:  Athlon XP 2600 (1.92 gHz)
First, installing the boot...something- another 4-letter acronym that I assume is similar to LILO.  It was the default for allowing me to choose Linux or XP at startup.  No problem, I thought, so I installed it on another partition which then failed.  I then installed LILO on my XP partition which worked.  Then after a restart, it tried to finish installation, where dozens of parts failed to install (this may have been a bad CD...I think).  It recommended trying again, and a few more parts worked, but the majority of these failed again (including the GUI which was a pain).  Installation was over by then, so I restarted.  Instead of allowing me to choose between XP and the incomplete Linux, it went straight to Linux which sent me to the console.  I got as far as logging in and then quit.  It was time to whip out XP then...

So- in short:
1.  I thought installing LILO on my non-Linux partition would allow me to pick between Linux and XP- apparently not.  Could someone explain why not?
2.  Many parts failed to install- what could this have been caused by?

---

### Post by dataw0lf on 2005-04-17
1) -- GRUB, not LILO.  And, yes, it should've.
2) Like you said, it might've been a bad CD. I haven't heard of anything like this.

Questions - How did you partition the install?  How exactly did everything 'fail'?  I assume you mean that a ton of packages failed to install.

---

### Post by CArnifexpuer on 2005-04-17
[QUOTE=dataw0lf]1) -- GRUB, not LILO.  And, yes, it should've.
2) Like you said, it might've been a bad CD. I haven't heard of anything like this.

Questions - How did you partition the install?  How exactly did everything 'fail'?  I assume you mean that a ton of packages failed to install.[/QUOTE]
 GRUB was it.
The drive was already partitioned from when I installed Windows- I had set aside 20 gigs in case I wanted to install Linux (which ended up happening).  You're correct, a lot of packages did not install- some error writing them to the disc.

---

### Post by dataw0lf on 2005-04-18
[QUOTE=CArnifexpuer]GRUB was it.
The drive was already partitioned from when I installed Windows- I had set aside 20 gigs in case I wanted to install Linux (which ended up happening).  You're correct, a lot of packages did not install- some error writing them to the disc.[/QUOTE]

I meant, how did you partition the 20 gigs during the install ?

---

### Post by CArnifexpuer on 2005-04-18
[QUOTE=dataw0lf]I meant, how did you partition the 20 gigs during the install ?[/QUOTE]
 Originally, it was FAT32, but I chose the first one on the list (classic, eh?) since I had no clue as to which one.  Any recommendations?

---

