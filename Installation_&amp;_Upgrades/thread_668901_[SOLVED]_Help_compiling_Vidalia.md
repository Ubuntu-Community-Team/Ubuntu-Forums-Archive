---
title: "[SOLVED] Help compiling Vidalia"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by absolutezero1287 on 2008-01-15
I'm trying to install a program called Vidalia. It's the GUI for Tor, an onion router type proxy. The instruction for Linux and Ubuntu are there but I'm afraid that I don't understand them. Can anyone be of some assistance?

[http://trac.vidalia-project.net/wiki/InstallSource](http://trac.vidalia-project.net/wiki/InstallSource)

Thanks

---

### Post by absolutezero1287 on 2008-01-19
I haven't worked with BASH for too long, one part that lost me was part 3 under Linux/BSD/Unix General. "Run ./configure && make from the location of Vidalia's source." How exactly do I do that? I already extracted the contents of the tar.gz file so I imagine that this is next?

I generally understand that I have to run certain commands but I don't know how to go about it nor do I know the proper syntax.

Also, would it be a better idea to extract the tar.gz file to some place other than my home directory? (Right now it's sitting on my desktop).

---

### Post by p_quarles on 2008-01-20
The "location of the source" is the directory that was created when you extracted the file. In the terminal, use the "cd" command to change directories.

It doesn't matter where the source is located when you compile it. The last step:
```
sudo make install
```
will put the compiled application in the proper place.

---

### Post by absolutezero1287 on 2008-01-20
Well I understand that but what goes inbetween, i.e.
sudo make (?) install (?)

---

### Post by p_quarles on 2008-01-20
> **absolutezero1287 said:**
> Well I understand that but what goes inbetween, i.e.
sudo make (?) install (?)
Nothing. That's a single command.

---

### Post by absolutezero1287 on 2008-07-04
Got vidalia up and running by following the instruction.

---

