---
title: "List modified system files?"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by mikeym on 2011-08-12
Hi,

I'm about to do a migration on a laptop where I have had to make a number of modifications to files mainly in /etc/ but I have lost track of what I have done. Does anyone have any suggestions as to how to identify those files that have been modified from their packaged versions?

---

### Post by slooksterpsv on 2011-08-12
You could do this:

```

ls -alh /etc | grep 2011-08-11

```

Here's what I did though, it just shows what was modified from the 6th

```

_____@_______:~/Downloads/firefox$ ls /etc -alh | grep 2011-08-06
drwxr-xr-x   3 root    root    4.0K 2011-08-06 00:57 apache2
drwxr-xr-x   6 root    root    4.0K 2011-08-06 00:55 apt
drwxr-xr-x   2 root    root    4.0K 2011-08-06 00:57 javascript-common
drwxr-xr-x   3 root    root    4.0K 2011-08-06 00:57 lighttpd
drwxr-xr-x  15 root    root    4.0K 2011-08-06 00:57 xdg

```

---

### Post by mikeym on 2011-08-12
I would need to know the dates of each file modified, wouldn't I?

I was thinking more along the lines of using something like debsums on all the packages with files in /etc/ Just not sure how to do it.

---

### Post by mikeym on 2011-08-12
well, I've done this:

```

dpkg --get-selections > ~/installed-software
debsums -ec `cat ~/installed-software | cut -f 1` | tee ~/modified_configs

```

Which has picked up a couple of things I knew I'd modified but has definitely missed many of the core system files that I'm sure I modified some of. Also I'm not sure the installed-software list works as it has included some packages that are no longer installed.

---

