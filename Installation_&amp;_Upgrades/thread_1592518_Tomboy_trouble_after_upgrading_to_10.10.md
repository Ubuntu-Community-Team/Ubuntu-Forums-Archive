---
title: "Tomboy trouble after upgrading to 10.10"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by shaagerup on 2010-10-10
After upgrading to Ubuntu 10.10 my Tomboy will not start.

I tried to backup and remove the /home/soren/.local/share/tomboy directory, but it didn't solve it.

I have attached a dump of this:
```
$ tomboy --debug &> tomboy.txt
```

It ends with
```

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================
```
so it certainly looks like something is wrong.

Any suggestions on how I might solve this issue?

---

### Post by sharm on 2010-10-11
rm -rf ~/.config/tomboy/addin*
tomboy --debug

Then you should be fine.  This is a random Mono.Addins bug that I've seen from time to time.

---

### Post by shaagerup on 2010-10-11
Thanks a lot for your answer! It works nicely now!

---

