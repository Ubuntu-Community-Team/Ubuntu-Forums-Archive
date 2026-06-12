---
title: "desktopcouch problems"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Payteer on 2010-03-30
Hello all, I am on Beta 1 totally updated as of a few mins ago.  Anyway, I have had problems with Desktopcouch, it used 100% of my CPU.  I am on a lenovo X61 with enough juice to run this system.  Anyway, as soon as I start Evolution, Desktopcouch starts up and basically maxes my CPU and freezes Evolution.  I have uninstalled Desktopcouch and now everything is hunky dorry, but I would like to know what does Desktopcouch do and why does it use so much CPU?

---

### Post by solitaire on 2010-03-30
i've been having roughly the same problem with desktopcouch (and beam).

Think it's a way to transfer settings between machines (with UbuntuOne) so you have all the same bookmarks and settings on all your machines, if required, or something like that!

I'm thinking of removing it since I can do all that manually if I wanted that to happen.
I just kill couchdb, and associated processes.

---

### Post by timosha on 2010-03-30
Its bug 530605. And it not only affects desktopcouch.

[https://bugs.launchpad.net/ubuntu/+source/libgnome-keyring/+bug/530605](https://bugs.launchpad.net/ubuntu/+source/libgnome-keyring/+bug/530605)

---

### Post by gdonwallace on 2010-03-31
Just wanted to +1 this.

I am having the same issue.  Only started after I tried to connect through Nautilus to a shared windows drive.  gvfsd-smb is also using over 100% of my duel core.

All related to the above mentioned bug.

---

### Post by PendragonUK on 2010-04-01
+1

---

### Post by sebbouckaert on 2010-04-02
I can't make out what program makes the process dektopcouch start, it seems to be running on every session I start here. 
And yes,  it's eating one of my cpu cores constantlly at 100% usage. 
I'm running Lucid beta1 amd64. 
Computer is a HP Pavilion Media Center t3640.nl Desktop PC (Intel(R) Pentium(R) D CPU 3.00GHz dual core  - 2 GB RAM)

---

### Post by Endomancer on 2010-04-02
Desktop has been eating up my cpu aswell.
Within a couple of seconds after booting up my cpu is maxed out which makes everything run real slow


Thank you Solitaire, I just killed desktopcouch as you suggested now everything is running fine and fast

---

### Post by Endomancer on 2010-04-04
I ran update last night and since then, about a minute after completing a boot desktop couch crashes. No more having to kill it

---

### Post by sebbouckaert on 2010-04-05
+1

---

### Post by jamsh on 2010-04-10
I'm regularly getting a crash report for desktopcouch when I start Lucid Lynx.

---

