---
title: "Compiling Resin with apache"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by Peque on 2008-01-11
Hey Forum. 

I'm trying to rebuiold my server after an crash. 
The problem is I'm using jsp webpages. 
Normally I have run Apache2 with resin on Ubuntu 6.06 LTS. 
Now I have installed 7.10 after the crash - but when I'm compiling Resin with 
./configure --with-apxs2 
Make && make install 
- that'll run without any problems at all - But no mod_caucho.so is made - and there for there cannot create the connector between Apache and resin. 
Have anybody else experience with that ??? 
The making: 
> 
/usr/local/resin# ./configure --with-apxs2
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for egrep... grep -E
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking sys/epoll.h usability... yes
checking sys/epoll.h presence... yes
checking for sys/epoll.h... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for JAVA_HOME... /opt/jdk1.6.0_03
checking if Java is 64-bit... no
checking for JNI in /opt/jdk1.6.0_03/include/linux ... found
Using JVMTI for class reloading
Using openssl include in ... /usr/include
Using openssl lib in ... /usr/lib
Using openssl libraries in ...  -lssl -lcrypto
configure: creating ./config.status
config.status: creating Makefile
config.status: creating modules/c/src/Makefile
config.status: creating modules/c/src/common/Makefile
config.status: creating modules/c/src/apache1/Makefile
config.status: creating modules/c/src/apache2/Makefile
config.status: creating modules/c/src/resin_os/Makefile
config.status: creating contrib/init.resin
config.status: executing depfiles commands

####################################
/usr/local/resin# make
(cd modules/c/src; make)
make[1]: Entering directory `/usr/local/resin/modules/c/src'
for dir in common   resin_os; do (cd $dir; make); done
make[2]: Entering directory `/usr/local/resin/modules/c/src/common'
gcc -c -I/usr/include -g -O2 -DPOLL -DEPOLL -D_POSIX_PTHREAD_SEMANTICS -DHAS_SOCK_TIMEOUT -DHAS_JVMTI stream.c
gcc -c -I/usr/include -g -O2 -DPOLL -DEPOLL -D_POSIX_PTHREAD_SEMANTICS -DHAS_SOCK_TIMEOUT -DHAS_JVMTI config.c
gcc -c -I/usr/include -g -O2 -DPOLL -DEPOLL -D_POSIX_PTHREAD_SEMANTICS -DHAS_SOCK_TIMEOUT -DHAS_JVMTI memory.c
/usr/bin/ld -r -o common.o stream.o config.o memory.o
/usr/local/resin/libtool --silent --mode=compile gcc -o stream.lo -c -I/usr/include -g -O2 -DPOLL -DEPOLL -D_POSIX_PTHREAD_SEMANTICS -DHAS_SOCK_TIMEOUT -DHAS_JVMTI stream.c
/usr/local/resin/libtool --silent --mode=compile gcc -o config.lo -c -I/usr/include -g -O2 -DPOLL -DEPOLL -D_POSIX_PTHREAD_SEMANTICS -DHAS_SOCK_TIMEOUT -DHAS_JVMTI config.c
/usr/local/resin/libtool --silent --mode=compile gcc -o memory.lo -c -I/usr/include -g -O2 -DPOLL -DEPOLL -D_POSIX_PTHREAD_SEMANTICS -DHAS_SOCK_TIMEOUT -DHAS_JVMTI memory.c
make[2]: Leaving directory `/usr/local/resin/modules/c/src/common'
make[2]: Entering directory `/usr/local/resin/modules/c/src/resin_os'
gcc -g -O2 -DPOLL -DEPOLL -D_POSIX_PTHREAD_SEMANTICS -DHAS_SOCK_TIMEOUT -DHAS_JVMTI  -D_FILE_OFFSET_BITS=64 -DRESIN_HOME=\"/usr/local/resin\" -I/usr/include -I/opt/jdk1.6.0_03/include -I/opt/jdk1.6.0_03/include/linux -I../common -DCPU=\"i386\" -DOS=   -c -o jni_os.o jni_os.c
gcc -g -O2 -DPOLL -DEPOLL -D_POSIX_PTHREAD_SEMANTICS -DHAS_SOCK_TIMEOUT -DHAS_JVMTI  -D_FILE_OFFSET_BITS=64 -DRESIN_HOME=\"/usr/local/resin\" -I/usr/include -I/opt/jdk1.6.0_03/include -I/opt/jdk1.6.0_03/include/linux -I../common -DCPU=\"i386\" -DOS=   -c -o jni_jvmti.o jni_jvmti.c
gcc -g -O2 -DPOLL -DEPOLL -D_POSIX_PTHREAD_SEMANTICS -DHAS_SOCK_TIMEOUT -DHAS_JVMTI  -D_FILE_OFFSET_BITS=64 -DRESIN_HOME=\"/usr/local/resin\" -I/usr/include -I/opt/jdk1.6.0_03/include -I/opt/jdk1.6.0_03/include/linux -I../common -DCPU=\"i386\" -DOS=   -c -o jni_jvmdi.o jni_jvmdi.c
/usr/bin/ld -shared -L/usr/lib -o libresin_os.so jni_os.o jni_jvmti.o jni_jvmdi.o -lpthread -lc
make[2]: Leaving directory `/usr/local/resin/modules/c/src/resin_os'
make[1]: Leaving directory `/usr/local/resin/modules/c/src'

