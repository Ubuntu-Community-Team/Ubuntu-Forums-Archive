---
title: "Xubuntu GUI no longer starts after upgrading from 14.04 to 14.10 on Lenovo T60"
date: 2015-01-05
forum: Installation &amp; Upgrades
---

### Post by erik-brangs on 2015-01-05
I'm using a Lenovo Thinkpad T60. I upgraded to Xubuntu 14.10 from 14.04 yesteryday by using the do-release-upgrade script on the terminal. After the upgrade, I can no longer boot into a graphical environment. The system seems to hang. The last 3 lines are:

Loading tp-smapi kernel module...done.
Setting battery charge thresholds...done.
Starting upowerd...done.

I am still able to use the terminal. If I type startx at the terminal, I get to a graphical environment. It looks like that might be Unity but I'm not sure because I don't see any user interface elements: only the background and desktop symbols are present.

What can I do to troubleshoot this problem (without doing a complete reinstall)?

---

### Post by ajgreeny on 2015-01-05
I do not understand your comment "It looks like that might be Unity but I'm not sure because I don't see  any user interface elements: only the background and desktop symbols are  present."

Have you ever used Ubuntu with unity on that OS or has it always been Xubuntu?

---

### Post by erik-brangs on 2015-01-05
> Have you ever used Ubuntu with unity on that OS or has it always been Xubuntu?
The system is quite old. I installed plain Ubuntu back then. I used the default desktop environment for some years before switching to XFCE by installing the xubuntu-desktop package. When Unity was introduced, I tried it out for a time and then went back to using XFCE.

> I do not understand your comment "It looks like that might be Unity  but I'm not sure because I don't see  any user interface elements: only  the background and desktop symbols are  present."
I said that it looked like it might be Unity because the color scheme looks similar to the one Unity uses. I'm not sure if it's really Unity. It might also be Gnome. I've not really used either of them for some time. 

I'm pretty sure that it's not XFCE because I configured that to use a dark color scheme (i.e. grey fonts, black background).

---

### Post by ajgreeny on 2015-01-05
At the login screen can you make sure you choose Xubuntu as the session and see if that gets you to the Xubuntu desktop.

I don't know what else to suggest as I have never updated my distro version; I always clean install because it is so much quicker as far as I can make out; it takes about 15 mins to install from scratch, then more to update and re-install the packages I need, but it's worth it to me to get a clean OS.

---

### Post by erik-brangs on 2015-01-05
EDIT: I've marked this thread as solved because the problem disappeared after reinstalling GRUB2. There was an additional argument "text" in the kernel command line before "quiet splash" that caused this behaviour. That disappeared after reinstalling GRUB2.  > I don't know what else to suggest as I have never updated my distro version Thanks for the help.  > At the login screen can you make sure you choose Xubuntu as the session and see if that gets you to the Xubuntu desktop. I don't see any login screen. I see the GRUB boot menu, then a black screen and then a bit of display output. Then the system hangs as described above.  > I always clean install because it is so much quicker as far as I can make out I'm in the opposite camp. I only use full installation mediums when I want to switch the operating system and I've never had any problems so far.

---

