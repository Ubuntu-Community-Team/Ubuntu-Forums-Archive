---
title: "Checking glibc installed version"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by arodulfo on 2014-09-25
Dear all,

I need to check my glibc version is 2.15 or later. After reading this [link]("http://ubuntuforums.org/showthread.php?t=2088459"), I got the following results:
```

~$dpkg-query -l glibc* | grep un

un glibc-2.13-1
un glibc-doc

```

When looking for libc6 in synaptic, all the versions shown say 2.15-0ubuntu10.7. :confused:

If I pay attention to the first one, I slhould upgrade my glibc to the latest available version.
If I pay attention to synaptic, which I am tempted to do, my current system is ok and need no glibc upgrade.

Which one is correct?

Thanks a lot for being there! Kind regards. ):P

---

### Post by kc1di on 2014-09-25
Which version of Ubuntu you using? 
My 14.04 install shows glibc of 2.19 -- Latest glibc released is 2.20 on 2014-09-07.

---

### Post by ian-weisser on 2014-09-25
I think you have discovered a bug in an old version in 12.04 (wrong release number).

Different releases of Ubuntu use appropriately released version of libc6 for their time.

```
$ rmadison -u ubuntu libc6
 libc6 | 2.11.1-0ubuntu7    | lucid            | amd64, armel, i386, powerpc, sparc
 libc6 | 2.11.1-0ubuntu7.17 | lucid-security   | amd64, armel, i386, powerpc, sparc
 libc6 | 2.11.1-0ubuntu7.17 | lucid-updates    | amd64, armel, i386, powerpc, sparc
 libc6 | 2.15-0ubuntu10     | precise          | amd64, armel, armhf, i386, powerpc
 libc6 | 2.15-0ubuntu10.7   | precise-security | amd64, armel, armhf, i386, powerpc
 libc6 | 2.15-0ubuntu10.7   | precise-updates  | amd64, armel, armhf, i386, powerpc
 libc6 | 2.19-0ubuntu6      | trusty           | amd64, arm64, armhf, i386, powerpc, ppc64el
 libc6 | 2.19-0ubuntu6.3    | trusty-security  | amd64, arm64, armhf, i386, powerpc, ppc64el
 libc6 | 2.19-0ubuntu6.3    | trusty-updates   | amd64, arm64, armhf, i386, powerpc, ppc64el
 libc6 | 2.19-10ubuntu1     | utopic           | amd64, arm64, armhf, i386, powerpc, ppc64el
 libc6 | 2.19-10ubuntu1     | ubuntu-rtm/14.09 | amd64, armhf, i386
```

If you are updating libc6 regularly from the Ubuntu repositories (instead of a PPA or someplace else), then you should be safe and stable.

---

