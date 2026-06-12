---
title: "Console output stops during bootup (ubuntu 10.4 lucid)"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by bob_wh on 2011-08-06
After upgrading from Ubuntu 9.10  to 10.4 the console output stops during bootup at various points (during init final scripts processing and when the tty1 auto login).  This is a colinux environment but has nothing do with the problem as it is the same version of colinux kernel that works correctly with 9.10 but exhibits the problem with in version 10.4 Lucid.

when tty1 using mingetty auto logs in the .profile file starts the gnome-session (command:  DISPLAY=$DISPLAY dbus-launch gnome-session &) and when the panel comes up the shutdown button is disabled when it should be enabled.

However, if during the bootup when the console output stops, I immediately toggle to virtual console 2 (tty2) and immediately toggle back to virtual console 1 (tty1) it restores the output to the console and when bootup completes the gnome panel has the shutdown button enabled as it should be.

Some times when the console output stops it looks like a screen clear was issued and other times the lines remains an the screen.  I added --noclear to the line that calls mingetty in /etc/init/tty1.conf but is has no effect.

Can anybody give me some ideas on how to debug this problem or has anyone else experienced the problem and have a solution.

thanks.
regards,
Bob

---

### Post by gordintoronto on 2011-08-06
A version upgrade will install a new kernel. Might this affect your computer?

---

### Post by bob_wh on 2011-08-07
To Gordintoronto:

Any new kernel installed by the update process is not used. I said that this is a colinux environment.  That means that I am running ubuntu in a process on windows and the colinux kernel the kernel that is being used.

I accidently discovered the solution by trying to fix the PLYMOUTH errors that appeared in the boot up log.  I had previously applied the fix to mount the /dev in fstab that had partially fixed some of the plymouth aborting errors. Yesterday, I rename all the plymouth*.conf to Plymouth*.conf.disable to disable plymouth.  This seems to fixed the console output stopping problem and we will see of it prevents the plymouth aborting error when a filesystem check is forced a bootup.
This plymouth component seems to cause numerous problems.

For the time being I am marking this problem as SOLVED.

regards,
Bob

---

