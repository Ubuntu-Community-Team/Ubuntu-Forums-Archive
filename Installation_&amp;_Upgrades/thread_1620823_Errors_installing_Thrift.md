---
title: "Errors installing Thrift"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by dbhatt on 2010-11-13
I'm trying to install Thrift on my Lucid build, and it's giving me errors. I'm still new to Ubuntu so I was wondering if someone could identify what the problem is. 

The bootstrap and the configure work fine. The problems start with the make. 

Here's what I get: 

> 
(CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/bash /home/dharmesh/Programs/thrift-instant-r760184/missing --run autoheader)
rm -f stamp-h1
touch config.hin
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
make  all-recursive
make[1]: Entering directory `/home/dharmesh/Programs/thrift-instant-r760184'
Making all in compiler/cpp
make[2]: Entering directory `/home/dharmesh/Programs/thrift-instant-r760184/compiler/cpp'
Regenerating version.h... cmp: version.h: No such file or directory
Updated.
make  all-am
make[3]: Entering directory `/home/dharmesh/Programs/thrift-instant-r760184/compiler/cpp'
\
     \
    /bin/bash ../../ylwrap `test -f 'src/thrifty.yy' || echo './'`src/thrifty.yy y.tab.c thrifty.cc y.tab.h thrifty.h y.output thrifty.output -- bison -y  -d
updating thrifty.h
g++ -DHAVE_CONFIG_H -I. -I../..    -Wall -I./src -I/usr/include -g -O2 -MT thrift-thrifty.o -MD -MP -MF .deps/thrift-thrifty.Tpo -c -o thrift-thrifty.o `test -f 'thrifty.cc' || echo './'`thrifty.cc
mv -f .deps/thrift-thrifty.Tpo .deps/thrift-thrifty.Po
\
     \
    /bin/bash ../../ylwrap `test -f 'src/thriftl.ll' || echo './'`src/thriftl.ll lex.yy.c thriftl.cc -- flex  
g++ -DHAVE_CONFIG_H -I. -I../..    -Wall -I./src -I/usr/include -g -O2 -MT thrift-thriftl.o -MD -MP -MF .deps/thrift-thriftl.Tpo -c -o thrift-thriftl.o `test -f 'thriftl.cc' || echo './'`thriftl.cc
In file included from ./src/parse/t_const.h:10,
                 from ./src/main.h:11,
                 from thriftl.ll:20:
./src/parse/t_type.h:88: error: ISO C++ forbids declaration of ‘uint8_t’ with no type
./src/parse/t_type.h:88: error: expected ‘;’ before ‘*’ token
./src/parse/t_type.h:92: error: expected ‘;’ before ‘std’
./src/parse/t_type.h:110: error: ‘uint8_t’ has not been declared
./src/parse/t_type.h:149: error: ‘uint8_t’ does not name a type
./src/parse/t_type.h: In member function ‘virtual void t_type::generate_fingerprint()’:
./src/parse/t_type.h:76: error: ‘fingerprint_’ was not declared in this scope
./src/parse/t_type.h: In member function ‘bool t_type::has_fingerprint() const’:
./src/parse/t_type.h:81: error: ‘fingerprint_’ was not declared in this scope
./src/parse/t_type.h: In member function ‘std::string t_type::get_ascii_fingerprint() const’:
./src/parse/t_type.h:94: error: expected initializer before ‘*’ token
./src/parse/t_type.h:96: error: ‘fp’ was not declared in this scope
./src/parse/t_type.h: In constructor ‘t_type::t_type()’:
./src/parse/t_type.h:123: error: ‘fingerprint_’ was not declared in this scope
./src/parse/t_type.h: In constructor ‘t_type::t_type(t_program*)’:
./src/parse/t_type.h:129: error: ‘fingerprint_’ was not declared in this scope
./src/parse/t_type.h: In constructor ‘t_type::t_type(t_program*, std::string)’:
./src/parse/t_type.h:136: error: ‘fingerprint_’ was not declared in this scope
./src/parse/t_type.h: In constructor ‘t_type::t_type(std::string)’:
./src/parse/t_type.h:143: error: ‘fingerprint_’ was not declared in this scope
thriftl.cc: In function ‘int yylex()’:
thriftl.cc:1463: warning: label ‘find_rule’ defined but not used
thriftl.cc: At global scope:
thriftl.cc:2497: warning: ‘void yyunput(int, char*)’ defined but not used
thriftl.cc:3152: warning: ‘int yy_flex_strlen(const char*)’ defined but not used
make[3]: *** [thrift-thriftl.o] Error 1
make[3]: Leaving directory `/home/dharmesh/Programs/thrift-instant-r760184/compiler/cpp'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/dharmesh/Programs/thrift-instant-r760184/compiler/cpp'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dharmesh/Programs/thrift-instant-r760184'
make: *** [all] Error 2


