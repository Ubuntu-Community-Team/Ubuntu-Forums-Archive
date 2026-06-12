---
title: "My Hoary machine will not recognize Breezy install CD!!"
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by pointym5 on 2006-02-26
I keep reading about how the update manager is supposed to magically recognize a Breezy install CD, and magically ask me if I want to upgrade. It does not. :evil: :evil: 

I've tried manually adding the CD, and that does not work either; I get the same error I get when I try to add the CD with "apt-cdrom" ("not a Debian CD"; it can't find the Packages info).  I've tried two separate burned copies of the CD, both of which seem to be in perfectly good shape.

How can it possibly be the case that my installation is somehow broken?  In all other respects my package management stuff seems happy; in other words, I can bring up Synaptic and everything works fine.

---

### Post by robenne on 2006-02-26
Open Synaptic and under the the "EDIT" click "Add CDROM". Then click on "Reload Package ...", then click on the "Mark All Upgrades", "Apply" 

This should do the trick. Also if you downloaded the ISO and burned it to CD make you burned it as an ISO file.

Hope this helps.

:cool:

---

### Post by pointym5 on 2006-02-26
No, that does not work!  When I attempt to "Add CD", Synaptic tells me that it cannot find any packages on the CD and that it's "not a Debian disk," as I wrote above.

---

### Post by robenne on 2006-02-26
:-k  Did you make the CD or is it one shipped from Ubuntu?

If you burned it, make sure that you are burning it as an ISO CD and NOT a DATA CD. 

:cool:

---

### Post by pointym5 on 2006-02-26
The CD is fine - I can boot from it with no problem and it correctly initiates the install process.

... though I realize that I have no idea what you're talking about.  I burned the ISO image like I always do, from the command line with cdrecord.

---

### Post by pointym5 on 2006-02-26
One thing I don't get: the "apt-cdrom" man page lists a "-a" (or "--thorough") option, which supposedly tells it to search more thoroughly for package files. However when I try that on my CD running it through strace I see absolutely no difference in behavior from when I run it without "-a".

Relevant excerpt from the strace output:```
stat(".disk", 0x7fbfffedc0)             = -1 ENOENT (No such file or directory)
stat(".aptignr", 0x7fbfffedc0)          = -1 ENOENT (No such file or directory)
stat("Release.gpg", 0x7fbfffedc0)       = -1 ENOENT (No such file or directory)
stat("Packages", 0x7fbfffedc0)          = -1 ENOENT (No such file or directory)
stat("Packages.gz", 0x7fbfffedc0)       = -1 ENOENT (No such file or directory)
stat("Sources.gz", 0x7fbfffedc0)        = -1 ENOENT (No such file or directory)
stat("Sources", 0x7fbfffedc0)           = -1 ENOENT (No such file or directory)
open(".", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = 3
fstat(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl(3, F_SETFD, FD_CLOEXEC)           = 0
getdents64(3, /* 2 entries */, 4096)    = 48
getdents64(3, /* 0 entries */, 4096)    = 0
close(3)                                = 0
chdir("/etc/")                          = 0
write(1, "Found 0 package indexes, 0 sourc"..., 59Found 0 package indexes, 0 source indexes and 0 signatures

```

The packages on the installation CD are of course all under "dists/breezy/main", but apt-cdrom is making no attempt at all to find them.  Oddly, it stats .disk and finds nothing. The .disk directory definitely exist on the cd. :confused:

---

### Post by pointym5 on 2006-02-26
Well, it looks like the whole affair has been a complete waste of time anyway, as the upgrade process (regardless of how I run it)  is an unmitigated disaster. Looks like it's time for a complete re-install, which really sucks.

---

