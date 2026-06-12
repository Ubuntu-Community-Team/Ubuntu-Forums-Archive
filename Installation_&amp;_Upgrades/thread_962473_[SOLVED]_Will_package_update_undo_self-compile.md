---
title: "[SOLVED] Will package update undo self-compile?"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by steviefordi on 2008-10-29
Not sure if this is the right forum, sorry if not, but here goes...

I recently downloaded the source code for mplayer from their website and compiled it. I needed it to work with a restricted format codec that was not included in the medibuntu release.

All seems to be working fine now but every day I get a message to update this package to the one in the repositories.

My question is, if I update, will this break my working version of mplayer? If so how can I stop my system wanting to update this package?

---

### Post by andrew.46 on 2008-10-29
Hi,

The repository version of MPlayer, which would be older than the ?svn version you have compiled and will overwrite your newer version. Do you need MPlayer to be part of the package management system? If not just ./configure / make / sudo make install and the package manager will not bother you.

  Andrew

---

### Post by steviefordi on 2008-10-30
Thanks for the tip.

The compilation instructions in the ubuntu docuentation suggest using checkinstall rather than make install in order to package the
application. I admit following this blindly without properly understanding what I was doing. 

The only reason I would want mplayer in the package management system is to remove it easily if I wanted (not that I'm planning to).

Problem is I wouldn't know how to uninstall something if it wasn't packaged. I guess you have to go deleting all the files and directories it created during install, but how do you know where they are?

---

### Post by Partyboi2 on 2008-10-30
Have you tried to lock the version in synaptic package manager? Search synaptic for your the package and then highlight and select "Package" then "lock version"

---

### Post by steviefordi on 2008-10-30
Partyboi2 you rock!!

That was exactly what I needed. I thought there must be a way to stop ubuntu reporting on updates to packages that I didn't want to update. I just didn't know where to go and what to do...

I'd still really like to know how you go about removing an application that hasn't been installed via a package?

I don't actually need to do this but it would help deepen my understanding of ubuntu and Linux in general.

---

### Post by Partyboi2 on 2008-10-30
>  I'd still really like to know how you go about removing an application that hasn't been installed via a package? If you compiled a program from source normally you would cd (change directory) into the source directory and uninstall it by
```
sudo make uninstall
```

---

### Post by steviefordi on 2008-10-31
Nice one! You wouldn't believe I've been a programmer for 10 years would you. Just never on a decent OS.

See ya...):P

---

