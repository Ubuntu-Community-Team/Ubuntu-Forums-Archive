---
title: "After 8.04 -&gt; 10.04 upgrade, X totally unresponsive"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by mmaxx555 on 2010-07-23
Hello there, 

I just upgraded the machine of a friend from 8.04 to 10.04, straight through. (Since they are both LTS).

Installation went OK, everything as expected. 
But after login into 10.04 the whole graphical side is pretty much unresponsive. 

Now there are a few things that seem extremely odd: 

1) The desktop loads ok, the CPU has picks of being maxed out, but not continuously.
2) The menus and graphics work ok and are responsive, yet you can't open any applications because the CPU shoots up and the machine sort of freezes.
3) ALT-F2 works, but I can't input anything, as if the keyboard would be disconnected.
4) But the keyboard allows me to switch to another terminal and everything works fine there (tty1) and the system is as responsive as it should be. 

The laptop is fairly old, but it was working pretty well with Hardy Heron.

It's a p4 2.0 GHz with 512MB. Ati graphics.

I have googled around and I haven't been able to find anything remotely similar. If anyone has any suggestions or can point me to some bug report, or other thread I would appreciate it.

Cheers
M

---

### Post by ajgreeny on 2010-07-23
What ati graphics?  They are not good, particularly older cards, in 10.04, and you may need a custom xorg.conf to get the best from it.

How does the live CD run, or did you not try that, having done the on-line update?

---

### Post by mmaxx555 on 2010-07-23
Hey ajgreeny,

No I didn't try to the live CD as I never actually downloaded it. 

I forced the distro update by gksudo Update-Manager --proposed.

However graphics were very responsive and all menus and windows worked fine. 

This machine is for a blind user, so what I did is use the Vinux script to configure all the orca settings, etc from the terminal and all problems got solved... 

I truly have no idea what was causing the problems but the installation of the other packages plus the updates fixed it. 

I will be marking it as solve, although it is NOT technically a solution... 

Cheers for the reply though!
M

---

