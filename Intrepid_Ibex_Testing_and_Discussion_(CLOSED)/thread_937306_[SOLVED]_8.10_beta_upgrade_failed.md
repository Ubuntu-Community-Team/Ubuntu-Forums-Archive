---
title: "[SOLVED] 8.10 beta upgrade failed"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by moschops on 2008-10-03
I started doing an upgrade to 8.10 beta this morning but the downloads were taking too long so I canceled it and bit-torrented the alternate CD ROM iso.

Now when I try to do the cdromupgrade form the disk it just dies after asking me if I want to download updates from the net (I hit no) and if I still want to continue because it doesn't have good drivers for my nvidia card (I said yes).  Since there is no error message and I see no log entry I'm not sure what to do?

If I run update-manager -d from the commandline again it tells me it first tells me I need to do a partial upgrade, and then when I click yes it says "could not calculate upgrade" and that it is most likely a transient problem and I should try again.

I think somehow I screwed things up by interrupting (with cancel button) the original upgrade - is there a way to remove all traces of the previous upgrade attempt and start over?

---

### Post by moschops on 2008-10-03
Okay I fixed this myself but figured I'd leave the post for anyone that has the same problem.

To fix go to System->Software Sources and under "Third-Party Software" tab uncheck all the Intrepid repositories.

Then cd to / and run /media/cdromupgrade as root or via sudo

The upgrade may offer to rewrite your software sources list but after that it ran perfectly from the cdrom.  I suspect I could have restarted a regular network based update-manger -d upgrade too.

---

### Post by MadeOfEyelashes on 2008-10-12
> **moschops said:**
> Okay I fixed this myself but figured I'd leave the post for anyone that has the same problem.

To fix go to System->Software Sources and under "Third-Party Software" tab uncheck all the Intrepid repositories.

Then cd to / and run /media/cdromupgrade as root or via sudo

The upgrade may offer to rewrite your software sources list but after that it ran perfectly from the cdrom.  I suspect I could have restarted a regular network based update-manger -d upgrade too.

How could I do this over the command line?

---