Naturally, the make install is also ridden with errors: 

> 
Making install in compiler/cpp
make[1]: Entering directory `/home/dharmesh/Programs/thrift-instant-r760184/compiler/cpp'
Regenerating version.h... No changes.
make  install-am
make[2]: Entering directory `/home/dharmesh/Programs/thrift-instant-r760184/compiler/cpp'
g++ -DHAVE_CONFIG_H -I. -I../..    -Wall -I./src -I/usr/include -g -O2 -MT thrift-thriftl.o -MD -MP -MF .deps/thrift-thriftl.Tpo -c -o thrift-thriftl.o `test -f 'thriftl.cc' || echo './'`thriftl.cc
In file included from ./src/parse/t_const.h:10,
                 from ./src/main.h:11,
                 from thriftl.ll:20:
./src/parse/t_type.h:88: error: ISO C++ forbids declaration of ‘uint8_t’ with no type
./src/parse/t_type.h:88: error: expected ‘;’ before ‘*’ token
./src/parse/t_type.h:92: error: expected ‘;’ before ‘std’
./src/parse/t_type.h:110: error: ‘uint8_t’ has not been declared
./src/parse/t_type.h:149: error: ‘uint8_t’ does not name a type
./src/parse/t_type.h: In member function ‘virtual void t_type::generate_fingerprint()’:
./src/parse/t_type.h:76: error: ‘fingerprint_’ was not declared in this scope
./src/parse/t_type.h: In member function ‘bool t_type::has_fingerprint() const’:
./src/parse/t_type.h:81: error: ‘fingerprint_’ was not declared in this scope
./src/parse/t_type.h: In member function ‘std::string t_type::get_ascii_fingerprint() const’:
./src/parse/t_type.h:94: error: expected initializer before ‘*’ token
./src/parse/t_type.h:96: error: ‘fp’ was not declared in this scope
./src/parse/t_type.h: In constructor ‘t_type::t_type()’:
./src/parse/t_type.h:123: error: ‘fingerprint_’ was not declared in this scope
./src/parse/t_type.h: In constructor ‘t_type::t_type(t_program*)’:
./src/parse/t_type.h:129: error: ‘fingerprint_’ was not declared in this scope
./src/parse/t_type.h: In constructor ‘t_type::t_type(t_program*, std::string)’:
./src/parse/t_type.h:136: error: ‘fingerprint_’ was not declared in this scope
./src/parse/t_type.h: In constructor ‘t_type::t_type(std::string)’:
./src/parse/t_type.h:143: error: ‘fingerprint_’ was not declared in this scope
thriftl.cc: In function ‘int yylex()’:
thriftl.cc:1463: warning: label ‘find_rule’ defined but not used
thriftl.cc: At global scope:
thriftl.cc:2497: warning: ‘void yyunput(int, char*)’ defined but not used
thriftl.cc:3152: warning: ‘int yy_flex_strlen(const char*)’ defined but not used
make[2]: *** [thrift-thriftl.o] Error 1
make[2]: Leaving directory `/home/dharmesh/Programs/thrift-instant-r760184/compiler/cpp'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/dharmesh/Programs/thrift-instant-r760184/compiler/cpp'
make: *** [install-recursive] Error 1


I was initially missing flex and bison, but I installed them. I also reinstalled almost all the dependencies; an idea I got from here: 

[http://ubuntuforums.org/showthread.php?p=10071940](http://ubuntuforums.org/showthread.php?p=10071940)

It appears like the problem is with the C++ compiler, but I can't be sure. 

Anyone have any suggestion?

---

### Post by Ronrico19 on 2010-12-23
I was having the exact same problem so I tried the svn version which can be downloaded at 

[https://github.com/dreiss/thrift](https://github.com/dreiss/thrift)

After re-running bootstrap and configure, the make seemed to go pretty well and thrift currently seems to be working though I haven't tested it fully yet.

Hopefully this helps,
Nick

---

