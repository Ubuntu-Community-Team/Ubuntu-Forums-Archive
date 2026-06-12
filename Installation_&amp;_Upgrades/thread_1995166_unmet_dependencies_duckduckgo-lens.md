---
title: "unmet dependencies duckduckgo-lens"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by Lorin Ricker on 2012-06-03
Ubuntu 12.04 LTS (Precise) -- I was exploring Unity Lenses today, and came across this web article:

"[What lenses for Unity are available?]("http://askubuntu.com/questions/38772/what-lenses-for-unity-are-available")" ([http://askubuntu.com/questions/38772/what-lenses-for-unity-are-available](http://askubuntu.com/questions/38772/what-lenses-for-unity-are-available))

Decided to attempt to install a couple of them: 1) the Wikipedia lens, which installation worked fine; and 2) the DuckDuckGo lens, which installed with errors (but appears to work).

DuckDuckGo install went like this:

```

sudo add-apt-repository ppa:w-vollprecht/ppa
sudo apt-get update
sudo apt-get install duckduckgo-lens
```

This resulted in a broken/unmet dependency:

```

$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 duckduckgo-lens : Depends: python-unity-singlet but it is not installed
E: Unmet dependencies. Try using -f.
```

and "trying to use -f" replicates the problem and results in:

```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-unity-singlet
The following NEW packages will be installed:
  python-unity-singlet
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/5,932 B of archives.
After this operation, 84.0 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 220367 files and directories currently installed.)

Unpacking python-unity-singlet (from .../python-unity-singlet_0.2.2-ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/python-unity-singlet_0.2.2-ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/pyshared/singlet/__init__.py', which is also in package unity-singlet 0.2.1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/python-unity-singlet_0.2.2-ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Like I said, the new lenses, both Wikipedia and DuckDuckGo, appear to work fine (after restarting my login session).

Any advice for how to remove this broken package &/or dependency?  I've now got an ugly red-circle-with-minus-sign in my top task-bar which demarks this problem until I can remove it.  TIA! :(  -- Lorin

---

### Post by raja.genupula on 2012-06-03
```
sudo rm  /var/cache/apt/archives/python-unity-singlet_0.2.2-ubuntu1_all.deb 

sudo apt-get install -f
```

do them one by one .

---

### Post by Lorin Ricker on 2012-06-03
Thanks, Raja.

Did the rm with the -v flag, to confirm file removal... check.

The "sudo apt-get install -f" apparently re-fetches the same .deb file, and then fails with exactly the same behavior as originally posted.

So now I'm more confused... Advice?  TIA -- Lorin

---

### Post by Lorin Ricker on 2012-06-04
Fixed/resolved broken dependency by removing the dependent package **duckduckgo-lens**:

```

$ sudo apt-get remove duckduckgo-lens
  ...
$ sudo rm -v /var/cache/apt/archives/python-unity-singlet_0.2.2-ubuntu1_all.deb
removed `/var/cache/apt/archives/python-unity-singlet_0.2.2-ubuntu1_all.deb'
$ sudo apt-get install -f
  ...
```

So, as of this writing, count the **duckduckgo-lens** as not-yet-ready-for-prime-time.

---

