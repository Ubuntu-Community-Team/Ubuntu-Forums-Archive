---
title: "Wine Error while installing .exe files"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by gcmarimon on 2010-05-04
Hy all! Im having trouble with wine, for any installation i get the following errror

> Archive:  /home/mandos/Download/MoorHunt.exe
[/home/mandos/Download/MoorHunt.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/mandos/Download/MoorHunt.exe or
          /home/mandos/Download/MoorHunt.exe.zip, and cannot find /home/mandos/Download/MoorHunt.exe.ZIP, period.

how may i fix this please ?
i also have to install my AutoCad here! does it works fine with wine ?
ive found that p2m, openp2m, morrhunt, etc would work... but all i can get are these kind of error...

also i have uninstalled and reinstalled the wine and it still give the same error.... for any .exe...
 
Using linux ubuntu Licud Lynx!
thanks all
 


best regards

---

### Post by gcmarimon on 2010-05-04
i am still waiting for help since i really need this to work!
anyone can please help me ?
 

thnks

---

### Post by Dragonmuphin on 2010-12-28
Heloooo!!!
The reason that it's not installing correctly through wine is because wine decided that it would read that little .exe file as an archive. Messed up, huh?

What I do whenever I install .exe files is: 

1. cd to whatever directory the .exe file is located in
2. When you're in that directory, Do "wine blahablahblah.exe" (whatevah your .exe is...)

Yah! 

It works then. VOILA!

Thank goodness I have an uber smart older brother to show me the ropes of Linux! PHEW!

---

### Post by Dragonmuphin on 2010-12-28
MEHEHEHE...
I forgot to mention a step before step one...
Go into the terminal to do this...
Right...

I had to add this post so that you know I realize my carelessness...
I am quite tired... bleh

---

