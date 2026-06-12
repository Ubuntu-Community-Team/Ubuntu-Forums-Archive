---
title: "Can not log in after update - Could not update ICEauthority file"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2011-05-05
I upgraded from 10.10 to 11.04 on my Toshiba 32-bit  laptop without any problems.

Since the upgrade I am starting to have troubles on this machine.  Most others are 64-bit and bar an Evolution issue are fine.

In this case, 24 hours after the upgrade the machine wanted to do an Update.  It would not allow the update until I fixed some broken packages which I did via **Synaptics Package Manager**.  I then** Marked All Upgrade**s and did the update from there.  It was fine until I shut down and tried to log in again.

I got the Blue Screen of Death!!!!!!  I thought only Windows had this!

Anyway, I could not log in.  The auto login was not working so I used **Other** which gave me **Recover**y, entered my UN and PW, and I got the error message:

[HTML]Could not update ICEauthority file[/HTML]
I have searched the forum and some other sites, but none of the ideas can I get to work.  I can start the machine using a 9.10 CD in the trial mode, but can not download the files suggested or delete the ICEauthority file, etc...

Can anyone help, please?

I thought it was all going so well.

---

### Post by Jonners59 on 2011-05-06
[SIZE=4][COLOR=Red]**HELP ME PLEASE, SOMEONE!!!!**[/COLOR][/SIZE]

:sad:

---

### Post by drs305 on 2011-05-06
There have been numerous posts about similar problems after upgrading to Natty. I haven't had this problem, but this is one of the longer threads on the subject in case you haven't seen it:
[http://ubuntuforums.org/showthread.php?t=1746144]("http://ubuntuforums.org/showthread.php?t=1746144")

I wrote a guide on resolving .ICEauthority and .dmrc problems but I really think this is a Natty issue. Hopefully there is something in the above thread which can help you. If not, subscribe to it as I'm sure someone will come up with a solution and post it there.

---

### Post by Jonners59 on 2011-05-07
Thanks drs305
I had been following but nothing worked.  I ended up doing something very wrong and deleted my Home directroy in error and have just rebuilt the machine.  So not fixed and not happy, but it is all working now.

---

