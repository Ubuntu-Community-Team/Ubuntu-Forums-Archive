---
title: "Repo Errors?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by moore.bryan on 2007-10-19
*when i try to update-manager, it tells me the signatures of the base ubuntu feisty repos are invalid; anyone else?*

---

### Post by FredB on 2007-10-19
Can you post your /etc/apt/sources.list ?

And invalid ? Maybe server are under a too big pressure with gutsy release...

---

### Post by moore.bryan on 2007-10-19
```

## BASE
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse  
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse  

## UPDATES
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse  
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse  

## BACKPORTS
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse  
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse  

## SECURITY
deb http://security.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse    
deb-src http://security.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse     

## PROPOSED
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed main restricted universe multiverse

```
*this is what i get:*
```

W: GPG error: http://archive.ubuntu.com feisty-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com feisty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

---

### Post by likes2skate on 2007-10-23
On two machines (a desktop and a laptop), I get a similar error, namely this:

[INDENT]GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release: The following
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>[/INDENT]

What is going on?

Thanks

---

