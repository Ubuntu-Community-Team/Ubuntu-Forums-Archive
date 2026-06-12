---
title: "installing code blocks"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by MiThRaZoR on 2011-05-22
I'm trying to install Code blocks through Software Center but it's giving me an error.

```
The following packages have unmet dependencies:

codeblocks: PreDepends: codeblocks-common (= 10.05svn7075-0ubuntu1~lucid) but 10.05svn7143-0ubuntu1~lucid is to be installed
            Depends: libcodeblocks0 (= 10.05svn7075-0ubuntu1~lucid) but 10.05svn7075-0ubuntu1~lucid is to be installed
            Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed

```

---

### Post by gsmanners on 2011-05-22
You have something going on in your apt sources? Here's what I get for codeblocks:

```
$ apt-cache policy codeblocks
codeblocks:
  Installed: 8.02-0ubuntu4
  Candidate: 8.02-0ubuntu4
  Version table:
 *** 8.02-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/universe Packages
        100 /var/lib/dpkg/status
```

---

### Post by MiThRaZoR on 2011-05-22
Hmmm. That could be it. Cause I was messing with it to get CodeBlocks from [http://lgp203.free.fr/ubuntu/](http://lgp203.free.fr/ubuntu/)

I added those repositories. Idk how to install the code blocks from there. I think it'd be better if I used those repositories cause codeblocks from the Software Center is an old version.

---

### Post by gsmanners on 2011-05-22
Looks like the latest CB depends on gcc 4.5. That might be a little too bleeding edge for Lucid.

---

### Post by MiThRaZoR on 2011-05-23
Ooh okay. Lol. And yeah, once I removed the repositories I tried adding earlier. It installed just fine. Thanks.

---

