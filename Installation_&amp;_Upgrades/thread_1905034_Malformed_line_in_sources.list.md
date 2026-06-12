---
title: "Malformed line in sources.list"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by imachavel on 2012-01-05
> **fdrake said:**
> ```

sudo dpgk --purge -a
sudo dpgk --configure -a 

```

well. I tried using those commands to remove virtual box 4.0 for a different problem involving a kernel error in which I need to re download and reinstall virtual box 4.0. then I right clicked on the app and selected uninstall and got this error:

E: Malformed line 12 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I get the same exact error when I try to open synaptic package manager. idk if this is the right thread for the question, I didn't want to start an entirely brand new thread.

---

### Post by oldos2er on 2012-01-05
Post moved to its own thread.

When in doubt, start a new thread. "Thread hijacking" is generally frowned upon.

Can you post the output of this command? You've apparently got a typo or something in your sources.list file. ```
cat /etc/apt/sources.list
```

---

### Post by imachavel on 2012-01-05
here we are:

deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) katya main upstream import
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty partner
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free

# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb games

deb [http://dl.google.com/linux/deb](http://dl.google.com/linux/deb)


sorry to hijack the thread, I just noticed that this forum moves very very fast. I wanted to try not to create another thread but anyway here is what you wanted.

---

### Post by raja.genupula on 2012-01-05
remove the last line(i mean this *deb [http://dl.google.com/linux/deb](http://dl.google.com/linux/deb)*) or put # before it and  

 open your terminal and do this 

```
 [B]wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
deb http://dl.google.com/linux/deb/ testing non-free [/B]
```

all the best

---

