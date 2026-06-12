---
title: "Should you alias, add to path, or symbolic link?"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Marupio on 2009-12-02
I just installed a program in /usr/local/bin (Eclipse C++ IDE) and now I have to link to it.  Should I:
alias eclipse=/usr/local/bin/eclipse/eclipse

or
Add /usr/local/bin/eclipse to the PATH

or
rename the eclipse directory and add a symbolic link in /usr/local/bin?

Which is best?  Any other suggestions?

---

### Post by lloyd_b on 2009-12-02
> **Marupio said:**
> I just installed a program in /usr/local/bin (Eclipse C++ IDE) and now I have to link to it.  Should I:
alias eclipse=/usr/local/bin/eclipse/eclipse

or
Add /usr/local/bin/eclipse to the PATH

or
rename the eclipse directory and add a symbolic link in /usr/local/bin?

Which is best?  Any other suggestions?

Personally, I'd go with the alias, since that has the least possible affect on your system.  

I would avoid the move-and-symlink solution, as the program may be looking for that particular directory (Ideally, it shouldn't, but if they aren't smart enough to put the binary in a default location all bets are off).

Adding it to the PATH could have side effects - if there's a executable in that directory with the same name as a standard executable, then which one will run?  It depends on where in the PATH you add that directory.

Lloyd B,

---

### Post by Marupio on 2009-12-03
Done.  Thanks!

---

