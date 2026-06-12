---
title: "[SOLVED] Problem during compiling"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by psavva on 2007-05-19
Every time i download source code for a program from Sourceforge or any other place, i can never seem to compile without getting a million errors and warnings.

this is just one example of me trying o compile following step by step instructions and can never get it to work.
I am i doing something wrong or is there a configuration error on my system.

I'm using Ubuntu Fiesty,  installed a few weeks ago :D

Trying to install pwlib

```

./configure

```
All Goes well here i think. This is the output

```

PTLib version is 1.5.2
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
OSTYPE set to linux
OSRELEASE set to 2.6.20-15-386
MACHTYPE set to x86
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking whether byte ordering is bigendian... no
checking if linker accepts --gc-sections... yes
checking if compiler accepts -ffunction-sections... yes
checking if compiler accepts -fdata-sections... yes
checking if compiler accepts -fvtable-gc... no
checking for pthread_create in -lpthread... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking libdc1394/dc1394_control.h usability... no
checking libdc1394/dc1394_control.h presence... no
checking for libdc1394/dc1394_control.h... no
checking libavc1394/avc1394.h usability... no
checking libavc1394/avc1394.h presence... no
checking for libavc1394/avc1394.h... no
checking libdv/dv.h usability... no
checking libdv/dv.h presence... no
checking for libdv/dv.h... no
checking for res_search... no
checking for res_search in -lresolv... yes
checking ldap.h usability... no
checking ldap.h presence... no
checking for ldap.h... no
checking for /usr/local/include/ldap.h... no
checking openssl/ssl.h usability... no
checking openssl/ssl.h presence... no
checking for openssl/ssl.h... no
checking if openssl/ssl.h works with OPENSSL_NO_KRB5... no
checking if /usr/local/openssl/include/openssl/ssl.h works... no
checking if /usr/local/openssl/include/openssl/ssl.h works with OPENSSL_NO_KRB5... no
checking if /usr/local/ssl/include/openssl/ssl.h works... no
checking if /usr/local/ssl/include/openssl/ssl.h works with OPENSSL_NO_KRB5... no
checking expat.h usability... yes
checking expat.h presence... yes
checking for expat.h... yes
checking for XML_ParserCreate in -lexpat... yes
checking SDL/SDL.h usability... yes
checking SDL/SDL.h presence... yes
checking for SDL/SDL.h... yes
checking for SDL_CreateYUVOverlay in -lSDL... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for IPv6 Support... yes
checking linux/videodev.h usability... yes
checking linux/videodev.h presence... yes
checking for linux/videodev.h... yes
checking machine/ioctl_meteor.h usability... no
checking machine/ioctl_meteor.h presence... no
checking for machine/ioctl_meteor.h... no
checking i386/ioctl_meteor.h usability... no
checking i386/ioctl_meteor.h presence... no
checking for i386/ioctl_meteor.h... no
checking dev/ic/bt8xx.h usability... no
checking dev/ic/bt8xx.h presence... no
checking for dev/ic/bt8xx.h... no
checking for swab... yes
checking for dlopen in -ldl... yes
configure: creating ./config.status
config.status: creating make/ptbuildopts.mak
config.status: creating make/ptlib-config
config.status: creating Makefile
config.status: creating include/ptbuildopts.h
config.status: include/ptbuildopts.h is unchanged
psavva@Ubuntu:~/pwlib$ 


```

now for "make", here is where the problems come in

