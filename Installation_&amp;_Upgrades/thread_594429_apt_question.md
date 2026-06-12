---
title: "apt question"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by jon3k on 2007-10-28
How do I found out what package provides a particular file?

For example, I was trying to find what packages contain the standard C libraries (stdio.h, etc).

jon@host:~/$ sudo apt-cache search stdio.h
jon@host:~/$

So really two questions:
1.) How do I find what packages provide a certain file I'm looking for?
2.) Where is stdio.h?

---

### Post by taurus on 2007-10-28
That file is part of the build-essential package.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by jon3k on 2007-10-28
ok - i needed libc6-dev (and dependencies) which I actually had to do a google search to find :(

So, it's half solved.  Anyway want to tell me the appropriate "ubuntu way" of solving this problem?

On fedora I would have just:
$ sudo yum provides stdio.h
<package name>
$ sudo yum install <package name>

---

### Post by jon3k on 2007-10-28
> **taurus said:**
> That file is part of the build-essential package.

```
sudo aptitude update
sudo aptitude install build-essential
```

wow that was a bunch of stuff I didn't need at all.  I don't care about any of the C++ stuff, I just wanted the standard C header files.

---

### Post by taurus on 2007-10-28
It's the whole package so it's like take it or leave it thing.

---

### Post by jon3k on 2007-10-28
No, no, build-essentials requires like 4 packages I don't need.  The only package I needed was libc6-dev.

But the original question stands - how do you determine which package a file is in?

---

### Post by jon3k on 2007-10-31
bump - is this not possible?

---

### Post by boweeb on 2007-11-02
> how do you determine which package a file is in?
I don't know the answer to that question, but if you're trying to install libc6-dev, the ONLY way to get it is to install "build-essential". Taurus is right:> It's the whole package so it's like take it or leave it thing.

---

### Post by ruibernardo on 2007-11-02
> **jon3k said:**
> how do you determine which package a file is in?

That's an interesting feature. Searched a bit and found the answer [here]("http://debaday.debian.net/2007/01/24/apt-file-search-for-files-in-packages-installed-or-not/"): apt-file.

```
user@desktop:~$ sudo apt-get install apt-file
user@desktop:~$ sudo apt-file update

```Wait while apt-file downloads files from the repositories and builds the search database, then search for the files you want (stdio.h is kinda a popular file, so I've just put the libc6-dev output here):

```
user@desktop:~$ apt-file search stdio.h
...
libc6-dev: usr/include/stdio.h
libc6-dev: usr/include/stdio.h
libc6-dev: usr/include/stdio.h
...

```This works even if you don't have the package installed. Final match result: 
yum 1 - 1 APT

:popcorn:

---

