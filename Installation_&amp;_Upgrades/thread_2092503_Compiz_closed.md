---
title: "Compiz closed"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by greenspud on 2012-12-08
I have installed Ubuntu 12.10 on a old Pentium 4. ( dimensions 3000)I get a report Compiz closed and I have no desk top. I have a Nivida graphic card coming in the mail. I have had graphic problems with this computer before. 
 Can I install mother board driver updates before I have a OS?
 Compiz closing is a graphic problem?
 Thank you 
 Tony

---

### Post by Ubumang on 2012-12-28
I'm having the *exact *same issue.

I'm a complete newb when it comes to linux/ubuntu.  On my first attempt, I installed Ubunto to a Dell Dimension 3000 desktop.  I see the login screen, but after I log in I see a blank desktop.  If I wait long enough, I see an error that "compiz" crashed.

The video card is an on board Intel.

Would love to know what the issue is and how to resolve it...

---

### Post by WierdKid on 2012-12-28
Some more information on all the hardward in the computers might help. But I had a similar issue and [http://ubuntuforums.org/showthread.php?t=1981213]("http://ubuntuforums.org/showthread.php?t=1981213") got me through it. Not sure if the situation is exactly the same but it is a place to start.

---

### Post by Ubumang on 2012-12-28
> **WierdKid said:**
> Some more information on all the hardward in the computers might help. But I had a similar issue and [http://ubuntuforums.org/showthread.php?t=1981213](http://ubuntuforums.org/showthread.php?t=1981213) got me through it. Not sure if the situation is exactly the same but it is a place to start.

Thanks WierdKid.  I tried running the command:  unity --reset

Here is the result...

compiz (core) - info: starting plugin: ccp
compizconfig - info: backend : gsettings
compizconfig - info: integration : true
compizconfig - info profile : Unity
compiz (core) - info: loading plugin: composite
compiz (core) - info: starting plugin: composite
compiz (core) - info: loading plugin: opengl
x error of failed request: badalloc (insufficient resources for operation)
   major opcode of failed request: 153 (GLX)
   minor opcode of failed request: 3 (X_GLXCreateContext)
   Serial number of failed request: 32
   Current serial number in output stream: 33
compiz (core) - info: unity is not supported by your hardware.  Enabling software rendering instead (slow).
x error of failed request: BdAlloc (insufficient resources for operation)
   major opcode of failed request: 153 (GLX)
   minor opcode of failed request: 3 (X_GLXCreateContext)
   Serial number of failed request: 32
   Current serial number in output stream: 33
compiz (core) - info: unity is not supported by your hardware.  Enabling software rendering instead (slow).
compiz (core) info: starting pluging: opengl
segmentation fault (core dumped)

---

### Post by WierdKid on 2012-12-28
Did you just do the unity --reset or did you do all the rest. I had the same output just running unity --reset.

---

