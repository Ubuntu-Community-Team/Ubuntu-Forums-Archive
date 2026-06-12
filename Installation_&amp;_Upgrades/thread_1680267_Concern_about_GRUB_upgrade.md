---
title: "Concern about GRUB upgrade"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by Vimmander on 2011-02-02
I have a concern about something that I did on accident while Update Manager was running.  I was at the terminal, getting ready to hit "enter" to view a man page about javawc, and a "debconf" window popped up, asking me if I wanted to "Keep the locally installed version of GRUB".  There were other options, one of which I assume was to replace the current version of GRUB with a new one.  Unfortunately, the moment that the window took over the role of "active window" (the one in front of all others), I hit the enter key, telling debconf that I wanted to "Keep the locally installed version of GRUB" or whatever that option is.

My questions are:  1.  Is this selection of "Keep" going to screw up my machine in any way when I reboot?  If so, 2.  How do I redo that process of selection?  3.  Is there a plan to stop programs like Update Manager from taking over the role of the active window when other programs have that role?

---

### Post by Benchrest on 2011-02-02
I have the same question in a little different view. I am sitting here with the question on the screen. Seven possible replies.  I don't know which is the correct one and apparently Grub doesn't know either. If I were a guessing person I would say the default is probably right, but which one do I want?  How am I to determine that? Thanks

---

### Post by Benchrest on 2011-02-02
I found a user only gets this message if you have made modifications to grub.  I saved a copy of etc/default/grub.  Also took the option to show the differences between the new one and the old one and saved that.  Then took the option to use the developers version.  Hopefully I have enough information to make the corrections when I get this figured out.

As to Grog, I think you saved your changes by the option you took but lost any thing new that might have been added to the grub menu by the fixes.  But I don't really know.  Hopefully someone might shed some light on this.

---

### Post by Benchrest on 2011-02-02
It appears to me that when grub is updated it saves an old copy.  So you can compare the old to the new to see if you lost some parameter.  The new copy is /etc/default/grub   The old is /etc/default/grub.ucf-old  
I am not expert so use this info cautiously.

---

