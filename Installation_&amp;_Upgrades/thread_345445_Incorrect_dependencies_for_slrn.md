---
title: "Incorrect dependencies for slrn"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by ralphmerridew on 2007-01-24
The version of slrn being distributed ( slrn 0.9.8.1pl1 ) is meant to be used with s-lang 1, but only s-lang 2 is available.  (Parts of it won't display correctly with the newer library.)

Please, either fix the dependencies, or make the CVS slrn (written against s-lang 2) available.

---

### Post by andrew.46 on 2007-06-11
Hi,

 Being an slrn groupie I read your post with interest:

> **ralphmerridew said:**
> The version of slrn being distributed ( slrn 0.9.8.1pl1 ) is meant to be used with s-lang 1, but only s-lang 2 is available.  (Parts of it won't display correctly with the newer library.)

Please, either fix the dependencies, or make the CVS slrn (written against s-lang 2) available.

 I have compiled slrn recently using the developer release (0.9.8.1pl1) and have had no problems. This release works with s-lang 2 and I suspect the Dapper repository version has been compiled against it. You can check this by running:

```
slrn --version
```

 My compiled version shows:

```
andrew@ilium:~$ slrn --version
Slrn 0.9.8.1pl1 [2005-02-17]
        * Note: This version is a developer preview.
S-Lang Library Version: 2.0.5
Compiled at: Jun 10 2007 20:52:02
Operating System: Linux

```

Files you may need to install to compile:

```
sudo apt-get  install libslang2  libslang2-dev
```

 Hope this helps,

      Andrew

---

