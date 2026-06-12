---
title: "Problem removing python-gtk2-dev"
date: 2015-08-10
forum: Installation &amp; Upgrades
---

### Post by liviu1 on 2015-08-10
Hi everyone,
I am running Ubuntu 14..04 and I ran into this problem: trying to remove (from Synaptic) package 'python-gtk2-dev' I get this error message:

Removing python-gtk2-dev (2.24.0-3ubuntu3) ...
dpkg: error processing package python-gtk2-dev (--purge):
 subprocess installed pre-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-gtk2-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
___
This doesn't allow me to do : 'apt-get autoremove' either

---

### Post by dino99 on 2015-08-10
with your file manager, try to search about that 'python-gtk2-dev' file, and delete the line ending with 'postinst' (if it does not resolve that issue, delete the other related entries too)
you may need to logout/in

---

### Post by liviu1 on 2015-08-10
Tried to find with 
'sudo find  / -type f -name python-gtk2-dev'
Nothing was returned. Any other suggestions, please ?

---

### Post by Bashing-om on 2015-08-10
liviu1; Hello;

Maybe "reverse engineer" and see what we can find ?
```

ls -al /var/lib/dpkg/info/python*.list

```
Once the package is identified, one can open the related text file in an editor and see where the files were installed to.
Isolate the one in question and make the proper edit ?

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by liviu1 on 2015-08-11
Problem solved as here: h[ttp://ubuntuforums.org/showthread.php?t=1336548]("http://www.google.com/url?q=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1336548&sa=D&sntz=1&usg=AFQjCNEUJEhHSOVCcNbmRwuqjycFP7ax2w")   . Thank you everyone for inputs!;)

---

### Post by Bashing-om on 2015-08-11
liviu1; Great !

Pleased you have resolution and as well provided the solution.

Control files, control files; What is that control file doing !

As this matter is now under control;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT][INDENT]we will have more fun
[INDENT][INDENT][INDENT][INDENT]later
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

