---
title: "Emacs only starts with -nw after upgrade to 13.04"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by jazzgossen on 2013-04-25
After today's upgrade from Kubuntu 12.10 to 13.04, Emacs only starts with "emacs -nw". It's the same for both emacs23 and emacs24. I have tried running with --live-safe-mode and --debug-init, but there's simply no output, and nothing happens. I also tried to purge and reinstall emacs, but no change. What can I do?

---

### Post by emilvolcheck on 2013-04-26
I just upgraded and I have the same problem.  emacs -nw works but ordinary emacs does not.

PaulW2U reports this on kubuntuforums:

[http://www.kubuntuforums.net/showthread.php?62033-emacs23-and-emacs24-both-fail-to-run-most-of-the-time&highlight=emacs](http://www.kubuntuforums.net/showthread.php?62033-emacs23-and-emacs24-both-fail-to-run-most-of-the-time&highlight=emacs)

Thanks for any help!

--Emil

---

### Post by suem on 2013-05-05
Hi,

Had the same problem. This is how i fixed it (btw. I am not sure which parts actually fixed the problem):

- change the GTK theme settings the following way: [http://imgur .com/IsWrCn8]("http://imgur.com/IsWrCn8")
- delete all ~/.gtk* files and folders from your home dir.

Hope it works,
Cheers Suem

---

### Post by SabreWolfy on 2013-05-20
^ I don't have those themes available. Removing ~/.gtk* files did not help.

---

### Post by jazzgossen on 2013-05-22
Did you try running emacs23-lucid, or emacs24-lucid, instead? That works for me (although with a slightly uglier interface).

---

### Post by SabreWolfy on 2013-05-22
> **jazzgossen said:**
> Did you try running emacs23-lucid, or emacs24-lucid, instead? That works for me (although with a slightly uglier interface).

Not yet. I didn't like the idea of the uglier interface, so I've been using the terminal version. I thought Lucid was XEmacs? I wonder why such a critical bug has not yet been fixed for 13.04.

---

### Post by jazzgossen on 2013-05-30
> **SabreWolfy said:**
> I thought Lucid was XEmacs?

Good point. But actually, when I do "About Emacs" from my emacs (/usr/bin/emacs23-lucid) I get the following message

```
This is GNU Emacs, one component of the GNU/Linux operating system.

GNU Emacs 23.4.1 (i686-pc-linux-gnu, X toolkit, Xaw3d scroll bars)
 of 2012-09-22 on akateko, modified by Debian
Copyright (C) 2012 Free Software Foundation, Inc.
```

So it's still GNU Emacs, but with another interface.

---

### Post by PaulW2U on 2013-06-05
This bug was fixed in the last couple of hours. Both emacs23 and emacs24 are working here on Kubuntu 13.04. :D

See - [https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/1142213](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/1142213).

Depending on what repositories you have enabled the fixed packages may not be available for another seven days.

---

### Post by jazzgossen on 2013-06-06
Great! I upgraded gtk2-engines-oxygen, installed emacs23 (and automatically removed emacs23-lucid), and now emacs starts as it should.

---

