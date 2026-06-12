---
title: "Tried to upgrade to Rhythmbox 0.12.8, but not working!!"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by Kangaroo_Style on 2010-04-25
I'm trying to upgrade from Rhythmbox 12.5 to Rhythmbox 12.8. I did everything, I'm supposed to...I think. But when open Rhythmbox and click on "help -> about" I still get 12.5 as the version number. 

Here is what I've done:

1. Downloaded tar ball from rhythmbox site
2. Unzipped it to desktop
3. Ran apt-get update
4. Ran apt-get upgrade
5. Ran apt-get upgrade rhythmbox
6. CD to Rhythmbox 12.8 folder, and ./configure
7. Ran make
8. Ran sudo su
9. Ran make install
10. Checked version and still at 12.8.

Where did I go wrong?

---

### Post by oldos2er on 2010-04-25
You can leave out the "apt-get" commands, because apt only looks in the repositories.

Did configure and make complete without errors?

---

### Post by Kangaroo_Style on 2010-04-25
> **oldos2er said:**
> You can leave out the "apt-get" commands, because apt only looks in the repositories.

Did configure and make complete without errors?


So I can just type "upgrade" in terminal and it will do all that for me? (I'm still a linux noob, and just getting used to working in the command line)

There were no errors in the configure, and no errors with make.

The only thing I can think of is that I didn't uninstall Rhythmbox 12.5 prior to running configure and make?

---

### Post by oldos2er on 2010-04-25
No, apt-get upgrade only gets you what's in the repositories.

If you run **/usr/local/bin/rhythmbox** do you get the correct version?

---

### Post by Kangaroo_Style on 2010-04-25
> **oldos2er said:**
> No, apt-get upgrade only gets you what's in the repositories.

If you run **/usr/local/bin/rhythmbox** do you get the correct version?


I just tried it, and it still opened up 12.5.

---

### Post by oldos2er on 2010-04-26
Which version of Ubuntu are you running? Can you run **sudo make install** from within the source code directory, and post the output here?

---

### Post by Kangaroo_Style on 2010-04-26
> **oldos2er said:**
> Which version of Ubuntu are you running? Can you run **sudo make install** from within the source code directory, and post the output here?


9.10. I restarted my computer and ran Cairo Dock. For some reason it updated to 12.8!! Maybe just needed a reboot!

---

