---
title: "problems with home directory"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by pdlethbridge on 2008-07-01
I have had problems with some of the files in the home directory.
Let me explain whats happening. When reinstalling gutsy, I had synaptic problems that were, come to find out, caused by the home directory. By cleaning out all but my personal files from home gave me a successful install of gutsy. I fresh installed hardy using files in the home directory from gutsy and I again had problems such as pages not centered on screen, unable to save nvidia settings using the terminal, not bad stuff, but very irritating. After again cleaning out the home directory of all but personal files, the computer is up and running hardy beautifully. I have added a 2 gig fat 32 partition for my photos and settings beside the home directory
 It seems that the home directory can have its good points and bad. It might be better to limit some of the system files that go into home to desk top settings and browser bookmarks. If you add too much salt to the stew, you spoil the taste. Don't, by default, add so much extra stuff to the home directory.

---

### Post by sdennie on 2008-07-01
By default no system files go into your home directory at all.  It sounds to me like you had some files owned by root in your home directory (which can happen if you run programs as root and they create config files).  I don't think an upgrade from Gutsy to Hardy touches a single file in your home directory but, upgraded apps may want to modify config files after they are started the first time.  If those files were owned by root, it would cause the kinds of problems you are describing.

---

### Post by pdlethbridge on 2008-07-02
I don't mess around with it too much, but if I have problems, I'm not afraid to reinstall the software. Maybe I've been doing that too much:oops:

---

### Post by sdennie on 2008-07-02
> **pdlethbridge said:**
> I don't mess around with it too much, but if I have problems, I'm not afraid to reinstall the software. Maybe I've been doing that too much:oops:

Hehe.  It happens.  One of the strong points of Unix/Linux is the forced distinction between the system level things and user level things.  If you start to blur that distinction by having root owned files in $HOME or having user owned files outside of $HOME or /media, it can cause problems.

If you find yourself regularly breaking your machine by trying things out, you may want to look at VirtualBox or other virtualization software and run a VM of Ubuntu.  That way you can tinker with the virtual machine without causing damage to your real machine.

---

### Post by pdlethbridge on 2008-07-02
I'm retired and a home body (stroke) so I have plenty of time to play with the computer. I'd like to know how I could accidentally screw things up in the home folder. The only time I install stuff is when I'm putting in an update or a game in wine. Now could I be having problems because of wine?

---

### Post by sdennie on 2008-07-02
If you still have the old data around, one thing you could test would be this:

```

cd /place/where/backup/home/is
find . ! -user $USER

```

That may take a while to run but, it will tell you all the files in your backup home directory that aren't owned by you.

---

### Post by pdlethbridge on 2008-07-02
tried it and got an Immediate answer. nadda

---

