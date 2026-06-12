---
title: "How to completely re-configure Ubuntu?"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by hooz on 2011-04-28
I don't know how, but i've managed to delete my new sidebar and the topbar you get when you upgrade to 11.04. I did with an accident on compiz. Someone that can help me? 
PS: i don't know how to open Terminal anymore....

---

### Post by KegHead on 2011-04-28
Hi!

Did you try  right clicking with your mouse?

Also on boot up, you have options.

KegHead

---

### Post by vanadium on 2011-04-28
[edit]On second thought, the method below may not work: settings you make in compiz are user settings, and thus are stored in your home directory in hidden folders. There is a .compiz folder, but I am not sure that is pertinent. Anyway, the method below is in principle harmless to your system, drastic as it sounds though. You could try, if it does not work, then you may need to reset your user profile.[/edit]

What helps in a case where you screw up system configuration is to boot up in a recovery terminal with networking, then purge the offending packages, then reinstall ubuntu-desktop. (I talk from experience ;) )

* Restart the computer, holding the left shift key pressed
* Select an entry with "Recovery mode"
* Choose "root prompt with networking"

You are dropped to a prompt with root privileges: no sudo needed and it is very easy to nuke your system further ;)

```

apt-get purge compiz
apt-get install ubuntu-desktop

```

First one purges compiz (and all its dependencies and related packages), second one reinstalls all packages needed for a well functioning desktop.

```

reboot now

```
to effectuate a clean restart.

---