```

psavva@Ubuntu:~/pwlib$ make
make[1]: Entering directory `/home/psavva/pwlib'
set -e; for i in /home/psavva/pwlib; do make -C $i debugdepend debug; done
make[2]: Entering directory `/home/psavva/pwlib'
Created dependencies.
set -e; make -C src/ptlib/unix debugdepend; make -C tools/asnparser debugdepend;
make[3]: Entering directory `/home/psavva/pwlib/src/ptlib/unix'
Created dependencies.
make[3]: Leaving directory `/home/psavva/pwlib/src/ptlib/unix'
make[3]: Entering directory `/home/psavva/pwlib/tools/asnparser'
Created dependencies.
make[3]: Leaving directory `/home/psavva/pwlib/tools/asnparser'
set -e; make -C src/ptlib/unix debug; make -C tools/asnparser debug;
make[3]: Entering directory `/home/psavva/pwlib/src/ptlib/unix'
g++ -DP_LINUX=2.6.20-15-386 -ffunction-sections -fdata-sections -D_REENTRANT -Wall  -fPIC -DP_USE_PRAGMA -g -D_DEBUG -DPMEMORY_CHECK=1 -DPHAS_TEMPLATES -I/home/psavva/pwlib/include/ptlib/unix -I/usr/include/pwlib -I/home/psavva/pwlib/include -fPIC -DP_USE_PRAGMA -DPTRACING=1 -x c++ -c ../../ptclib/asner.cxx -o /home/psavva/pwlib/lib/obj_linux_x86_d/asner.o
/home/psavva/pwlib/include/ptlib/unix/ptlib/../../timer.h:351: error: ISO C++ forbids declaration of &#8216;PTimerList&#8217; with no type
/home/psavva/pwlib/include/ptlib/unix/ptlib/../../timer.h:351: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/home/psavva/pwlib/include/ptlib/unix/ptlib/pprocess.h:181: error: ISO C++ forbids declaration of &#8216;PHouseKeepingThread&#8217; with no type
/home/psavva/pwlib/include/ptlib/unix/ptlib/pprocess.h:181: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/home/psavva/pwlib/include/ptclib/html.h:213: warning: &#8216;class PHTML::Element&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:235: warning: &#8216;class PHTML::HTML&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:240: warning: &#8216;class PHTML::Head&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:247: warning: &#8216;class PHTML::Body&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:254: warning: &#8216;class PHTML::Title&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:265: warning: &#8216;class PHTML::Banner&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:270: warning: &#8216;class PHTML::Division&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:275: warning: &#8216;class PHTML::Heading&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:299: warning: &#8216;class PHTML::BreakLine&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:304: warning: &#8216;class PHTML::Paragraph&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:309: warning: &#8216;class PHTML::PreFormat&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:319: warning: &#8216;class PHTML::HotLink&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:328: warning: &#8216;class PHTML::Target&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:337: warning: &#8216;class PHTML::ImageElement&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:349: warning: &#8216;class PHTML::Image&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:367: warning: &#8216;class PHTML::HRule&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:372: warning: &#8216;class PHTML::Note&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:377: warning: &#8216;class PHTML::Address&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:382: warning: &#8216;class PHTML::BlockQuote&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:387: warning: &#8216;class PHTML::Credit&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:392: warning: &#8216;class PHTML::SetTab&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:401: warning: &#8216;class PHTML::Tab&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:413: warning: &#8216;class PHTML::Bold&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:416: warning: &#8216;class PHTML::Italic&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:419: warning: &#8216;class PHTML::TeleType&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:422: warning: &#8216;class PHTML::Underline&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:425: warning: &#8216;class PHTML::StrikeThrough&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:429: warning: &#8216;class PHTML::Big&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:432: warning: &#8216;class PHTML::Small&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:435: warning: &#8216;class PHTML::Subscript&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:439: warning: &#8216;class PHTML::Superscript&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:443: warning: &#8216;class PHTML::Emphasis&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:446: warning: &#8216;class PHTML::Cite&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:449: warning: &#8216;class PHTML::Strong&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:452: warning: &#8216;class PHTML::Code&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:455: warning: &#8216;class PHTML::Sample&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:458: warning: &#8216;class PHTML::Keyboard&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:461: warning: &#8216;class PHTML::Variable&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:464: warning: &#8216;class PHTML::Definition&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:468: warning: &#8216;class PHTML::Quote&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:471: warning: &#8216;class PHTML::Author&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:474: warning: &#8216;class PHTML::Person&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:477: warning: &#8216;class PHTML::Acronym&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:480: warning: &#8216;class PHTML::Abbrev&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:483: warning: &#8216;class PHTML::InsertedText&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:487: warning: &#8216;class PHTML::DeletedText&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:493: warning: &#8216;class PHTML::SimpleList&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:500: warning: &#8216;class PHTML::BulletList&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:505: warning: &#8216;class PHTML::OrderedList&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:514: warning: &#8216;class PHTML::DefinitionList&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:519: warning: &#8216;class PHTML::ListHeading&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:524: warning: &#8216;class PHTML::ListItem&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:533: warning: &#8216;class PHTML::DefinitionTerm&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:540: warning: &#8216;class PHTML::DefinitionItem&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:552: warning: &#8216;class PHTML::TableStart&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:564: warning: &#8216;class PHTML::TableEnd&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:572: warning: &#8216;class PHTML::TableRow&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:577: warning: &#8216;class PHTML::TableHeader&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:582: warning: &#8216;class PHTML::TableData&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:588: warning: &#8216;class PHTML::Form&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:609: warning: &#8216;class PHTML::FieldElement&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:623: warning: &#8216;class PHTML::Select&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:644: warning: &#8216;class PHTML::Option&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:668: warning: &#8216;class PHTML::FormField&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:683: warning: &#8216;class PHTML::TextArea&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:702: warning: &#8216;class PHTML::InputField&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:715: warning: &#8216;class PHTML::HiddenField&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:728: warning: &#8216;class PHTML::InputText&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:773: warning: &#8216;class PHTML::InputPassword&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:808: warning: &#8216;class PHTML::RadioButton&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:843: warning: &#8216;class PHTML::CheckBox&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:863: warning: &#8216;class PHTML::InputRange&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:878: warning: &#8216;class PHTML::InputFile&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:892: warning: &#8216;class PHTML::InputImage&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:913: warning: &#8216;class PHTML::InputScribble&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:923: warning: &#8216;class PHTML::ResetButton&#8217; has virtual functions but non-virtual destructor
/home/psavva/pwlib/include/ptclib/html.h:946: warning: &#8216;class PHTML::SubmitButton&#8217; has virtual functions but non-virtual destructor
../../ptclib/asner.cxx: In member function &#8216;PString PASN_Choice::GetTagName() const&#8217;:
../../ptclib/asner.cxx:2057: error: &#8216;psprintf&#8217; was not declared in this scope
make[3]: *** [/home/psavva/pwlib/lib/obj_linux_x86_d/asner.o] Error 1
make[3]: Leaving directory `/home/psavva/pwlib/src/ptlib/unix'
make[2]: *** [debug] Error 2
make[2]: Leaving directory `/home/psavva/pwlib'
make[1]: *** [libs] Error 2
make[1]: Leaving directory `/home/psavva/pwlib'
make: *** [debuglibs] Error 2
psavva@Ubuntu:~/pwlib$ 


```

