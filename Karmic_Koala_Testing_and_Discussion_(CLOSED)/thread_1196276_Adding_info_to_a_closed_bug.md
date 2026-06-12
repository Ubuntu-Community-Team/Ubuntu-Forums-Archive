---
title: "Adding info to a closed bug"
date: 2009-06-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by douham on 2009-06-24
Hi, I have just added to a closed bug in Karmic ([https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/388168]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/388168") . Can someone advise as whether it's okay to add info to a closed bug or reported a new bug. Thx   

I have been all over the bug reporting stuff on the wiki many times.

---

### Post by descendent87 on 2009-06-24
I was the one who reported that bug, as far as I know it's ok to add to a closed bug if it's not fixed for you

As for valgrind, just install it then from a terminal run
```

G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log evolution
```
Then you should have a file called valgrind.log in your home folder, upload it to the bug report

---

### Post by 23meg on 2009-06-24
It's okay, but be advised that closed reports do not appear on bug listings and searches, and the only people who are alerted to your comments are the subscribers of the bug report.

For this particular case I suspect some of your packages may not be up to date. Double check that you have the fixed versions of Evolution and its dependencies.

---

### Post by descendent87 on 2009-06-24
> **23meg said:**
> the only people who are alerted to your comments are the subscribers of the bug report.

Which would be just me :P

---

### Post by 23meg on 2009-06-24
> **descendent87 said:**
> Which would be just me :P

Not exactly; you're the only *direct* subscriber. All the people and teams under the "Also notified" heading are.. also notified. But since most of them will be people who will have opted in to receive large amounts of bug mail for either a particular package, or the whole of Ubuntu, it's safe to assume that unless they're responsible for or very enthusiastic about a particular set of incoming bug reports, your comment may go unnoticed by them.

---

### Post by douham on 2009-06-24
Thanks descendant87 and 23meg. Descendant87, I had tried to get Valgrind to run but thanks for that Valgrind cmd, it got Evolution going.
 Bugger me.

---

### Post by chrisccoulson on 2009-06-25
In general, you should only comment on or reopen old bug reports if you are absolutely certain that your issue is the exact same issue as the original reporter. It's often better just to open a new bug report.

The most acceptable time to open an old bug report is if it were previously invalidated due to lack of response from the original reporter, and you have the exact same issue and can provide the missing information.

In general, it's not a good idea to reopen bug reports that were previously fixed. It's highly likely that your issue would be a different one, unless the fix regressed in some way.

---

