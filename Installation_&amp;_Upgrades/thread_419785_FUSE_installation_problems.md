---
title: "FUSE installation problems"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by cygnus81 on 2007-04-23
I tried installing the Fuse Perl module using cpan, in order to use mount an ftp filesystem.
However, when I `make test Fuse` I get:
```

Running make test
rm -f blib/arch/auto/Fuse/Fuse.so
LD_RUN_PATH="" cc  -shared -L/usr/local/lib -pthread -L/usr/local/lib -lfuse -lr t Fuse.o -lpthread  -o blib/arch/auto/Fuse/Fuse.so
chmod 755 blib/arch/auto/Fuse/Fuse.so
PERL_DL_NONLAZY=1 /usr/bin/perl "-Iblib/lib" "-Iblib/arch" test.pl
test/s/mount.....ok 1/3# mounting examples/loopback_t.pl to /tmp/fusemnt-root
# Mounted in 5.1 secs

**#   Failed test 'mount succeeded'**
#   at test/s/mount.t line 27.
# Looks like you failed 1 test of 3.
test/s/mount.....dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 3
        Failed 1/3 tests, 66.67% okay
test/chmod.......not properly mounted
...

```
and from there on its abour 30 "not properly mounted" errors (probably resulting from the first failed test).

Any ideas ?

My uname -a; Linux itamar-desktop 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux

Thanks in advance for any help.

EDIT: I've checked (using module-assistant) and found that I do have the fuse module installed (Version 2.4.2-0ubuntu3+2.6.15-28.53 of fuse-module-2.6.15-28-386).

EDIT: ***Solved !*** All I needed was just to update to fuse 2.6 manually (newbiely I thought its done automatically...) by downloading it from [http://fuse.sourceforge.net/](http://fuse.sourceforge.net/) building and installing it.

---

