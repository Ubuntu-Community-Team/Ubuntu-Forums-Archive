---
title: "Error: Dependency is not satisfiable: libc6 (&gt;= 2.15)"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by milise2 on 2014-01-26
Hello,

I got this message:

Error: Dependency is not satisfiable: libc6 (>= 2.15)

when trying to install the google music manager here: [https://play.google.com/music/listen#/manager](https://play.google.com/music/listen#/manager)

on Ubuntu lucid lynx..

Can anyone help me out on how to solve this?

Thanks in advance. :)

---

### Post by ajgreeny on 2014-01-26
No we can't, or not on Lucid Lynx, at least.

Lucid Lynx, 10.04, lost support in April last year; 10.04 had a three year support life, not five years as newer LTS versions have.

You will need to update to a newer supported version, 12.04 is probably best at the moment with support till April 2017, I think, but 14.04 will be with us soon, so if you can wait till April you could use that.  However with no support for 10.04 you would be best to upgrade immediately.

These versions use unity DE, which may be great for you, but if after trying it for a time, you don't like it there are other flavours to use; Xubuntu, Kubuntu, Lubuntu, or you can try adding Classic Gnome, which is available for 12.04 and I presume will also be for 14.04.

---

### Post by ian-weisser on 2014-01-26
The server version of Lucid has been tested only with 2.11.1 and lower.
A package requiring a higher version of libc6 is not compatible with Lucid.

While it's possible to use (or compile) untested versions, it's not supported.
If you're willing to haywire your system that much...then you probably shouldn't be using a (obsolete) LTS version of Ubuntu.

```
$ rmadison -u ubuntu libc6
 libc6 | 2.11.1-0ubuntu7    | lucid            | amd64, armel, i386, powerpc, sparc
 libc6 | 2.11.1-0ubuntu7.13 | lucid-updates    | amd64, armel, i386, powerpc
 libc6 | 2.15-0ubuntu10.5   | precise-updates  | amd64, armel, armhf, i386, powerpc
 libc6 | 2.15-0ubuntu20.2   | quantal-updates  | amd64, armel, armhf, i386, powerpc
 libc6 | 2.17-0ubuntu5.1    | raring-updates   | amd64, armhf, i386, powerpc
 libc6 | 2.17-93ubuntu4     | saucy            | amd64, arm64, armhf, i386, powerpc
 libc6 | 2.18-0ubuntu6      | trusty           | amd64, arm64, armhf, i386, powerpc, ppc64el
```

---

