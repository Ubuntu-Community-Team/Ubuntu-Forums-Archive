---
title: "Ubuntu (10.04) freezes after 'Select Keyboard'"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by TC.Seven on 2010-09-23
I am currently attempting to install Ubuntu 10.04 on my Inspiron  1525. For redundancy's sake, I have attempted to install both AMD64 and  i386 from both CD and Flash Drive using InfraRecorder and Universal USB  Installer respectively with no change in the freezing issue.


 I do have an empty partition set up in EXT3 format, though I tried  installing Ubuntu on FAT32 and unpartitioned sections as well, all of  which exceeded minimum size requirements.


 Again, the issue occurs just after I select my keyboard type during  the install process. (No pun intended) I hit 'next' and the cursor makes  to load, but idles for longer than six hours with no notable change in  state.


Apologies if this problem has already been explored elsewhere on the board. My search didn't find a solution.

---

### Post by mörgæs on 2010-09-24
Hi, welcome to the forum.

Can you install 9.10?
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by TC.Seven on 2010-09-24
Ubuntu 9.4 architecture i386 will not install from flash drive, claiming to be unable to write on unknown location (104.1)

Ubuntu 9.4 architecture i386 will install to 44% before claiming the CD is not clean and file transfer cannot continue. I have cleaned the disk and attempted the process twice. Both times the failure occurs at 44% (I don't have another CD to try it on, so unfortunately I cannot verify if the problem is in the CD.)

Ubuntu 9.4 architecture AMD64 will not install from flash drive, claiming to be unable to write on unknown location (101.1)

Ubuntu 9.4 architecture AMD64 will not install from CD, claiming to be unable to write on unknown location (----)

---

### Post by C.S.Cameron on 2010-09-24
Have you checked the MD5SUM of the iso to make sure the download was good?

---

### Post by TC.Seven on 2010-09-26
Yes.

---

### Post by Ben_neB on 2010-09-26
I would put in a live CD of 9.10, and use Disk Utility to check your hard drive, you might have some bad sectors.

---

### Post by mörgæs on 2010-09-26
If you want to use the entire disk for Ubuntu, you could also delete everything using Killdisk and watch for messages during the process. This will give a good indication of the health of the hard drive.

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by Claude Rebeck on 2010-09-26
Ubuntu 10.04 (Dvd from iubuntu User magazine) installs OK but after 2 minutes
the mouse arrow does not respond, ubuntu is locked up.
Same problem when attempting to use the "from DVD verstin"

  Claude Rebeck    PS new to the forum

---

### Post by TC.Seven on 2010-09-26
One error was found. It is good to know where the problem resides. I'll acquire new CDs and try both versions again.

---

### Post by mörgæs on 2010-09-27
If that means ordering them by mail, this could take some time. Better to burn them yourself from the link above.

---

### Post by TC.Seven on 2010-09-27
I am burning them myself.

---

### Post by TC.Seven on 2010-09-28
Using a new CD, 10.04 AMD64 has properly installed. Thanks to everyone who helped me pin down the problem!

---

### Post by mörgæs on 2010-09-28
You are welcome. Please mark the thread 'solved'.

---