More Info:
I think this might be a little more helpful if you knew the make version i have
make --version
```

psavva@Ubuntu:~/pwlib$ make --version
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu
psavva@Ubuntu:~/pwlib$ 


```

Any hep here would seriously be appreciated. [-o<

---

### Post by xodeus on 2007-05-20
You always have to read the documentation of the project you'll try to compile and meet ALL the dependencies listed there first...

---

### Post by psavva on 2007-05-21
> **xodeus said:**
> You always have to read the documentation of the project you'll try to compile and meet ALL the dependencies listed there first...
I always do, 
I still run into problems even with the most simplest of projects.

If you have a look at my previous post, could you determine or make suggestions how to fix this compile ??

---

### Post by xodeus on 2007-05-22
Maybe is this due to autoconf.
Try to run autoconf in the working directory then continue with ./configure && make && make install

---

### Post by psavva on 2007-05-22
> **xodeus said:**
> Maybe is this due to autoconf.
Try to run autoconf in the working directory then continue with ./configure && make && make install

Nope, No luck, I'm still getting the same errors

[/code]
make[3]: *** [/home/psavva/pwlib/lib/obj_linux_x86_d/asner.o] Error 1
make[3]: Leaving directory `/home/psavva/pwlib/src/ptlib/unix'
make[2]: *** [debug] Error 2
make[2]: Leaving directory `/home/psavva/pwlib'
make[1]: *** [libs] Error 2
make[1]: Leaving directory `/home/psavva/pwlib/src/ptlib/unix'
make: *** [debuglibs] Error 2
[code]
:(

---

### Post by xodeus on 2007-05-23
Thats really strange.
have to back up from this as my experience on making packages from source is poor, but just wanted to help with the knowledge I have...

---

### Post by psavva on 2007-05-24
> **xodeus said:**
> Thats really strange.
have to back up from this as my experience on making packages from source is poor, but just wanted to help with the knowledge I have...
Thanks Anyways,

If anyone else could maybe make any suggestions, i would really appreciate the help

---

