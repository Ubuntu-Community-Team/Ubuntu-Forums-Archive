---
title: "Clipit 1.4.2 no longer launching on Ubuntu 12.04"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by markwagner on 2012-09-27
I need help with Clipit 1.4.2 on Ubuntu 12.04. Can anyone help?

I just switched to Ubuntu from OS X and one thing that convinced me was seeing Clipit as a replacement for FlyCut.

I originally installed Clipit using Ubuntu Software Center, got it configured the way I liked (this software is awesome), and it worked great (for about a day). Then, the battery died while I was working. This might’ve been a coincidence, but when I plugged in and rebooted Clipit wouldn’t launch anymore. I tried a bunch of standard troubleshooting – restarting, reinstalling, etc. And eventually tried installing using the instructions here. However, regardless of the install method I’m getting errors like this:

(clipit:6767): GLib-ERROR **: /build/buildd/glib2.0-2.32.3/./glib/gmem.c:165: failed to allocate 18446744072034725823 bytes
Trace/breakpoint trap (core dumped)

A clipboard buffer is critical to my workflow. I don’t have the skills to fix it myself but I’m happy to offer compensation for anyone who can... let me know if you take donations or if there is anything else I can do to help. :)

---

### Post by markwagner on 2012-09-28
I noted that clipit still worked for other users on the same machine. Then I located the clipit files in ~/.local/share/

This worked:

cd ~/.local/share/
rm -r -I clipit/

Also, Clipit's creator, Cristian, also replied to my comment on his site this way:

my guess would be that, since your machine didn’t shut down properly, the clipit history file didn’t get saved properly and thus got corrupted. When you loaded it back up, clipit tried to load that corrupted file and errored out. Should this happen again, my tip would be to just delete the history file (which should be ~/.local/share/clipit/history) and re-launch clipit.

---

