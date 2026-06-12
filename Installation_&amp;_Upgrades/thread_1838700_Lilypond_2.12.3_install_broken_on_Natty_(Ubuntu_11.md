---
title: "Lilypond 2.12.3 install broken on Natty (Ubuntu 11)"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by maarvarq on 2011-09-04
As advised here [http://www.ubuntugeek.com/lilypond-a-program-for-typesetting-sheet-music.html](http://www.ubuntugeek.com/lilypond-a-program-for-typesetting-sheet-music.html)
I tried to use apt-get to install Lilypond, but it wouldn't run
[FONT=Courier New]$ lilypond
GNU LilyPond 2.12.3
warning: not relocating, no 2.12.3/ or current/ found under /home/mark/share/lilypond/
ERROR: In procedure primitive-load-path:
ERROR: Unable to find file “lily.scm” in load path[/FONT]
because the installation had been to /usr/share/lilypond/ instead, and adding this directory to the FILE variable didn't help

I was advised by someone else to manually install it instead, which was quite simple
[http://lilypond.org/unix.html](http://lilypond.org/unix.html)
essentially

[LIST=1]
[*]download the file
[*]open a terminal
[*]change the directory to the one the file was downloaded to
[*]sh <name-of-downloaded-file>
[/LIST]
and allowed me to install a later version 2.14.2  

I hope this is of use to someone else too.

---

### Post by Dominicus on 2011-10-10
Yep...this worked well.  Thx!

---

