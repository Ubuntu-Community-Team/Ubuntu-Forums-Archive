---
title: "dpkg-scanpackages command error"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by tianyun16 on 2011-01-10
[SIZE=3]I use the command  dpkg-scanpackages in the terminal .but have a problem .
this is the error message:
Can't locate Dpkg.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/bin/dpkg-scanpackages line 23.
BEGIN failed--compilation aborted at /usr/bin/dpkg-scanpackages line 23.

question: what is the file Dpkg.pm ?
How to solve the problem?

my os is ubuntu10.10 .


thinks 
              
[/SIZE]

---

### Post by tianyun16 on 2011-01-10
[SIZE=4]anybody knows?[/SIZE]

---

### Post by dino99 on 2011-01-10
you should use "apt" not dpkg-scanpackages which is called by "apt"

[http://manpages.ubuntu.com/manpages/maverick/man1/dpkg-scanpackages.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/dpkg-scanpackages.1.html)

---

