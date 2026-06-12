---
title: "can't install libwnck-dev"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by barnjo on 2007-02-01
tried to install libwnck-dev and got this wierd error message:

The following packages have unmet dependencies.
  libwnck-dev: Depends: libwnck18 (= 2.16.1-0ubuntu1) but 2.16.1-0ubuntu1.1 is to be installed
E: Broken packages

Anyone got any ideas?

---

### Post by empthollow on 2007-02-01
You could try installing the package listed to be installed first but generaly it will lead to requiring a string of updated packages.  The reason for the error is conflicting versions.  OR you could try installing from source, the packaging system may be causing the dependancies.  Also, you could look for a different version of the package.

---

### Post by tyce on 2007-02-01
I am seeing the same problem...


$ sudo apt-get install libwnck-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck-dev: Depends: libwnck18 (= 2.16.1-0ubuntu1) but 2.16.1-0ubuntu1.1 is to be installed
E: Broken packages

Any help appreciated!

---

### Post by hanzomon4 on 2007-02-02
Same problem here.......

---

### Post by Scotty562 on 2007-02-02
Same issue here, anyone figure it out yet?

---

### Post by jackhynes on 2007-02-02
And again here...

---

### Post by TheBlueCow on 2007-02-02
```
sudo apt-get install libwnck18=2.16.1-0ubuntu1
```

That should do the trick =D

---

### Post by hanzomon4 on 2007-02-02
Yes it does!

---

