---
title: "gcc 4.5.1 installation error  on ubuntu 11.04"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by ravish112 on 2011-08-19
Hi,
 
I was trying to install gcc 4.5.1 on ubuntu 11.04 I got following error:-
 
under /usr/bin/gcc version is 4.5.2
 
/usr/include/unistd.h:275:21: error: two or more data types in declaration specifiers
 
in line #275 of /usr/include/unistd.h
 
we have 
 
#if defined __USE_BSD || defined __USE_XOPEN
# ifndef __socklen_t_defined
typedef __socklen_t socklen_t;
# define __socklen_t_defined
# endif
#endif
 
Could you please help me in this scenario

---

