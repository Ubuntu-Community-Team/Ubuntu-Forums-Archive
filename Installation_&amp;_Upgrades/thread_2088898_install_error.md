---
title: "install error"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by nycap on 2012-11-27
after command sudo make install:

```
2::usrp2>::shared_ptr(const boost::shared_ptr<usrp2::usrp2>&)
/usr/include/boost/smart_ptr/shared_ptr.hpp:164:25: note:   no known conversion for argument 1 from ‘int’ to ‘const boost::shared_ptr<usrp2::usrp2>&’
usrp2.cc:73:23: error: expected type-specifier
usrp2.cc:73:23: error: expected ‘)’
usrp2.cc:74:30: error: no matching function for call to ‘usrp2::usrp_table_entry::usrp_table_entry(std::string&, usrp2::usrp2::sptr&)’
usrp2.cc:74:30: note: candidates are:
usrp2.cc:43:5: note: usrp2::usrp_table_entry::usrp_table_entry(const string&, int)
usrp2.cc:43:5: note:   no known conversion for argument 2 from ‘usrp2::usrp2::sptr {aka boost::shared_ptr<usrp2::usrp2>}’ to ‘int’
usrp2.cc:38:10: note: usrp2::usrp_table_entry::usrp_table_entry(const usrp2::usrp_table_entry&)
usrp2.cc:38:10: note:   candidate expects 1 argument, 2 provided
In file included from /usr/include/boost/shared_ptr.hpp:17:0,
                 from /home/matt/src/gnuradio-3.2.2/usrp2/host/include/usrp2/usrp2.h:22,
                 from usrp2.cc:23:
/usr/include/boost/smart_ptr/shared_ptr.hpp: In instantiation of ‘boost::shared_ptr<T>::shared_ptr(Y*) [with Y = int; T = usrp2::usrp2]’:
usrp2.cc:73:56:   required from here
/usr/include/boost/smart_ptr/shared_ptr.hpp:183:50: error: cannot convert ‘int*’ to ‘usrp2::usrp2*’ in initialization


```

the source compiles but stops here on install.  thanks in advance for any help

---

### Post by wildmanne39 on 2012-11-27
Thread closed. Please do not post duplicates, it dilutes community effort.

---

