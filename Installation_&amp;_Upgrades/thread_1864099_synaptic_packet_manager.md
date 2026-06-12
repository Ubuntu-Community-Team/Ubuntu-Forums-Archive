---
title: "synaptic packet manager"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by craigx on 2011-10-18
Since upgrading to 11.10 I cant load the synaptic packet manager. I am asked for a paaword and then I get a momentary glimpse of the program before it disappears. I have tried downloading a new copy , but the same thing happens. Any ideas would be appreciated.

Craig

---

### Post by haresear on 2011-10-18
I would suggest starting it from the command line in a terminal window. You might get an error message that would be helpful to figure out what is wrong.

> gksudo synaptic

---

### Post by craigx on 2011-10-18
I tried that and below is the result

what():  vector::_M_range_check
 instance of 'std::out_of_range'

no idea what that means !

---

### Post by awam66 on 2011-10-18
I have a friend who also gets this. Tried a clean install then installed synaptic and the result is the same. Tried from terminal and it said no such command synaptic!
Any ideas how to solve please.

---

### Post by haresear on 2011-10-18
> **craigx said:**
> I tried that and below is the result

what():  vector::_M_range_check
 instance of 'std::out_of_range'

no idea what that means !

Hmm.., sounds like an array that is too large or too small. Sorry -- I have no idea what would be causing this or how to fix it. This is just a shot in the dark, but you might try doing an apt-get update to refresh the package lists:

> sudo apt-get update

---

### Post by haresear on 2011-10-18
> **awam66 said:**
> I have a friend who also gets this. Tried a clean install then installed synaptic and the result is the same. Tried from terminal and it said no such command synaptic!
Any ideas how to solve please.

Sounds like synaptic didn't install. How was synaptic installed? The Software Center has a habit of not doing anything when you click on install, and not telling you it failed. If you try to start synaptic from the terminal without 'sudo' and it still says no such command, I would suspect the "universe" repository is not activated. I would do the following:

1. Make sure the "universe" repository is checked/activated.
2. Update the package lists.
3. Install synaptic again.

I'm pretty sure all these steps can be done from the Software Center, but I don't have an Ubuntu desktop right now so I can't tell you exactly how.

Step 1 can also be done from the Update Manager under Settings.. (Also from the app called "Software Sources".)

Steps 2 & 3 can be done from a terminal command line as:

> sudo apt-get update
> sudo apt-get install synaptic

---

### Post by craigx on 2011-10-19
I did that, but no change- the program just apears for about 1 second and then disapears.

---

### Post by haresear on 2011-10-19
I notice that someone else is getting the same error from synaptic -- also after an upgrade:

[http://ubuntuforums.org/showthread.php?t=186425](http://ubuntuforums.org/showthread.php?t=186425)

I would have suggested a purge and reinstall of synaptic, but the other person tried that and it didn't fix the problem. I can't think of anything else to try at the moment. Maybe someone else will come in with another idea.

---

### Post by mdhollis on 2011-10-19
Synaptic isn't installed on 11.10 by default.  Not sure why it wouldn't work after re-installing it.

---

### Post by haresear on 2011-10-19
This apparently is a bug that has been reported. This thread has a solution in post #10:

[http://ubuntuforums.org/showthread.php?t=1854470](http://ubuntuforums.org/showthread.php?t=1854470)

---

### Post by craigx on 2011-10-22
Many thanks - that fixed it.

---

### Post by johanlt on 2011-11-08
Activating and deactivating screen reader did not do it for me. Synaptic keep flashing for a second at launching, and then just die away.

---