##################################################

/usr/local/resin# make install
(cd modules/c/src; make install)
make[1]: Entering directory `/usr/local/resin/modules/c/src'
for dir in common   resin_os; do (cd $dir; make install); done
make[2]: Entering directory `/usr/local/resin/modules/c/src/common'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/usr/local/resin/modules/c/src/common'
make[2]: Entering directory `/usr/local/resin/modules/c/src/resin_os'
mkdir /usr/local/resin/libexec
cp libresin_os.so /usr/local/resin/libexec
make[2]: Leaving directory `/usr/local/resin/modules/c/src/resin_os'
make[1]: Leaving directory `/usr/local/resin/modules/c/src'
if test /usr/local/resin != `pwd`; then \
          mkdir -p /usr/local/resin/lib; \
          mkdir -p /usr/local/resin/libexec; \
          cp -r libexec/* /usr/local/resin/libexec; \
          cp lib/*.jar /usr/local/resin/lib; \
          mkdir -p /usr/local/resin/bin; \
          cp bin/* /usr/local/resin/bin; \
          mkdir -p /usr/local/resin/webapps; \
          cp -r webapps/* /usr/local/resin/webapps; \
          mkdir -p /usr/local/resin/conf; \
          cp conf/resin.conf /usr/local/resin/conf/resin.conf.orig; \
          cp conf/app-default.xml /usr/local/resin/conf/app-default.xml.orig; \
          if test ! -r /usr/local/resin/conf/resin.conf; then \
            cp conf/resin.conf /usr/local/resin/conf/resin.conf; \
            cp conf/app-default.xml /usr/local/resin/conf/app-default.xml; \
          fi; \
        fi


##################################################
All that I get afterwards is: 
root@atlantis:/usr/local/resin# locate mod_caucho
/usr/local/resin/win32/apache-2.0/mod_caucho.dll
/usr/local/resin/win32/apache-2.2/mod_caucho.dll
/usr/local/resin/modules/c/src/apache1/mod_caucho.c
/usr/local/resin/modules/c/src/apache2/mod_caucho.c



So whart are the options here for making this work ?? 
Is it possible to download the module somewhere ??? Or can anybody upload it so that I can get it ?? 
THanks

---

### Post by Darling on 2008-01-30
I know, it's not easy.
You don't really have to compile resin if you use it standalone. That's just a (couple of) jar file and a startup script.

however, if you want to use Apache as webserver and resin as servlet runner, you need to compile the apache mod_coucho module.
The make script isn't working well under ubuntu. Here's how I did it.

To ./configure you need to install header files in /usr/include/apache2/ and /usr/include/apr-0/ but you can only specify 1 header directory.
 
```
sudo apt-get install apache2-prefork-dev
mkdir /tmp/apache-include
cp /usr/include/apr-0/* /tmp/apache-include/
cp /usr/include/apache2/* /tmp/apache-include/

./configure --with-apache-include=/tmp/apache-include/  --with-apache-libexec=/usr/lib/apache2/modules/ --with-apache-conf=/etc/apache2/httpd.conf
make
sudo make install


```

Resin adds some code in /etc/apache2/httpd.conf. It's better to delete this and use this cleaner approach:
```

sudo touch /etc/apache2/mods-available/caucho.load
sudo chmod a+w /etc/apache2/mods-available/caucho.load
echo "LoadModule caucho_module /usr/lib/apache2/modules/mod_caucho.so" > /etc/apache2/mods-available/caucho.load
sudo a2enmod  caucho
sudo /etc/init.d/apache2 force-reload

```

If I find some time, I'll try to make a resin.deb package. That would be a good test case for learn how to make packages.

---

### Post by Peque on 2008-01-30
Well That's sounds great. 

But what I did was building a "old" 6.06 again compiled on there - saved the module installed 8.08 and well that's that. 
But a resin deb package sounds great! 

I now I can use it as a stand alone - but had some proiblems earlier with the php in Resin - so have from that time - runned it along with apache! 

Per

---

