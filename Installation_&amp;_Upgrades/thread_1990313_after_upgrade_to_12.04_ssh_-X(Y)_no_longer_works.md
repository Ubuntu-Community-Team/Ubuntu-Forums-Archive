---
title: "after upgrade to 12.04 ssh -X(Y) no longer works"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by Wolf-Ekkehard on 2012-05-29
The upgrade to 12.04 (64 bit, KDE 4.8.2) went great for me - not a single problem with any application (and I run lots), except one: ssh.

For years, I have been logging into my lab machine (lots of HW attached) via ssh -Y and I could run all X-applications wihout any problems over Ethernet.  Not anymore :mad:.  Every time I try to start a Qt-based (KDE) application remotely it crashes with 

*** glibc detected *** konsole: malloc(): memory corruption: 0x08d94480 ***

on the remote side (the ssh-login itself shows no signs of errors).  Happens at least for konsole (above example), dolphin, kdevelop (the ones I use the most in this mode), and my own Qt-based application.  The only application I use often that still works remotely is gschem (from what I can tell not a Qt-based app).  As expected, results for ssh -X and ssh -Y are identical.

BTW, the remote lab machine still runs 11.10 (32 bit, KDE 4.7.4), and I can do a ssh -Y from that machine to the one running 12.04 with full X-functionality, only from 12.04 to 11.10 does not work.

Did anybody else notice this problem?  Found a sloution??

---

### Post by ve4cib on 2012-07-12
A bit of threadomancy, but I'm running into this exact issue with Xubuntu 12.04.  Any Qt applications I try running over SSH (e.g. VLC, QtCreator), are segfaulting.

Did you ever find a solution to this problem?

This thread was the first thing that came up when I googled "qt crash when running program over ssh," so hopefully we can figure something out.

---

### Post by Wolf-Ekkehard on 2012-07-12
I know, the thread is kind a old and stale.  Back about 5 or 6 years ago all questions to this forum were answered within a day or two.  Now all we get is "I have the same problem" replys.  Maybe my questions have become harder- maybe there's too much traffic now on the forum for the experts to read and respond to it all - maybe (most likely) both.

Well - sorry ve4cib - I did not find, let alone fix, root cause and therefore did not mark the thread solved.  But I somehow worked around the most urgent aspects of the problem for my environment.  I painfully upgraded my lab machine to 12.04.  Now ssh works in both directions with full X functionality over the Ethernet - no more memory corruption.  It also works between an old laptop that is running cygwin under XP and both of these machines (as it did before I upgraded to 12.04).  So I just filed that problem mentally under an 11.10/12.04 incompatibility issue concerning Qt applications.

The only area where I am still uneasy is my own Qt application, since I now know that it has an interoperability issue between different versions of *Ubuntu, and I have no idea how to address it.  Therefore I am still interested in a possible fix.  But since it looks like it affects all Qt applications, it may be beyond of what I could tackle without diving deep into Qt code, and that's too daunting a task for me.  My experience with the Qt forum (for other issues) hasn't been great, but admittedly I am not a paying customer...

Is your X-server also running under 11.10, or is it a more wide-spread problem?

---

### Post by ve4cib on 2012-07-13
My SSH server was running Xubuntu 11.10, with a 12.04 client.  Any Qt applications segfaulted exactly the way you described, but it was intermittent.  Sometimes they'd work, but most of the time they didn't.

Today I just gave up and reformatted the server and upgraded to 12.04.  The problem seems to have gone away for now.  I'll keep an eye on it, but hopefully it's fixed now.

---

