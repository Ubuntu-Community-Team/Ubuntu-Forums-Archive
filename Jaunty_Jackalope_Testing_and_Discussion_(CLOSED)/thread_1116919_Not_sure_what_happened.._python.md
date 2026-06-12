---
title: "Not sure what happened.. python?"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by snkngshps on 2009-04-05
I did an update a while ago and now I'm having some crazy issues. I think there was an error when python updated.. could that be what's causing this? Here are my issues:

Pidgin, Deluege, Update Manager and Synaptic all won't load. They all open up a completely gray window that I eventually have to force quit. The worst problem of all is when I open terminal, there is no text at all. If I type, no text appears. Luckily Firefox has been working and I'm going to make sure to keep it open so it doesn't stop. Any idea what this could be or how I can fix it?

---

### Post by eyefragment on 2009-04-05
I was having similar issues, and presumably this has to do with the bad python update that came down the pipe: [http://ubuntuforums.org/showthread.php?t=1107854](http://ubuntuforums.org/showthread.php?t=1107854)

The aptitude crash also had a tendency to completely screw up my file system, so that I would need to run fsck on my linux partition every time that I rebooted before I could get into ubuntu (but this seems to be fixed now).  You might run into that problem... you might not.  Maybe the two are unrelated, but that's just a heads up.  I haven't noticed any data loss.

As for fixing the issue, you'll need to get access to a terminal.  control+ alt + f[1 through 6] should do that for you, and then run sudo apt-get update && sudo apt-get dist-upgrade.  If apt-get just segfaults (instead of actually updating itself), rebooting might fix the issue and allow you to update.  In any case, this worked for me (rebooting after getting segfaults from aptitude), but your mileage may vary, and I have no clue _why_ the segfaults would be fixed after a reboot.  I also have no clue why aptitude was butchering my file system so badly.

---

