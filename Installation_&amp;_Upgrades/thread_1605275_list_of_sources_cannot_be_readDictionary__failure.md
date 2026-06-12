---
title: "list of sources cannot be read/Dictionary  failure"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by Evangelia23 on 2010-10-25
I am running ubuntu 9.10.Few days ago I installed packages that apparently have unmet dependencies and now as soon as i turn my pc on, there is a red sign saying:Error opening cache E:malformed line 56 in source. list of sources could not be read.The same red stop sign suggests that i run the package manager to deinstall these packages,however every time i try to open it  doesn't ready do anything. Tried going to the software center to deinstall from there and it doesn't even read the installed packages.Tried going to terminal giving apt-get command plus the suggested commands  but I can't really work it out.Another thing that has failed me is the dictionary, apparently it cannot connect to server dict.org 2628.Any suggestions? 
Thanks

---

### Post by LotusTekINC on 2010-10-25
I just recently had the same issue when i went into the file where the update packages are listed i saw there was a file in the folder called "lock" that was present i moved the document to another directory and edited a new lock file and i was able to download using my apt.

I can't be sure this is the same problem but look for the "lock" file in the error list if its present follow the directory and remove that file and your good.

---

### Post by mörgæs on 2010-10-25
It might be dangerous to delete the lock file. 

As a first step, best is to boot the machine and run 
```
sudo apt-get update 
sudo apt-get upgrade
```

and post the error messages, if any.

If any application opens during the process, including Update Manager, it should be closed.

---

