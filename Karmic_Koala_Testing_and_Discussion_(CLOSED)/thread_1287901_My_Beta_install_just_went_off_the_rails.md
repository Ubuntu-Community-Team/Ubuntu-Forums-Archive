---
title: "My Beta install just went off the rails"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tony_clifton on 2009-10-10
Triple boot system with 9.10 beta, 9.04, and XP.   Had been running the beta with no major issues until today.   I ran update manager to see if anything new was available and it found 279 packages.   I hit the apply button and waited.   

It downloaded everything, started installing and configuring everything, then I got bored and was randomly clicking on windows to resize and move them.   As I was doing this the system suddenly apparently logged me off and I couldn't log back in  (wouldn't prompt for a password).

Hit the manual reset button, selected the beta with latest kernel and was treated to a black screen.  Waited for a while and got more black screen.

Manually reset again, chose beta with previous kernel version, got pre-splash screen with various messages in white on black screen, then screen starting flashing like it was having a seizure.

Manually reset again and am now running 9.04.

---

### Post by emarkay on 2009-10-10
Same thing here - I had to use "startx" at the CLI after manually logging in.

[http://ubuntuforums.org/showthread.php?t=1287628](http://ubuntuforums.org/showthread.php?t=1287628)
[http://ubuntuforums.org/showthread.php?t=1287709](http://ubuntuforums.org/showthread.php?t=1287709)

I am presuming it's an update thing of Beta proportions.

---

### Post by kansasnoob on 2009-10-10
I'm not sure, but if the upgrade was interrupted, I'd boot into recovery mode and if it completes you'll be faced with several choices:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

I'd start with dpkg and if you still have no luck I'd next go to netroot and run the commands "apt-get update" and "apt-get upgrade".

Third maybe xfix.

Watch for any errors or messages displayed during those processes.

---

### Post by tony_clifton on 2009-10-10
> **kansasnoob said:**
> I'm not sure, but if the upgrade was interrupted, I'd boot into recovery mode and if it completes you'll be faced with several choices:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

I'd start with dpkg

That's it- dpkg from recovery did the trick.   Thank you very much.

---

