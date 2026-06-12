---
title: "Is the official upgrade method really the best?"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2007-02-23
I've read in some places that people did fine with the "official" upgrade method (from Dapper to Edgy), and that some people went through hell with it. I can't find a definite answer anywhere, so I wanted to know whether you people recommend the ```
gksu "update-manager -c"
``` method or some other way. Any suggestions?

---

### Post by taurus on 2007-02-23
If you can backup your important files, do a fresh install.  That's the best method; otherwise, that is the official method to upgrade from Dapper to Edgy.

---

### Post by rainwalker on 2007-02-23
When you say "important files" do you mean my home directory? I backed that up, but I'd prefer to be able to upgrade without doing a clean install.

---

### Post by rainwalker on 2007-02-23
Okay, I ran the command in the terminal and it gave me > warnings.warn("apt API not stable yet", FutureWarning)
Is this bad?

---

### Post by rainwalker on 2007-02-23
I went ahead with the install and I got this:
> Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or with synaptic.

What should I do?

---

### Post by taurus on 2007-02-23
Before you run that command to upgrade your machine from Dapper to Edgy, you're supposed to comment out all the 3rd party repos in /etc/apt/sources.list.  That's what it's telling you right now.

Just continue.

---

### Post by rainwalker on 2007-02-23
How do I re-enable them after the upgrade? I'm not actually sure what 3rd-party sources it's talking about

---

### Post by taurus on 2007-02-23
You can enable them again by removing the # in front of them in /etc/apt/sources.list.  

Post your /etc/apt/sources.list here and maybe I can spot some extra repos in there for you.

```
cat /etc/apt/sources.list
```

---

### Post by rainwalker on 2007-02-23
Here:> deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiversedeb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


---

### Post by rainwalker on 2007-02-23
Oy, I have to go eat dinner, I'll be back in a little while

---

### Post by taurus on 2007-02-23
The universe, multiverse, and edgy-backports are extra repos.

---

### Post by rainwalker on 2007-02-24
Okay, problem. I'm in the process of upgrading, it's about 5/6 done fetching and installing the packages and I just got a message asking if I want to replace the customized configuration file 'etc/services'. What is this file?

---

