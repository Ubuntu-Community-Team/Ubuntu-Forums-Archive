---
title: "Where to get /lib/modules/*/build?"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by xephyrus on 2008-08-01
I have been searching and trolling every ditch I can think of.  I can't find the answer to this very simple question:

Where does the /lib/modules/$(uname -r)/build directory come from?

I think the question itself is too simple.  People don't bother answering it.  It's like asking for air to breath.  It's just there.  Yeah, except it isn't.

My ubuntu-server installation doesn't have it, and I need it to build one very small, simple, maybe even silly, module.  How do I get that magical, apparently-almost-omnipresent directory onto my system?

Any help gets Thanks,
.  Topher

---

### Post by ibutho on 2008-08-01
I think when you install the kernel (linux) source, then the directory you mentioned is created.

---

### Post by xephyrus on 2008-08-01
Yeah, I figured that too.  Not true.

automan@casaman:~$ sudo apt-get install linux-source-2.6.24
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-source-2.6.24 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

I already have it, and I don't have any /lib/modules/2.6.24-19-*/build dir.

](*,)

.  Topher

---

### Post by ibutho on 2008-08-01
Have you tried installing linux-headers.

---

### Post by xephyrus on 2008-08-01
Yap.  Got that:

automan@casaman:~$ sudo apt-get install linux-headers-2.6.24-19-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-19-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

.  Topher

---

### Post by xephyrus on 2008-08-01
Ope!  I think I just solved it.

On a lark I installed the linux-headers for -generic rather than -server.  That has the build dir there, but the -server doesn't.  Is that a bug?

Anyhow, I can see that it's just a link into /usr/src/linux-headers-*, so I can make that link manually.  I do have the /usr/src/linux-headers-*-server dir, so it looks like everything is in place except that one link.

Many thanks for the clue!

.  Topher

---

