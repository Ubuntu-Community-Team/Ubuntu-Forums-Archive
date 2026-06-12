---
title: "screen shell goes into an infinite loop after upgrading to 10.10"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by dave_kirby on 2010-10-20
I have just upgraded from 10.4 to 10.10 (x64), and now when I run gnu screen the new shell session goes into an infinite loop displaying:
> Linux dave-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

0 packages can be updated.
0 updates are security updates.repeatedly until I hit CTRL-C and break out of screen.

I tried tmux and that did the same thing, so it is a problem with the shell initialisation rather than with the screen program.   However I can start bash, zsh or sh directly in a terminal with no problem.

Any help on tracking down this problem would be appreciated.

---

### Post by dave_kirby on 2010-10-21
I have found the problem.  For some reason my default $SHELL variable is set to /usr/bin/shell.

/usr/bin/shell is a script that displays the MOTD then execs the current shell that is stored in $SHELL... 

which is of course /usr/bin/shell...

The simple fix is to change the default shell in the user settings.  However /usr/bin/shell should check that it is not calling itself recursively - I have done that on my local version, just in case.

---

