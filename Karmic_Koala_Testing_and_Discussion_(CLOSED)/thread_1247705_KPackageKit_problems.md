---
title: "KPackageKit problems"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nomnomnom on 2009-08-23
I can't use KPackageKIt anymore as I get this;

```

Error Type: Error Value: 'PackageKitCache' object has no attribute '_dict' File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1966, in main() File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1963, in main run(args, options.single) File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1925, in run backend.dispatcher(args) File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 643, in dispatcher self.dispatch_command(args[0], args[1:]) File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 540, in dispatch_command self.get_updates(filters) File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 653, in get_updates for pkg in self._cache.getChanges(): File : /usr/lib/python2.6/dist-packages/apt/cache.py, line 164, in getChanges for p in self: File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 196, in __iter__ for pkgname in sorted(self._dict.keys()):

```

Anyone have any idea how to fix this?

P.S. I'm using Kubuntu Alpha 4 x64.

---

### Post by nomnomnom on 2009-08-23
Sorry for the problem all being in one long line, but I created the post in Konqueror... T_T'

---

### Post by tghe-retford on 2009-08-23
Known bug, it says that a fix has been committed, but KPackageKit doesn't work for me yet:

[https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/415993](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/415993)

---

### Post by taavikko on 2009-08-23
> **tghe-retford said:**
> Known bug, it says that a fix has been committed, but KPackageKit doesn't work for me yet:

[https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/415993](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/415993)

Fix commited means that the underlying problem is been fixed.
Fix released means that the fixed package is been uploaded to repos.

---

### Post by nomnomnom on 2009-08-23
> **tghe-retford said:**
> Known bug, it says that a fix has been committed, but KPackageKit doesn't work for me yet:

[https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/415993](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/415993)

Thanks.

---

### Post by taavikko on 2009-08-25
Fix released, in the repos.

---

### Post by tghe-retford on 2009-08-25
Not quite fixed yet. Updated less than an hour ago. As soon as I search for something, aptBackend.py crashes and apport immediately pops up to ask me to report the error.

---

### Post by taavikko on 2009-08-25
> **tghe-retford said:**
> Not quite fixed yet. Updated less than an hour ago. As soon as I search for something, aptBackend.py crashes and apport immediately pops up to ask me to report the error.

Use main server, local mirrors are usually behind.
Info: [https://edge.launchpad.net/ubuntu/+archivemirrors](https://edge.launchpad.net/ubuntu/+archivemirrors)

---

### Post by tghe-retford on 2009-08-25
> **taavikko said:**
> Use main server, local mirrors are usually behind.
Info: [https://edge.launchpad.net/ubuntu/+archivemirrors](https://edge.launchpad.net/ubuntu/+archivemirrors)
I am using the main server and everything is up to date. The error still occurs. :(

---

### Post by taavikko on 2009-08-25
> **tghe-retford said:**
> I am using the main server and everything is up to date. The error still occurs. :(

output of
```
dpkg -l *packagekit\*
```

---

### Post by VMC on 2009-08-25
$ dpkg -l *packagekit\*
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  packagekit-bac <none>         (no description available)
```

---

### Post by tghe-retford on 2009-08-25
Output of: dpkg -l *packagekit\*
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                         Version                      Description
+++-============================-============================-========================================================================
ii  kpackagekit                  0.4.2-0ubuntu2               KDE package management tool using PackageKit
ii  libpackagekit-glib11         0.4.9+20090825-0ubuntu1      Library for accessing PackageKit using GLib
ii  libpackagekit-qt11           0.4.9+20090825-0ubuntu1      Library for accessing PackageKit using Qt.
ii  packagekit                   0.4.9+20090825-0ubuntu1      provides a software installation daemon
ii  packagekit-backend-apt       0.4.9+20090825-0ubuntu1      APT backend for packagekit
un  packagekit-backend-smart     <none>                       (no description available)
un  packagekit-kde               <none>                       (no description available)
ii  python-packagekit            0.4.9+20090825-0ubuntu1      PackageKit Python bindings
```

---

