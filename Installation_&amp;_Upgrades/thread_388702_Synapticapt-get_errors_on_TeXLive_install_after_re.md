---
title: "Synaptic/apt-get errors on TeXLive install after removal"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by Timtro on 2007-03-19
Hello all,

I reticently decided to remove TeXLive and do a clean install, due to some exotic font problems. There was a broken package, yadda, yadda, thats a bug report in itself.

So! Stupid me runs `apt-get autoremove texlive-full`, `apt-get autoremove texlive-bin`... and so on. Then! I get the clever idea to open Synaptic and wipe out anything that may have been hiding. Sure enough, I found a couple of things and removed them all. Bad idea! Apparently I wiped out something so fundamental that I can't seem to get it back to satisfy what ever dependencies the texlive family has.

Now when I try to install anything with synaptic I get,
```

texlive-full:

Package texlive-full has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

```

As if this isn't fun enough, I try using apt-get, which yields yet more exciting news,
```

tteatro@photon:~$ sudo apt-get install texlive-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package texlive-full is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package texlive-full has no installation candidate

```

This goes for anything else in the TeXLIVE genus that I have attempted to synaptic or apt-get.

Any ideas?


Thanks for helping me out of my mess.

Gratefully yours,


Tim.

---

### Post by Timtro on 2007-03-19
Not sure how or why, but replacing my sources.list fixed it.

For the hell of it (or to get a faster server) I decided to have the ubuntu source-o-matic ([http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)) draft me up a fresh sources.list. And perhaps because I'm slightly insane, I decided to try sudo apt-get again and it worked!

Thanks to all who may have read this!

---

