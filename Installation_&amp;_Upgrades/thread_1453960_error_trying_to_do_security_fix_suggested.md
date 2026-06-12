---
title: "error trying to do security fix suggested"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by ltoso on 2010-04-14
Hi,
my ubuntu system 9.10 is trying to update erland* packages and giving the following error

Changes for the versions:
1:13.b.1-dfsg-2ubuntu1
1:13.b.1-dfsg-2ubuntu1.1

Version 1:13.b.1-dfsg-2ubuntu1.1: 

  * SECURITY UPDATE: denial of service via Heap-based buffer overflow in
    pcre_compile.c in the Perl-Compatible Regular Expression (PCRE)
    library (LP: #535090)
    - CVE-2008-2371
    - debian/patches/pcre-crash.patch is cherrypicked from upstream commit
      [http://github.com/erlang/otp/commit/bb6370a2](http://github.com/erlang/otp/commit/bb6370a2). The hunk for the
      testsuite does not apply cleanly and is not needed for the fix so was
      stripped. This fix is part of the current upstream OTP release R13B04.


please recommend
Regards
ltoso

---

