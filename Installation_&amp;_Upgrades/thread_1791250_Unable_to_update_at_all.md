---
title: "Unable to update at all"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by el_bandido on 2011-06-26
Hello,

I'm running ubuntu 11.04 from minimal with unity 2D on my eeepc T91mt.

Worked fine for ages, ran an update and now I get the following error message when using the updater:

"**Could not initialise the package information**

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"

I get a similar message when running sudo apt-get update in terminal.

Help!

---

### Post by dabl on 2011-06-26
Possibly there is a temporary problem with the repo.

You can open a terminal and issue:

```
sudo dpkg --configure -a
```

and see if it gives you any error.  If there is no error, then just wait for a few hours and try the update again, using the terminal and apt-get (so you can see error output if there is any).

---

### Post by el_bandido on 2011-06-26
> **dabl said:**
> Possibly there is a temporary problem with the repo.

You can open a terminal and issue:

```
sudo dpkg --configure -a
```

and see if it gives you any error.  If there is no error, then just wait for a few hours and try the update again, using the terminal and apt-get (so you can see error output if there is any).

No error. Been having the same problem for ~10 days. This error occurs when I try and run the update manager, or a general apt-get update, not update a specific package. Thanks for the input though.

---

### Post by mörgæs on 2011-06-26
[http://ubuntuforums.org/showthread.php?t=1791038](http://ubuntuforums.org/showthread.php?t=1791038)

---

### Post by el_bandido on 2011-06-26
> **mörgæs said:**
> [http://ubuntuforums.org/showthread.php?t=1791038](http://ubuntuforums.org/showthread.php?t=1791038)

Solved. Thanks. 

Now to solve the lagging boot times and irritating stability issues that occur every time I update 11.04.

---

