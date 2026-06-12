---
title: "apt-get update fails to find security Release and Packages on local mirror"
date: 2021-01-10
forum: Installation &amp; Upgrades
---

### Post by gobo7 on 2021-01-10
i have built a local mirror for 16.04.  apt-get update fails to find xenial-security Release and Packages files.  

```

Reading package lists... Done                                                                                                                               
W: The repository 'file:/mnt/urepo/ubuntu1604/mirror/archive.ubuntu/ubuntu xenial-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch file:/mnt/urepo/ubuntu1604/mirror/archive.ubuntu/ubuntu/dists/xenial-security/main/binary-amd64/Packages  File not found - /mnt/urepo/ubuntu1604/mirror/archive.ubuntu/ubuntu/dists/xenial-security/main/binary-amd64/Packages (2: No such file or directory)
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

both files are in the mirror. both are set to mode 644 along with their respective directory tree.
```

/mnt/urepo/ubuntu1604/mirror/archive.ubuntu.com/ubuntu/dists/xenial-security# ls -l
total 168684
...
-rw-r--r-- 1 root root   109198 Jan 10 12:03 InRelease
-rw-r--r-- 1 root root   108233 Jan 10 12:03 Release
-rw-r--r-- 1 root root      916 Jan 10 12:03 Release.gpg


/mnt/urepo/ubuntu1604/mirror/archive.ubuntu.com/ubuntu/dists/xenial-security/main/binary-amd64# ls -l
total 11360
-rw-r--r-- 1 root root 8204866 Jan 10 12:08 Packages
-rw-r--r-- 1 root root 1896320 Jan 10 12:03 Packages.gz
-rw-r--r-- 1 root root 1521064 Jan 10 12:03 Packages.xz
-rw-r--r-- 1 root root     105 Jan 10 12:03 Release


```

instead of the web server, i'm using an nfs mount.  the only thing i can think of is my sources.list file is incorrect or missing an option.
```

deb file:///mnt/urepo/ubuntu1604/mirror/archive.ubuntu/ubuntu/ xenial-security main restricted multiverse universe

```

can anyone make a suggestion on what i'm doing wrong or missing?

thanks,
gobo

---

### Post by TheFu on 2021-01-13
16.04 support ends in a few months.  Is this issue really worth solving at ts point?
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

---

### Post by gobo7 on 2021-01-13
> **TheFu said:**
> 16.04 support ends in a few months.  Is this issue really worth solving at ts point?
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

unfortunately yes, due to libraries and kernel version.  it is the reason i built the mirror.

---

### Post by grahammechanical on 2021-01-13
When I examine my sources.list file I see similarities.

This looks about right.
> deb file:///mnt/urepo/ubuntu1604/mirror/archive.ubuntu/ubuntu/ xenial-security main restricted multiverse universe

But this looks a different path. Or am I misunderstanding?

> /mnt/urepo/ubuntu1604/mirror/archive.ubuntu.com/ubuntu/dists/xenial-security

And so does this.

> mnt/urepo/ubuntu1604/mirror/archive.ubuntu.com/ubuntu/dists/xenial-security/main/binary-amd64

Extra directories, yes? Where is the release file? Is it in .../mirror/archive.ubuntu/ubuntu/     ? That is where Update is looking. So, why the reference to archive.ubuntu.com/ubuntu/dists/xenial-security   ?

Well, you did invite anyone to make a suggestion. And I am anyone. :)

Regards

---

### Post by gobo7 on 2021-01-13
> **grahammechanical said:**
> When I examine my sources.list file I see similarities.

Extra directories, yes? Where is the release file? Is it in .../mirror/archive.ubuntu/ubuntu/     ? That is where Update is looking. So, why the reference to archive.ubuntu.com/ubuntu/dists/xenial-security   ?

Well, you did invite anyone to make a suggestion. And I am anyone. :)

Regards

the directory ".../mirror/archive.ubuntu.com/ubuntu" was made by apt-mirror.  i should have included the statement from my mirror.lists (and didn't)
```

deb-amd64 http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse

``` 
under archive.ubuntu.com/ubuntu are two directories -- dists and pool.

the Packages file apt-get update is fussing about does exist:
```

/mnt/urepo/ubuntu1604/mirror/archive.ubuntu.com/ubuntu/dists/xenial-security/main/binary-amd64$ ls -l
total 11360
-rw-r--r-- 1 root root 8204866 Jan 12 00:11 Packages
-rw-r--r-- 1 root root 1896320 Jan 11 23:55 Packages.gz
-rw-r--r-- 1 root root 1521264 Jan 11 23:55 Packages.xz
-rw-r--r-- 1 root root     105 Jan 11 23:55 Release

```
on a test machine i didn't care much about, i just picked a package to install from the mirror.  it worked.  it installed the oldest version in the mirror not the latest.  so that kinda tells me the directory structure is mostly correct.  mostly???

---

