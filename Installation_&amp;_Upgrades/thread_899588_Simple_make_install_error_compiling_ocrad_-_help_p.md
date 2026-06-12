---
title: "Simple make install error compiling ocrad - help please!"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by michael1234 on 2008-08-24
Hello,

I am trying to get the [ocrad]("http://linux.softpedia.com/progDownload/GNU-Ocrad-Download-5269.html") OCR application so I can scan receipts to text. both adept and dpkg can't seem to configure it. So I compiled it manually.

All goes well (./configure and make are good) up until *make install*. At that point, I get this:```
make: [install-info] Error 1 (has no effect)
if test ! -d /usr/local/bin ; then install -d /usr/local/bin ; fi
install -p -m 755 ./ocrad /usr/local/bin/ocrad
root@Precision450:~/Desktop/ocrad-0.16# if test ! -d /usr/local/share/info ; then install -d /usr/local/share/info ; fi
root@Precision450:~/Desktop/ocrad-0.16# install -p -m 644 ./doc/ocrad.info /usr/local/share/info/ocrad.info
root@Precision450:~/Desktop/ocrad-0.16# install-info /usr/local/share/info/ocrad.info /usr/local/share/info/dir
install-info(/usr/local/share/info/ocrad.info): too many arguments
Usage: install-info [<options> ...] [--] <file>
```

I did a test output of make install (the -n switch prints the commands):
```
root@Precision450:~/Desktop/ocrad-0.16# make install -n
if test ! -d /usr/local/share/info ; then install -d /usr/local/share/info ; fi
install -p -m 644 ./doc/ocrad.info /usr/local/share/info/ocrad.info
install-info /usr/local/share/info/ocrad.info /usr/local/share/info/dir
if test ! -d /usr/local/bin ; then install -d /usr/local/bin ; fi
install -p -m 755 ./ocrad /usr/local/bin/ocrad

```

It's obviously the *install-info* line that is screwing up things. I tried running each of these commands one by one from the prompt but I'm just not sure how to hack that line. I RTFM'd, but I just don't quite get it.

There is a thread [here]("http://lists.gnu.org/archive/html/bug-ocrad/2005-11/msg00001.html") that talks about incompatible install-info files. I'm not sure where to go from here. Any ideas?

---

### Post by linux_tech on 2008-08-24
Are you installing it from the repositories?

---

