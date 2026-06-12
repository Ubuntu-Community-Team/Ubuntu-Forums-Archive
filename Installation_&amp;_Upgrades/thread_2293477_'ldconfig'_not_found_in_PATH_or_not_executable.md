---
title: "'ldconfig' not found in PATH or not executable"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by john_4 on 2015-09-05
Hello,
I have a notification saying I have unmet dependencies. If I try to install the updates, it says "The package system is broken".

If I run "apt-get install -f", I get the following errors:
```

Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
This is after trying to install "libc-bin".

I also did "echo $PATH"
and got the following:

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

---

### Post by steeldriver on 2015-09-05
Hello and welcome to the forums

**How** exactly did you try to install libc-bin?

---

