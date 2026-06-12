---
title: "Thrift installation problems on Ubuntu 10.10"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by ssich on 2011-06-28
I am getting the following error during thrift installation. Can anyone  help me please, I am using Ubuntu 10.10. I have successfully install the  pycassa and Cassandra. I checked thrift wiki and other sources too; but  it does not work. Can anyone please help me with these error?


gestion@gestion:~/thrift$ make make  all-recursive make[1]: Entering directory /home/gestion/thrift' Making all in compiler/cpp make[2]: Entering directory/home/gestion/thrift/compiler/cpp' make  all-am make[3]: Entering directory /home/gestion/thrift/compiler/cpp' g++ -DHAVE_CONFIG_H -I. -I../..  -I./src  -Wall -Wno-sign-compare  -Wno-unused -g -O2 -MT libparse_a-thriftl.o -MD -MP -MF  .deps/libparse_a-thriftl.Tpo -c -o libparse_a-thriftl.otest -f 'thriftl.cc' || echo './'thriftl.cc thriftl.ll: In function ‘int yylex()’: thriftl.ll:267: error: ‘ERANGE’ was not declared in this scope thriftl.ll:276: error: ‘ERANGE’ was not declared in this scope thriftl.cc: In function ‘int yy_get_next_buffer()’: thriftl.cc:2808: error: ‘EINTR’ was not declared in this scope make[3]: *** [libparse_a-thriftl.o] Error 1 make[3]: Leaving directory/home/gestion/thrift/compiler/cpp' make[2]: *** [all] Error 2 make[2]: Leaving directory /home/gestion/thrift/compiler/cpp' make[1]: *** [all-recursive] Error 1 make[1]: Leaving directory/home/gestion/thrift' make: *** [all] Error 2

---

### Post by mörgæs on 2011-06-29
Welcome to the fora.

Please post again using code tags around the text.

---

### Post by The Cog on 2011-07-28
I think I just got a successful install using these commands (on 11.04):
> 
apt-get install apt-get install libboost-dev libboost-test1.42-dev libboost-program-options1.42-dev libevent-dev automake libtool flex bison pkg-config g++
apt-get install python-setuptools easy_install
easy_install pycassa
easy_install thrift05



---

