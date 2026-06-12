---
title: "[SOLVED] synaptic not opening"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sef on 2008-10-21
I get this message:

> Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '-o' 'Synaptic::closeZvt=true' '--parent-window-id' '69206019' '--set-selections-file' '/var/tmp/tmpMQfQid' as user root.

Unable to copy the user's Xauthorization file.

What should I do to get my system back to normal?

It might be related to this problem [here]("http://ubuntuforums.org/showthread.php?t=954429").

---

### Post by petri on 2008-10-21
Maybe this will help you [http://ubuntuforums.org/showthread.php?t=474127](http://ubuntuforums.org/showthread.php?t=474127)

This problem may occur when using **sudo** with graphical program. Use always **gksu** when sudoing a program with GUI. Good luck!

---

### Post by Sef on 2008-10-21
> Maybe this will help you [http://ubuntuforums.org/showthread.php?t=474127](http://ubuntuforums.org/showthread.php?t=474127)

Thanks that worked.

---

