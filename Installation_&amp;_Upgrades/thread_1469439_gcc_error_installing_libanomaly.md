---
title: "gcc error installing libanomaly"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by spoilingmyself on 2010-05-02
Hello everyone,

While installing a library in C++ [libanomaly]("http://http://www.cs.ucsb.edu/~seclab/projects/libanomaly/index.html") on karmic I found various errors while running "make", related to the gcc compilation, 
In file included from /usr/include/c++/4.4/backward/hash_map:59,
                 from ../../include/anomaly.h:38,
                 from item.cpp:21:
/usr/include/c++/4.4/backward/backward_warning.h:28:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated.
In file included from ../../include/anomaly.h:54,
                 from item.cpp:21:
../../include/libAnomaly/item.h:149: error: 'hash' is not a template
../../include/libAnomaly/item.h:150: error: explicit specialization of non-template 'std::hash'
../../include/libAnomaly/item.h:310: error: extra qualification not allowed
../../include/libAnomaly/item.h:311: error: explicit specialization of non-template 'std::<anonymous struct>'
../../include/libAnomaly/item.h:311: error: an anonymous struct cannot have function members
../../include/libAnomaly/item.h:321: error: abstract declarator 'std::<anonymous struct>' used as declaration
In file included from ../../include/anomaly.h:68,
                 from item.cpp:21:
../../include/libAnomaly/model.h:269: error: ISO C++ forbids declaration of 'hash_map' with no type
../../include/libAnomaly/model.h:269: error: expected ';' before '<' token
In file included from ../../include/anomaly.h:75,
                 from item.cpp:21:
../../include/libAnomaly/profile.h: In member function 'virtual size_t Profile::EvaluationResult::hash_value() const':
../../include/libAnomaly/profile.h:184: error: 'std::hash' is not a template
../../include/libAnomaly/profile.h:186: error: no match for call to '(std::hash) (const char*)'
../../include/libAnomaly/item.h:156: note: candidates are: size_t std::hash::operator()(const Item*) const
make[2]: *** [item.lo] Error 1
make[2]: Leaving directory `/home/neha/Desktop/libanomaly-0.1/src/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/neha/Desktop/libanomaly-0.1/src'
make: *** [all-recursive] Error 1

though configure runs successfully but the config.log file shows errors.

conftest.cc:15: error: 'exit' was not declared in this scope
configure:2425: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "libAnomaly"
| #define PACKAGE_TARNAME "libanomaly"
| #define PACKAGE_VERSION "0.1"
| #define PACKAGE_STRING "libAnomaly 0.1"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "libanomaly"
| #define VERSION "0.1"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| exit (42);
|   ;
|   return 0;
| }
configure:2374: g++ -c -g -O2  conftest.cc >&5
conftest.cc:11: error: 'void std::exit(int)' should have been declared inside 'std'
configure:2380: $? = 1

I think this is due to incompatible versions of the gcc file.
Any suggestions how can I install this?
I appreciate every help. Thanks in advance!

---

### Post by James79 on 2010-05-02
More that likely, the code isn't compatible with the new stricter rules of gcc 4+.

Perhaps contact the authors and ask them what version of gcc they suggest you use. Perhaps they can update their code to be gcc4 compatible.

---

### Post by spoilingmyself on 2010-05-02
> **James79 said:**
> More that likely, the code isn't compatible with the new stricter rules of gcc 4+.

Perhaps contact the authors and ask them what version of gcc they suggest you use. Perhaps they can update their code to be gcc4 compatible.
Is there any way I could fix it myself if there is some software available which helps with this compatibility issue? or if there is some way to install earlier version of gcc to install this software in its original form... Thanks again for the prompt reply!

---

### Post by James79 on 2010-05-03
To my knowledge, there is not. 

Older versions of gcc are available on their site, but I would be careful about installing an older version for fear of screwing up your current install.

Perhaps an older version of Ubuntu in a virtual machine could be of some use?

Baring some C++ skills, I still say your best bet is via the original authors.

---

### Post by ranok on 2012-02-04
I know this is an old thread, but in case anyone else is running into this issue, I've fixed the issues and it now compiles on my Ubuntu box with gcc 4.4.3. You can download the modified source from [**here**]("http://code.jitunleashed.com/libanomaly-0.1-gcc4.tar.gz").

Cheers!
Ranok

---

