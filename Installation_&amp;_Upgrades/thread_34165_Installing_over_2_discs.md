---
title: "Installing over 2 discs"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by AndyTuson on 2005-05-13
I am trying to install Ubuntu with the root and swap partitions on one disc and home on another disc.  It appears to work correctly; I can use the partition installation to set the filesystem types and mount points. During the installation process I set up a user.  The problem appears when I try to log on as that user as Gnome refuses to run.  On investigation, /home exists on the second drive, but there is no user directory.  I have tried both the standard and expert installation process.

The discs are standard IDE discs.

Does anyone know what the problem may be? :-?

---

### Post by pointym5 on 2005-05-13
There's probably a fancy Gnome way to do this, but what I'd do is open up a terminal and type "mount".  That'll tell you what partitions are mounted where.

Then you can use the Gnome user management stuff to see where that user's home directory is.  If you can't log in at all, then you can just "sudo view /etc/passwd" from one of the text consoles and see where the home directory is configured for the user in question.

---

### Post by AndyTuson on 2005-05-13
I can only login using a failsafe terminal, when I get the following error:

Your home directory is listed as /home/andy but it does not appear to exist.

Looking at /etc/passwrd shows that the user directory is /home/andy.

The problem is that the installation process creates the /home directory but does not create the user directory.

---

### Post by pointym5 on 2005-05-13
Well, from the "failsafe" terminal try:
```

sudo mkdir /home/andy
sudo chown andy /home/andy

```

I don't know why the install wouldn't create the directory, but that ought to be all you need. The initial login will fault in a .gnome directory for all the desktop config needs.

---

