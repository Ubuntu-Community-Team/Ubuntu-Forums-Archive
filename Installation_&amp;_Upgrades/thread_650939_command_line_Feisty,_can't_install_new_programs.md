---
title: "command line Feisty, can't install new programs"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by PARO on 2007-12-27
This is the third time I'm installing Feisty via the same alternate cd (this time to downgrade from Gutsy -I was having way to many display issues and crashes), but for some reason this time I can't install new applications.  What I'm trying to do is install xorg, openbox, and synaptic.  I put in "sudo apt-get install xorg," it says it'll take up 111mb and such, and to put in my feisty i386 disc... which it's already in (and i put in about 20 more times).  I tried reinstalling twice (once w/o a network set-up in case it was updating something that was causing this problem), and checked the disc for errors.  I tried navigating, "cd /cdrom" "ls" and I get nothing, then I tried mounting with "sudo mount -t /dev/cdrom" (I never mounted via command line before, but following the --help didn't help me with the problem)  nothing has seemed to work.  Why can't feisty find my cd without help?  It did all  previous attempts.  And what do I need to do to get it to find my disc and install these programs? Please help.

---

### Post by PmDematagoda on 2007-12-27
Edit your sources.list file with vim or nano and comment the repository for the CD-ROM by typing # in front of it.

Open the sources file using:-
```
sudo vim /etc/apt/sources.list
```
or:-```

sudo nano /etc/apt/sources.list
```

After the editing is done do:-
```
sudo apt-get update
```

That should fix your problem.

---

### Post by PmDematagoda on 2007-12-27
Sorry, double post.

---

### Post by PARO on 2007-12-27
Thanks, that worked perfectly.  I'm back up and running in Feisty now and everythings looking great :)

---

