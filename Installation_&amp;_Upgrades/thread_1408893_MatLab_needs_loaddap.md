---
title: "MatLab needs loaddap"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by kayve on 2010-02-16
I have the latest 9.10 (8.10) ubuntu

kayve@kayve-laptop:~/Documents/MATLAB/patagonia/data/toilearn$ uname -a
Linux kayve-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux
kayve@kayve-laptop:~/Documents/MATLAB/patagonia/data/toilearn$ 

and I have installed MatLab.. I found out part of MatLab is going out to the web and you need this OpenDAP thing:

[http://opendap.org/download/libdap++.html#3.7.3](http://opendap.org/download/libdap++.html#3.7.3)

There aren't Ubuntu specific instructions and I tried apt-get install alien and alien
[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

I need to 

kayvey,
You actually need to install loaddap:
[http://opendap.org/download/ml-structs.html](http://opendap.org/download/ml-structs.html)
libdap is just a required library.

```
root@kayve-laptop:/home/kayve/src/matlab# script -a ~/apt-gets/libdap-dev-deb-dpkg.makesplat
Script started, file is /root/apt-gets/libdap-dev-deb-dpkg.makesplat
root@kayve-laptop:/home/kayve/src/matlab# date
Tue Feb 16 13:51:19 PST 2010
root@kayve-laptop:/home/kayve/src/matlab# dpkg -i libdap-devel_3.9.3-2_amd64.deb 
(Reading database ... 143700 files and directories currently installed.)
Preparing to replace libdap-devel 3.9.3-2 (using libdap-devel_3.9.3-2_amd64.deb) ...
Unpacking replacement libdap-devel ...
Setting up libdap-devel (3.9.3-2) ...
root@kayve-laptop:/home/kayve/src/matlab# date
Tue Feb 16 13:51:33 PST 2010
root@kayve-laptop:/home/kayve/src/matlab# exit
exit
Script done, file is /root/apt-gets/libdap-dev-deb-dpkg.makesplat
root@kayve-laptop:/home/kayve/src/matlab# 

```

I tried a tarball 

[http://opendap.org/pub/binary/libdap/centos5.2/3.9.3_x86_64/libdap-devel-3.9.3-1.x86_64.rpm](http://opendap.org/pub/binary/libdap/centos5.2/3.9.3_x86_64/libdap-devel-3.9.3-1.x86_64.rpm)

I did ./configure but the Makefiles were not in "Makefile" they had suffixes so "make install" didn't work as per the INSTALL instructions
```

  0. Please skim REQUIREMENTS and NOTES sections of this file
     before reporting problems. Thanks.

  1. Type `./configure' at the system prompt. On some systems you may have
     to type `sh configure'.

  2. Type `make' to build the library, `make check' to run the tests. You
     must have DejaGNU to run `make check.' If you have the CppUnit unit-test
     software, then 'cd unit-tests; make check' will build and run the unit
     tests.

  3. Type `make install' to install the DAP 3.7.3 library. The libraries
     (libdap.a. libdapclient.a and libdapserver.a), their header files and
     the getdap and dap-config utilities install under /usr/local/ in lib,
     include/libdap and bin by default. The deflate utility is installed in
     /usr/local/sbin by default. Use the --prefix option to specify a
     different root directory. For example, './configure
     --prefix=/opt/opendap' would set the build so that the library was
     installed in /opt/opendap/lib, ...

Building from Our SVN Repository
 mv Error.tab.c Error.tab.cc

root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# wc Makefile.am 
 231  840 7797 Makefile.am
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# ls Makefile.*
Makefile.am  Makefile.in
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# wc Makefile.in
 1267  4940 50065 Makefile.in
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3#

Can I just unzip this

[http://opendap.org/pub/source/libdap-3.7.3.tar.gz](http://opendap.org/pub/source/libdap-3.7.3.tar.gz)

    - To build with program instrumentation use `--enable-debug=<level>'
      where <level> is 1 or 2.
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# pwd
/home/kayve/src/matlab/libdap-3.7.3
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# script -a ~/apt-gets/libdap.makesplat
Script started, file is /root/apt-gets/libdap.makesplat
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# date
Tue Feb 16 12:42:25 PST 2010
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
DVR is 
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gawk... (cached) mawk
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# make; make install clean
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# 


libdap-3.7.3/parser-util.cc
libdap-3.7.3/OPeNDAPFile.cc
root@kayve-laptop:/home/kayve/src/matlab# ls
libdap-3.7.3                 stu_control_glnx86.tar  stu_pde_glnx86.tar
libdap-3.7.3.tar             stu_dspblks_glnx86.tar  stu_signal_glnx86.tar
matlab_installer_glnx86.tar  stu_images_glnx86.tar   stu_simulink_glnx86.tar
proof.png                    stu_matlab_glnx86.tar   stu_stats_glnx86.tar
serial_num.png               stu_optim_glnx86.tar    stu_symbolic_glnx86.tar
root@kayve-laptop:/home/kayve/src/matlab# cd libdap-3.7.3
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# ls
aclocal.m4              GSEClause.cc
AISConnect.cc           GSEClause.h
AISConnect.h            gse.lex
AISDatabaseParser.cc    gse_parser.h
AISDatabaseParser.h     gse.tab.cc
AISExceptions.h         gse.tab.h
AISMerge.cc             gse.y
AISMerge.h              HTTPCache.cc
AISResources.cc         HTTPCacheDisconnectedMode.h
AISResources.h          HTTPCache.h
AlarmHandler.h          HTTPCacheInterruptHandler.h
Array.cc                HTTPCacheResponse.h
ArrayGeoConstraint.cc   HTTPConnect.cc
ArrayGeoConstraint.h    HTTPConnect.h
Array.h                 HTTPResponse.h
AttrTable.cc            INSTALL
AttrTable.h             Int16.cc
BaseType.cc             Int16.h
BaseTypeFactory.cc      Int32.cc
BaseTypeFactory.h       Int32.h
BaseType.h              InternalErr.cc
Byte.cc                 InternalErr.h
Byte.h                  lex.ce_expr.cc
ce_expr.lex             lex.das.cc
ce_expr.tab.cc          lex.dds.cc
ce_expr.tab.h           lex.Error.cc
ce_expr.y               lex.gse_.cc
ce_functions.cc         libdap.spec
ce_functions.h          Makefile.am
ce_parser.h             Makefile.in
cgi_util.cc             NEWS
cgi_util.h              ObjectType.h
ChangeLog               OPeNDAPDir.cc
Clause.cc               OPeNDAPDir.h
Clause.h                OPeNDAPFile.cc
conf                    OPeNDAPFile.h
config_dap.h            Operators.h
config.h.in             parser.h
configure               parser-util.cc
configure.ac            PassiveArray.cc
Connect.cc              PassiveArray.h
Connect.h               PassiveByte.cc
ConstraintEvaluator.cc  PassiveByte.h
ConstraintEvaluator.h   PassiveFloat32.cc
Constructor.cc          PassiveFloat32.h
Constructor.h           PassiveFloat64.cc
COPYING                 PassiveFloat64.h
COPYRIGHT_URI           PassiveInt16.cc
COPYRIGHT_W3C           PassiveInt16.h
dap-config.in           PassiveInt32.cc
DAS.cc                  PassiveInt32.h
DAS.h                   PassiveStr.cc
das.lex                 PassiveStr.h
das.tab.cc              PassiveStructure.cc
das.tab.h               PassiveStructure.h
das.y                   PassiveUInt16.cc
DataDDS.cc              PassiveUInt16.h
DataDDS.h               PassiveUInt32.cc
DDS.cc                  PassiveUInt32.h
DDS.h                   PassiveUrl.cc
dds.lex                 PassiveUrl.h
dds.tab.cc              PipeResponse.h
dds.tab.h               RCReader.cc
dds.y                   RCReader.h
DDXExceptions.h         README
DDXParser.cc            README.AIS
DDXParser.h             README.dodsrc
debug.h                 Resource.h
deflate.c               Response.h
dods-datatypes.h        ResponseTooBigErr.cc
dods-datatypes.h.in     ResponseTooBigErr.h
DODSFilter.cc           RValue.cc
DODSFilter.h            RValue.h
dods-limits.h           Sequence.cc
doxy.conf               Sequence.h
doxy_private.conf       SignalHandler.cc
EncodingType.h          SignalHandler.h
Error.cc                SignalHandlerRegisteredErr.h
Error.h                 StdinResponse.h
Error.lex               Str.cc
Error.tab.cc            Str.h
Error.tab.h             Structure.cc
Error.y                 Structure.h
escaping.cc             tests
escaping.h              UInt16.cc
EventHandler.h          UInt16.h
expr.h                  UInt32.cc
Float32.cc              UInt32.h
Float32.h               unit-tests
Float64.cc              Url.cc
Float64.h               Url.h
GeoConstraint.cc        util.cc
GeoConstraint.h         util.h
getdap.cc               util_mit.cc
gl                      util_mit.h
GNU                     VCPP
Grid.cc                 Vector.cc
GridGeoConstraint.cc    Vector.h
GridGeoConstraint.h     xdrutil_ppc.c
Grid.h
root@kayve-laptop:/home/kayve/src/matlab/libdap-3.7.3# 


```

---

