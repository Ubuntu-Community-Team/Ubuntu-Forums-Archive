---
title: "[SOLVED] Uninstalled firefox and associated files from synaptic package manager now n"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by cmooreusa on 2007-08-10
Uninstalled firefox and associated files from synaptic package manager now no desktop...

I was trying to fix Firefox after installing a bunch of add-ons and then Firefox did not wanting to boot at all so I decided the best thing to do would be to uninstall Firefox and reinstall it.  This did not work.  I moved to the Synaptic Package Manager to see if I could uninstall all associated files that might need to be uninstalled with it.  There were several and I decided upon something like 5 or 6 that seemed to be a good idea at the time.  I was planing on reinstalling it in hopes that if I made a complete as possible uninstall of Firefox then I might be able to install it completely and get it fixed.

At this point I rebooted my system and I logged in but there was no "nautilus" or "desktop" whatsoever.  and trying to boot into GNOME failsafe mode didn't work but the terminal boot mode does.  I am new with Ubuntu and do not know my way around.  I would love any suggestions possible.  I have also tried installing Ubuntu CD 7.04 to run from it but it doesn't look like my system wants to use it after reading it.  It appears to be loading from the computer though it is obviously reading from the cd.

Anything at all is welcome!

Thank you in advance!

Charles

---

### Post by merlinus on 2007-08-10
You might try this:

```

sudo aptitude update && sudo aptitude install gnome-desktop

```

-merlin

---

### Post by cmooreusa on 2007-08-10
I'm about ready to cry... Your solution worked perfectly and even then some!  I have my Firefox back with all the attachments and it's working flawlessly!  Thank You so much!  The only thing that was off about your council was that the correct name for the install is/was "gnome-desktop-environment"

Thank you again!

Charles

PS- I have a folder group called Debian now in my Applications group ... some things that I tried to install in the past that never showed up before and now it has a loadable group for them... maybe they were there all along just didn't have their own group.

:KS

---

### Post by aysiu on 2007-08-10
If you want the default Ubuntu packages, the correct package is *ubuntu-desktop*.

---

### Post by cmooreusa on 2007-08-14
That's probably why it gave me some extra stuff :)

Thanks again!

Charles

---

