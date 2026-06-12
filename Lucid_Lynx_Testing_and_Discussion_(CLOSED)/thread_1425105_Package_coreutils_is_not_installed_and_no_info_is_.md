---
title: "Package coreutils is not installed and no info is available"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by coverslide on 2010-03-08
```

 $ sudo dpkg-query -s coreutils
Package `coreutils' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

OK so I did an upgrade to lucid on my machine, and a few headaches later I've managed to get it stable, but one thing that's been bugging me is that dpkg-reconfigure no longer works, not with any package, all I get is:

```

Package `whateverpackageitype' is not installed and no info is available.

```

I've poked around a bit and found the string comes from dpkg-query, so I type 

```
sudo dpkg-query -s ANYTHING
```

and it gives me the exact same results as above. I've tried anything and everything to get a package to show up but to no avail.

```

 $ sudo apt-get install coreutils
 $ sudo apt-get install -f coreutils
 $ sudo apt-get install --reinstall coreutils
 $ sudo apt-get install -f --reinstall coreutils

```

Still nothing. Does anybody have any idea on how to fix this problem? Thanks.

---

### Post by overdrank on 2010-03-08
Moved to Lucid Lynx Testing and Discussion

---

### Post by VMC on 2010-03-09
Here's my output of coreutils query:

```
$ aptitude show coreutils
Package: coreutils
Essential: yes
State: installed
Automatically installed: no
Version: 7.4-2ubuntu2
```

So you can't do any *cat, date, ls, df*, etc commands?!

---

