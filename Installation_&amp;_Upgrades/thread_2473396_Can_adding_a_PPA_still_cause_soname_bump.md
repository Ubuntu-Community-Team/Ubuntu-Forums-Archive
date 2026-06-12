---
title: "Can adding a PPA still cause soname bump?"
date: 2022-04-03
forum: Installation &amp; Upgrades
---

### Post by jis on 2022-04-03
I wonder, if a soname bump can happen when using some PPA in Ubuntu 20.04, for example? Can you give a detailed example of such a case?

---

### Post by TheFu on 2022-04-03
I can't see why not.
[https://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html](https://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html)
PPAs are trusted, by definition, and can add or replace any package on the system.

---

### Post by jis on 2022-04-03
That article does not say, if the soname bumps may affect to naming of the packages that contain the soname bumped libraries. At least sometimes in the past the package names have had some numbering, too. Is there some policy in package naming nowadays?

---

### Post by TheFu on 2022-04-03
There is no 1 person who decides these things and no standards exist to my knowledge. The library builders get to set it however they like, though I have to admit I've never gone out of my way to set the soname on any shared library that I've created.

---

### Post by jis on 2022-04-04
I asked this, because ppa-purge software does some guesswork on renamed packages when downgrading in order to purge a PPA. Can we assume that soname bumps are possible only for packages that contain libraries and whose package name start by "lib"?

---

### Post by TheFu on 2022-04-04
I wouldn't assume anything.  Check all the packages and libraries on your system. Shouldn't be more than a 5-10 line script. Then you'd KNOW the answer.

I've never used ppa-purge. It isn't a core package.

---

### Post by jis on 2023-03-05
I would like to know, if there is such a PPA available for 18.04 or 20.04.

---

### Post by ActionParsnip on 2023-03-05
> **jis said:**
> I would like to know, if there is such a PPA available for 18.04 or 20.04.

You can search PPAs

---

### Post by jis on 2023-11-19
Even though there was a soname bump, shouldn't the older version of the respective library be installed as a dependency, when downgrading packages? It seems like there was some manual library downgrading needed in the past at least: [https://bugs.launchpad.net/ubuntu/+source/ppa-purge/+bug/1392954](https://bugs.launchpad.net/ubuntu/+source/ppa-purge/+bug/1392954)

---

### Post by jis on 2023-11-20
> **ActionParsnip said:**
> You can search PPAs

Sure, currently there are 36082 PPAs in [the search]("https://launchpad.net/ubuntu/+ppas?name_filter=") and I have to click each to see which packages they provide.

---

