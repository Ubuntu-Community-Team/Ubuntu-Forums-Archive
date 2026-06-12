---
title: "ReiserFS for /home?"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by beebelo on 2005-08-08
Hello,

I installed Ubuntu as my second distro.  Everything works amazingly well, so congratulations to the development team!  Even my mouse scroll wheel works. :)

Anyway, I was unsuccessful at making the installer mount an existing /home partition; however, I found these instructions for changing the mount point:

[http://www.ubuntuforums.org/showthread.php?t=46866](http://www.ubuntuforums.org/showthread.php?t=46866) 

BUT, my existing /home in Slackware 10.1 is formatted ReiserFS.  Is this going to be a problem for Ubuntu?  (I don't recall being given a file system option during the installation.)  Based on my reasearch so far, I'm getting the impression it's not a good idea to mix file systems within the *same* distro.

Any advice from the experts out there?  

Thank you.

---

### Post by PeP on 2005-08-08
I never had any problem mixing reiserfs and ext3 for three years.

And id on't see why it would be a bad Idea.

---

### Post by beebelo on 2005-08-08
Ok, that's good news.  But let me just make sure I asked my question clearly...  

Are you saying that within a single installation -- Ubuntu, for example -- you've never had a problem with /root = ext3 and /home = reiser, etc. ?

---

### Post by PeP on 2005-08-08
[QUOTE=beebelo]Ok, that's good news.  But let me just make sure I asked my question clearly...  

Are you saying that within a single installation -- Ubuntu, for example -- you've never had a problem with /root = ext3 and /home = reiser, etc. ?[/QUOTE]

/etc/fstab for my laptop,   and running  various linux distros  for one year without disk failure nor any partition related problem:
```

/dev/hda5       /               reiserfs defaults        0       1
/dev/hda7       /home           ext3    defaults        0       2
[...]

```
on my desktop:  running various linux distros for three years without disk failure nor any partition related problem
```

/dev/hda6       /       reiserfs        defaults        0       1
[...]
/dev/hda5       /home   ext3    defaults        0       2
[...]

```

does it answer your question? :-)

---

### Post by beebelo on 2005-08-08
[QUOTE=PeP]
does it answer your question? :-)[/QUOTE]

Yup --  thanks!   :grin:

---

