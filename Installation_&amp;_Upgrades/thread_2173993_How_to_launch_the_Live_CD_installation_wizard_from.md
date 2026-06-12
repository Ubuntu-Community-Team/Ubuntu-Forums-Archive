---
title: "How to launch the Live CD installation wizard from the command line of the Live CD"
date: 2013-09-12
forum: Installation &amp; Upgrades
---

### Post by xkcdcode on 2013-09-12
Hi,

I have a custom Ubuntu 12.04 Live CD but when I boot it, it doesn't show a "Install Ubuntu" link on the desktop. So can you tell me the background command that I can use to manually launch the installation wizard from the Live CD's command line?

Thanks.

---

### Post by ajgreeny on 2013-09-12
The installer is called ubiquity, so I imagine the command is something like **ubiquity**, but in all honesty, I haven't really got a clue.

Still a good place to start, I think.

Have a read of [http://manpages.ubuntu.com/manpages/precise/man8/ubiquity.8.html](http://manpages.ubuntu.com/manpages/precise/man8/ubiquity.8.html) for the manual (for precise).

---

### Post by deadflowr on 2013-09-12
It's a shell scipt.
I can't remember the exact command, but you can find it in the /usr/share/applications folder.
Look for the installer icon and right click it, it'll show the command to launch it.

Also, have you tried searching through the dash for it?

---

