---
title: "nautilus problem?"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by y10linux on 2009-12-10
First of, all, I want to apologize if I am posting this thread a second time, I wrote this before but the system crashed and I think it did not get really posted.

Today after update mu ubuntu 9.10 using update manager I experienced an unexpected system crash. After restarting I found I cannot open any window graphically.

If I use the command line, data seems to be there (I even managed to get a copy of my work and it seems to be ok), but when i click on a folder the "opening folder" dialog appears but the folder does not really open.

After examining System->administration->log file viewer

I discovered that every time I click a folder, the following message appears:

*xxx-desktop kernel: [ 1912.032629] nautilus[3021]: segfault at 7f9da02a4ff8 ip 00007f9da7da86bd sp 00007f9da02a4ff0 error 6 in libc-2.10.1.so[7f9da7cd7000+166000]*

Can anyone help me?

Thanks

---

### Post by shredder12 on 2009-12-10
A system crash doesn't sound good but are there any other problems or issues since then..
and have you tried reinstalling nautilus..

---

### Post by y10linux on 2009-12-10
well, I tried reinstalling nautilus, linux kernel and a number of other things...

None of them worked and I ended up installing konqueror as an alternative file manager.

After making sure I had not lost any data I started working again but the system was unstable (crashed three times in half an hour). Finally I made the hard decision and reinstalled the whole system. Now I'm back in Ubuntu 9.04 and have almost completed reinstalation. I will go back to 9.10 but will wait for a long while before I do it ;-)

Thanks for the answer anyway, I will mark the thread as solved, hope no one finds himself in the same situation as the solution is quite "painful".

---

