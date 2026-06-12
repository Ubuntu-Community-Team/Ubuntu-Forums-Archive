---
title: "Upgrade 8.04 to 10.04 perl dependency problem"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by owainb on 2010-07-13
Hi all,

I am trying to upgrade my Ubuntu 8.04 installation to 10.04 using the alternate CD (mounted ISO image). It is reporting a problem with dependencies on perlapi-5.8.4 and perlapi-5.8.8. As far as I understand it these are virtual packages which are resolved by perl-base which I have version 5.8.8 of. The end of the apt.log produced looks like this:

Investigating libdbi-perl
Package libdbi-perl has broken dep on perlapi-5.8.4
  Considering perl-base 5307 as a solution to libdbi-perl 2
  Removing libdbi-perl rather than change perlapi-5.8.4
Investigating libdbd-mysql-perl
Package libdbd-mysql-perl has broken dep on perlapi-5.8.8
  Considering perl-base 5307 as a solution to libdbd-mysql-perl 0
  Removing libdbd-mysql-perl rather than change perlapi-5.8.8
Investigating mysql-server-5.1
Package mysql-server-5.1 has broken dep on libdbi-perl
  Considering libdbi-perl 2 as a solution to mysql-server-5.1 0
  Holding Back mysql-server-5.1 rather than change libdbi-perl
Investigating mysql-client-5.1
Package mysql-client-5.1 has broken dep on libdbi-perl
  Considering libdbi-perl 2 as a solution to mysql-client-5.1 0
  Holding Back mysql-client-5.1 rather than change libdbi-perl
Investigating mysql-server
Package mysql-server has broken dep on mysql-server-5.1
  Considering mysql-server-5.1 0 as a solution to mysql-server 10000
    Reinst Failed because of libdbi-perl
    Reinst Failed because of mysql-client-5.1

Can anyone suggest what is causing this problem and a possible solution could be.

Thanks

---

### Post by mörgæs on 2010-07-15
A clean install will most likely fix the problem.

---

### Post by owainb on 2010-07-16
Hi mörgæs,

Thanks for your reply. I actually solved the problem yesterday and was going to post the solution today. Removing mysql-server and mysql-client seemed to fix the problem. I can't understand why this is causing a problem on my particular installation because I'm sure most people have these installed. I'm sure I could have done something a bit cleverer and had those packages ignored but the brute-force method seems to have worked just as well.

---

### Post by dino99 on 2010-07-16
maybe you have some custom configs or ppa: before upgrading, clean the system and only use genuine lucid repo

---

