---
title: "libsm6 vs. libc6 version conflict"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by CptPicard on 2010-12-05
Recent routine updates to my Maverick box turned into quite a mess; I've ended up with a machine where I've had to remove pretty much everything to track down the version conflict that has resulted in the removal of a lot of stuff.

Anyway, it all boils down to this: The libsm6 library has the following conflict with libc6:

```

libsm6: Depends: libc6 (>= 2.t) but 2.12.1-0ubuntu9 is to be installed

```

This in turn prevents the installation of the entire X.Org server.

What on Earth is this "2.t" version of libc? Any ideas as to how to go about fixing this or am I going to just reinstall from scratch?

---

### Post by sikander3786 on 2010-12-05
Most of the time, aptitude is able to fix dependency issues like this.

Did you try to manually install the correct versions?

[http://packages.ubuntu.com/maverick/libsm6](http://packages.ubuntu.com/maverick/libsm6)

[http://packages.ubuntu.com/maverick/libc6](http://packages.ubuntu.com/maverick/libc6)

---

### Post by CptPicard on 2010-12-05
I tried that with libsm6, but it's of no use because it still fails the rest of the installations because its dependencies are still broken even if I force dpkg to install it.

It's almost as if there is a bug in libsm6's dependencies -- what kind of a version of libc is "2.t"?

---

### Post by sikander3786 on 2010-12-05
> what kind of a version of libc is **[COLOR="Red"]"2.t"[/COLOR]**?

That sounds like a bug or "oops".

Are there any errors when you do.

```
sudo apt-get check
```

---

### Post by CptPicard on 2010-12-05
Yes, I am suspecting that the libsm6 package's dependencies have a typo or something and that then breaks everything. I manually installed libsm6 from Lucid and things are advancing nicely; I guess I'll have to file a bug against the newest version...

---

