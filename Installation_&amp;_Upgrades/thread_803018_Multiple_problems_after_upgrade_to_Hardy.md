---
title: "Multiple problems after upgrade to Hardy"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2008-05-21
Running Hardy 8.04 (??) on an i386 PC

After upgrading via the upgrade manager I was unable to log in, getting the message "Greeter application appears to be crashing. Attempting to use a different one."

I followed the advice of many threads in this and the beginner's forum to try to solve the problem.  None of them worked and in the meantime I don't know what I may have screwed up.  Then I downloaded the live CD (advice from the forum) but found I could not do a clean upgrade from that.  Then I tried the alternate CD.  Again there was no option to do an upgrade, only an installation.  So I started the terminal, and as per advice from the forum, I tried "gksu sh /cdrom/cdromupgrade".  The commands were not accepted by the rudimentary shell provided on the CD..

Finally, I tried starting gdmsetup (from the live CD) and found out, quite by accident, that changing the login script from xserver to gnome fixed the problem.  Now I can at least login without using the CD.

Now I am confused about what I actually have on my system.  According to the system monitor I have Hardy 8.04.  But then I started up Firefox and it says I have version 2.0.0.14 installed.  I then went to Synaptic Package Manager and it said I had Firefox 3 installed.

Needless to say, I am now thoroughly confused.  I am not sure I have a complete Hardy installed.  How do I go about cleaning up this mess?

---

