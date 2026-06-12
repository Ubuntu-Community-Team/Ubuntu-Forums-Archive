---
title: "two version of a package still exits after removing"
date: 2013-12-18
forum: Installation &amp; Upgrades
---

### Post by bejirond31 on 2013-12-18
I installed  version 0.4.7  of [COLOR=#a52a2a]**[FONT=book antiqua]"ucto"- a unicode toknize[/FONT]**[/COLOR]r in my ubuntu machine and removed it and 
I install version [COLOR=#800000]**0.5.3**[/COLOR] from ubuntu repository. The problem is when I try to compile**[COLOR=#800000] "frog"[/COLOR]** package from the source
the compiler detects older version of "ucto" and the compiler complains that frog requires version of ucto >= 0.4.9 but version 0.4.7 exist in your system. 

I removed by using the command [COLOR=#800000]sudo apt-get purge ucto[/COLOR], [COLOR=#800000]sudo apt-get remove ucto , [/COLOR]
sudo apt-get --purge remove ucto and succesfully removed but when I run 
 [COLOR=#800000]apt-cache show ucto | grep Version [/COLOR]it displays the following[COLOR=#800000][/COLOR]
Version: 0.5.3-2~raring1
Version: 0.4.3-1build1

so how can remove these and able to compile other packages that needs newest version of "ucto"
or how can I force the compiler to use the newest version . please any help ! I am confused
Thanks

---

### Post by philinux on 2013-12-18
What does this command show.

```
apt-cache policy ucto
```

---

### Post by bejirond31 on 2013-12-18
it prints the following 
ucto:
  Installed: (none)
  Candidate: 0.5.3-2~raring1
  Version table:
     0.5.3-2~raring1 0
        500 [http://apt.ticc.uvt.nl/](http://apt.ticc.uvt.nl/) precise/main i386 Packages
     0.4.3-1build1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe i386 Packages

---

### Post by bejirond31 on 2013-12-18
I am still getting trouble !  I am waiting anyone

---

### Post by philinux on 2013-12-18
> **bejirond31 said:**
> it prints the following 
ucto:
  Installed: (none)
  Candidate: 0.5.3-2~raring1
  Version table:
     0.5.3-2~raring1 0
        500 [http://apt.ticc.uvt.nl/](http://apt.ticc.uvt.nl/) precise/main i386 Packages
     0.4.3-1build1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe i386 Packages

Please be patient all users here are volunteers.

The above shows that ucto version 0.5.3-2 is not installed.

If you need it then install it.

```
sudo apt-get install ucto
``` will install 5.3-2 as it says that version is the candidate.

---

### Post by bejirond31 on 2013-12-18
still the compiler complains unable to get newest version (0.5.3)

---

### Post by philinux on 2013-12-18
> **bejirond31 said:**
> still the compiler complains unable to get newest version (0.5.3)

Can you post the full error output from the compiler. 

Don't forget to use code tags.

---

### Post by bejirond31 on 2013-12-18
```
checking for ucto... no
configure: error: Package requirements (ucto >= 0.4.9 ) were not met:

Requested 'ucto >= 0.4.9' but version of ucto is 0.4.7

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ucto_CFLAGS
and ucto_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by bejirond31 on 2013-12-18
```
mesfin@mesfin-VGN-NW270F:~/frog-0.12.13$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... (cached) ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for pid_t... yes
checking for size_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for OpenMP flag of C++ compiler... -fopenmp
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for pkg-config... /usr/bin/pkg-config
checking for icu-config... /usr/bin/icu-config
checking for ICU >= 3.6... yes
checking ICU_CFLAGS... -g -Wall -O2 -Wall -ansi -pedantic -Wshadow -Wpointer-arith -Wmissing-prototypes -Wwrite-strings -Wno-long-long   
checking ICU_CPPSEARCHPATH... -I/usr/include 
checking ICU_CXXFLAGS... -g -Wall -O2 -W -Wall -ansi -pedantic -Wpointer-arith -Wwrite-strings -Wno-long-long   
checking ICU_LIBS... -licui18n -licuuc -licudata 
checking ICU_LIBPATH... -L/usr/lib 
checking ICU_IOLIBS...  -licuio 
checking for timbl... yes
checking for timblserver... yes
checking for mbt... yes
configure: pkg-config search path: :/usr/local/lib/pkgconfig:/usr/local/lib/pkgconfig:/usr/local/lib/pkgconfig:/usr/local/lib/pkgconfig 
checking for folia... yes
checking for ucto... no
configure: error: Package requirements (ucto >= 0.4.9 ) were not met:

Requested 'ucto >= 0.4.9' but version of ucto is 0.4.7

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ucto_CFLAGS
and ucto_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

if it gives you some hint , this is the whole out put of the compiler.

---

### Post by philinux on 2013-12-18
Odd. What does this reveal.

```
which ucto
```

---

### Post by bejirond31 on 2013-12-18
/usr/bin/ucto

---

### Post by bejirond31 on 2013-12-18
```
/usr/bin/ucto
```

---

### Post by philinux on 2013-12-18
How did you install 0.4.7 it still seems to think that version is active?

---

### Post by bejirond31 on 2013-12-18
I am not  quite sure how I installed it.  But, I was trying many ucto's version and 
I guess I installed it from the repository. it is surprise for me from where [COLOR=#800000]0.4.7 version[/COLOR] comes there is no any installed
version of it.

---

### Post by bejirond31 on 2013-12-20
still I am waiting solution, anyone please

---

### Post by steeldriver on 2013-12-20
what does

```
pkg-config --variable=libdir --modversion ucto
```

say? That should indicate where the configure command is finding the older version

---

### Post by bejirond31 on 2013-12-20
0.4.7
/usr/local/lib


This is the out put of the above command and when I > /usr/local/lib /ls 
 >  the following displayed 
libmbt.a   libmbt.so.1      libucto.la    libucto.so.1.0.0  python3.2
libmbt.la  libmbt.so.1.0.0  libucto.so    pkgconfig
libmbt.so  libucto.a        libucto.so.1  python2.7

what shall I do next

---

### Post by steeldriver on 2013-12-20
OK so as suspected you have a 'local' version of ucto - probably compiled/installed from source

Depending where you got the source from, there may be an option to 'make uninstall' it. Otherwise you should be able to tell the pkg-config program to search the standard /usr/lib ahead of /usr/local/lib when looking for .pc files by exporting a 

```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig/
```

before running the ./configure - if that doesn't work, then you can look in your /usr/local/lib/pkgconfig/ directory for a file called ucto.pc and rename it e.g.

```
sudo mv /usr/local/lib/pkgconfig/ucto.pc /usr/local/lib/pkgconfig/ucto.pc.ignore
```

Good luck!

---

### Post by ranger1021994 on 2013-12-20
Try using synaptic to do this work
1. Open synaptic
2. Locate ucto
3. Remove it by selecting Uninstall completely
4. Select the package and click on "Package" option and select Force version and select the latest version

--------------------------------------------------------------------------------------------------------------------------------------------
Or using command line you can try this
> sudo apt-get purge ucto
then
> sudo find / -name ucto*
then delete all files listen by the "find" command
and then
> sudo apt-get clean then
> sudo apt-get install ucto

---

### Post by bejirond31 on 2013-12-20
really I thank you ! solved !!

---

### Post by bejirond31 on 2013-12-20
_[**[COLOR=#000000]steeldriver[/COLOR]**]("http://ubuntuforums.org/member.php?u=1627500")_ I thank you ! it works as you directed me !

---

### Post by bejirond31 on 2013-12-21
I am back again with another problem- with the same issue. I properly configure with
out problem but when I typed ```
make
``` the compiler complains. the following are some of the out put of it
```
/usr/include/c++/4.6/bits/ostream.tcc:121:5: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__streambuf_type* {aka std::basic_streambuf<char>*}&#8217;
/usr/include/unicode/ustream.h:46:35: note: std::ostream& icu_48::operator<<(std::ostream&, const icu_48::UnicodeString&)
/usr/include/unicode/ustream.h:46:35: note:   no known conversion for argument 2 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;const icu_48::UnicodeString&&#8217;
/usr/include/c++/4.6/bits/basic_string.h:2693:5: note: template<class _CharT, class _Traits, class _Alloc> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const std::basic_string<_CharT, _Traits, _Alloc>&)
/usr/include/c++/4.6/ostream:451:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, _CharT)
/usr/include/c++/4.6/ostream:456:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, char)
/usr/include/c++/4.6/ostream:462:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, char)
/usr/include/c++/4.6/ostream:468:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, signed char)
/usr/include/c++/4.6/ostream:473:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, unsigned char)
/usr/include/c++/4.6/ostream:493:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const _CharT*)
/usr/include/c++/4.6/bits/ostream.tcc:323:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const char*)
/usr/include/c++/4.6/ostream:510:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const char*)
/usr/include/c++/4.6/ostream:523:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const signed char*)
/usr/include/c++/4.6/ostream:528:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const unsigned char*)
/usr/include/libfolia/foliautils.h:215:24: note: std::ostream& folia::operator<<(std::ostream&, const folia::AnnotationType::AnnotationType&)
/usr/include/libfolia/foliautils.h:215:24: note:   no known conversion for argument 2 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;const folia::AnnotationType::AnnotationType&&#8217;
mbma_mod.cxx:252:10: note: std::ostream& operator<<(std::ostream&, const std::vector<waStruct>&)
mbma_mod.cxx:252:10: note:   no known conversion for argument 2 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;const std::vector<waStruct>&&#8217;
mbma_mod.cxx:247:10: note: std::ostream& operator<<(std::ostream&, const waStruct&)
mbma_mod.cxx:247:10: note:   no known conversion for argument 2 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;const waStruct&&#8217;
/usr/include/timbl/Matrices.h:110:22: note: template<class T> std::ostream& operator<<(std::ostream&, const SparseSymetricMatrix<T>&)
mbma_mod.cxx:487:56: error: no match for &#8216;operator<<&#8217; in &#8216;std::operator<< [with _Traits = std::char_traits<char>]((* & std::operator<< [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]((* & std::operator<< [with _Traits = std::char_traits<char>]((* & std::cout), ((const char*)"inflectAndAffix: "))), (*(const std::basic_string<char>*)(& inflect)))), ((const char*)" - ")) << morphemes&#8217;
mbma_mod.cxx:487:56: note: candidates are:
/usr/include/c++/4.6/ostream:110:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__ostream_type& (*)(std::basic_ostream<_CharT, _Traits>::__ostream_type&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:110:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__ostream_type& (*)(std::basic_ostream<char>::__ostream_type&) {aka std::basic_ostream<char>& (*)(std::basic_ostream<char>&)}&#8217;
/usr/include/c++/4.6/ostream:119:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__ios_type& (*)(std::basic_ostream<_CharT, _Traits>::__ios_type&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>, std::basic_ostream<_CharT, _Traits>::__ios_type = std::basic_ios<char>]
/usr/include/c++/4.6/ostream:119:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__ios_type& (*)(std::basic_ostream<char>::__ios_type&) {aka std::basic_ios<char>& (*)(std::basic_ios<char>&)}&#8217;
/usr/include/c++/4.6/ostream:129:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::ios_base& (*)(std::ios_base&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:129:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;std::ios_base& (*)(std::ios_base&)&#8217;
/usr/include/c++/4.6/ostream:167:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:167:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;long int&#8217;
/usr/include/c++/4.6/ostream:171:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:171:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;long unsigned int&#8217;
/usr/include/c++/4.6/ostream:175:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(bool) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:175:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;bool&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:93:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(short int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.6/bits/ostream.tcc:93:5: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;short int&#8217;
/usr/include/c++/4.6/ostream:182:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(short unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:182:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;short unsigned int&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:107:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.6/bits/ostream.tcc:107:5: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;int&#8217;
/usr/include/c++/4.6/ostream:193:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:193:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;unsigned int&#8217;
/usr/include/c++/4.6/ostream:202:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long long int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:202:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;long long int&#8217;
/usr/include/c++/4.6/ostream:206:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:206:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;long long unsigned int&#8217;
/usr/include/c++/4.6/ostream:211:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(double) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:211:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;double&#8217;
/usr/include/c++/4.6/ostream:215:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(float) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:215:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;float&#8217;
/usr/include/c++/4.6/ostream:223:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long double) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:223:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;long double&#8217;
/usr/include/c++/4.6/ostream:227:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(const void*) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:227:7: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;const void*&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:121:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__streambuf_type*) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__streambuf_type = std::basic_streambuf<char>]
/usr/include/c++/4.6/bits/ostream.tcc:121:5: note:   no known conversion for argument 1 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__streambuf_type* {aka std::basic_streambuf<char>*}&#8217;
/usr/include/unicode/ustream.h:46:35: note: std::ostream& icu_48::operator<<(std::ostream&, const icu_48::UnicodeString&)
/usr/include/unicode/ustream.h:46:35: note:   no known conversion for argument 2 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;const icu_48::UnicodeString&&#8217;
/usr/include/c++/4.6/bits/basic_string.h:2693:5: note: template<class _CharT, class _Traits, class _Alloc> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const std::basic_string<_CharT, _Traits, _Alloc>&)
/usr/include/c++/4.6/ostream:451:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, _CharT)
/usr/include/c++/4.6/ostream:456:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, char)
/usr/include/c++/4.6/ostream:462:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, char)
/usr/include/c++/4.6/ostream:468:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, signed char)
/usr/include/c++/4.6/ostream:473:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, unsigned char)
/usr/include/c++/4.6/ostream:493:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const _CharT*)
/usr/include/c++/4.6/bits/ostream.tcc:323:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const char*)
/usr/include/c++/4.6/ostream:510:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const char*)
/usr/include/c++/4.6/ostream:523:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const signed char*)
/usr/include/c++/4.6/ostream:528:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const unsigned char*)
/usr/include/libfolia/foliautils.h:215:24: note: std::ostream& folia::operator<<(std::ostream&, const folia::AnnotationType::AnnotationType&)
/usr/include/libfolia/foliautils.h:215:24: note:   no known conversion for argument 2 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;const folia::AnnotationType::AnnotationType&&#8217;
mbma_mod.cxx:252:10: note: std::ostream& operator<<(std::ostream&, const std::vector<waStruct>&)
mbma_mod.cxx:252:10: note:   no known conversion for argument 2 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;const std::vector<waStruct>&&#8217;
mbma_mod.cxx:247:10: note: std::ostream& operator<<(std::ostream&, const waStruct&)
mbma_mod.cxx:247:10: note:   no known conversion for argument 2 from &#8216;std::vector<std::basic_string<char> >&#8217; to &#8216;const waStruct&&#8217;
/usr/include/timbl/Matrices.h:110:22: note: template<class T> std::ostream& operator<<(std::ostream&, const SparseSymetricMatrix<T>&)
mbma_mod.cxx: In member function &#8216;void Mbma::execute(const icu_48::UnicodeString&, const std::vector<std::basic_string<char> >&)&#8217;:
mbma_mod.cxx:523:48: error: &#8216;split_at&#8217; was not declared in this scope
mbma_mod.cxx:523:48: note: suggested alternative:
/usr/include/ticcutils/StringOps.h:48:10: note:   &#8216;TiCC::split_at&#8217;
mbma_mod.cxx: In member function &#8216;void Mbma::addMorph(folia::FoliaElement*, const std::vector<std::basic_string<char> >&)&#8217;:
mbma_mod.cxx:582:41: error: call of overloaded &#8216;toString(int&)&#8217; is ambiguous
mbma_mod.cxx:582:41: note: candidates are:
/usr/include/libfolia/foliautils.h:202:15: note: std::string folia::toString(const folia::AnnotationType::AnnotationType&) <near match>
/usr/include/libfolia/foliautils.h:202:15: note:   no known conversion for argument 1 from &#8216;int&#8217; to &#8216;const folia::AnnotationType::AnnotationType&&#8217;
/usr/include/libfolia/foliautils.h:207:15: note: std::string folia::toString(const folia::ElementType&) <near match>
/usr/include/libfolia/foliautils.h:207:15: note:   no known conversion for argument 1 from &#8216;int&#8217; to &#8216;const folia::ElementType&&#8217;
mbma_mod.cxx: In member function &#8216;void Mbma::postprocess(folia::FoliaElement*)&#8217;:
mbma_mod.cxx:598:28: error: no match for &#8216;operator<<&#8217; in &#8216;std::cout << it.__gnu_cxx::__normal_iterator<_Iterator, _Container>::operator-> [with _Iterator = const MBMAana*, _Container = std::vector<MBMAana>, __gnu_cxx::__normal_iterator<_Iterator, _Container>::pointer = const MBMAana*]()->MBMAana::getMorph()&#8217;
mbma_mod.cxx:598:28: note: candidates are:
/usr/include/c++/4.6/ostream:110:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__ostream_type& (*)(std::basic_ostream<_CharT, _Traits>::__ostream_type&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:110:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__ostream_type& (*)(std::basic_ostream<char>::__ostream_type&) {aka std::basic_ostream<char>& (*)(std::basic_ostream<char>&)}&#8217;
/usr/include/c++/4.6/ostream:119:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__ios_type& (*)(std::basic_ostream<_CharT, _Traits>::__ios_type&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>, std::basic_ostream<_CharT, _Traits>::__ios_type = std::basic_ios<char>]
/usr/include/c++/4.6/ostream:119:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__ios_type& (*)(std::basic_ostream<char>::__ios_type&) {aka std::basic_ios<char>& (*)(std::basic_ios<char>&)}&#8217;
/usr/include/c++/4.6/ostream:129:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::ios_base& (*)(std::ios_base&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:129:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::ios_base& (*)(std::ios_base&)&#8217;
/usr/include/c++/4.6/ostream:167:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:167:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long int&#8217;
/usr/include/c++/4.6/ostream:171:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:171:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long unsigned int&#8217;
/usr/include/c++/4.6/ostream:175:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(bool) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:175:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;bool&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:93:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(short int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.6/bits/ostream.tcc:93:5: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;short int&#8217;
/usr/include/c++/4.6/ostream:182:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(short unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:182:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;short unsigned int&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:107:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.6/bits/ostream.tcc:107:5: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;int&#8217;
/usr/include/c++/4.6/ostream:193:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:193:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;unsigned int&#8217;
/usr/include/c++/4.6/ostream:202:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long long int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:202:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long long int&#8217;
/usr/include/c++/4.6/ostream:206:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:206:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long long unsigned int&#8217;
/usr/include/c++/4.6/ostream:211:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(double) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:211:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;double&#8217;
/usr/include/c++/4.6/ostream:215:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(float) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:215:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;float&#8217;
/usr/include/c++/4.6/ostream:223:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long double) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:223:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long double&#8217;
/usr/include/c++/4.6/ostream:227:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(const void*) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:227:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const void*&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:121:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__streambuf_type*) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__streambuf_type = std::basic_streambuf<char>]
/usr/include/c++/4.6/bits/ostream.tcc:121:5: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__streambuf_type* {aka std::basic_streambuf<char>*}&#8217;
/usr/include/unicode/ustream.h:46:35: note: std::ostream& icu_48::operator<<(std::ostream&, const icu_48::UnicodeString&)
/usr/include/unicode/ustream.h:46:35: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const icu_48::UnicodeString&&#8217;
/usr/include/c++/4.6/bits/basic_string.h:2693:5: note: template<class _CharT, class _Traits, class _Alloc> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const std::basic_string<_CharT, _Traits, _Alloc>&)
/usr/include/c++/4.6/ostream:451:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, _CharT)
/usr/include/c++/4.6/ostream:456:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, char)
/usr/include/c++/4.6/ostream:462:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, char)
/usr/include/c++/4.6/ostream:468:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, signed char)
/usr/include/c++/4.6/ostream:473:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, unsigned char)
/usr/include/c++/4.6/ostream:493:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const _CharT*)
/usr/include/c++/4.6/bits/ostream.tcc:323:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const char*)
/usr/include/c++/4.6/ostream:510:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const char*)
/usr/include/c++/4.6/ostream:523:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const signed char*)
/usr/include/c++/4.6/ostream:528:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const unsigned char*)
/usr/include/libfolia/foliautils.h:215:24: note: std::ostream& folia::operator<<(std::ostream&, const folia::AnnotationType::AnnotationType&)
/usr/include/libfolia/foliautils.h:215:24: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const folia::AnnotationType::AnnotationType&&#8217;
mbma_mod.cxx:252:10: note: std::ostream& operator<<(std::ostream&, const std::vector<waStruct>&)
mbma_mod.cxx:252:10: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const std::vector<waStruct>&&#8217;
mbma_mod.cxx:247:10: note: std::ostream& operator<<(std::ostream&, const waStruct&)
mbma_mod.cxx:247:10: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const waStruct&&#8217;
/usr/include/timbl/Matrices.h:110:22: note: template<class T> std::ostream& operator<<(std::ostream&, const SparseSymetricMatrix<T>&)
mbma_mod.cxx:635:69: error: no match for &#8216;operator<<&#8217; in &#8216;std::operator<< [with _Traits = std::char_traits<char>]((* &(& std::operator<< [with _Traits = std::char_traits<char>]((* & std::cout), ((const char*)"\011match #")))->std::basic_ostream<_CharT, _Traits>::operator<< [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>](p)), ((const char*)" : ")) << (&((Mbma*)this)->Mbma::analysis.std::vector<_Tp, _Alloc>::operator[] [with _Tp = MBMAana, _Alloc = std::allocator<MBMAana>, std::vector<_Tp, _Alloc>::reference = MBMAana&, std::vector<_Tp, _Alloc>::size_type = unsigned int](matches.std::vector<_Tp, _Alloc>::operator[] [with _Tp = unsigned int, _Alloc = std::allocator<unsigned int>, std::vector<_Tp, _Alloc>::reference = unsigned int&, std::vector<_Tp, _Alloc>::size_type = unsigned int](p)))->MBMAana::getMorph()&#8217;
mbma_mod.cxx:635:69: note: candidates are:
/usr/include/c++/4.6/ostream:110:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__ostream_type& (*)(std::basic_ostream<_CharT, _Traits>::__ostream_type&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:110:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__ostream_type& (*)(std::basic_ostream<char>::__ostream_type&) {aka std::basic_ostream<char>& (*)(std::basic_ostream<char>&)}&#8217;
/usr/include/c++/4.6/ostream:119:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__ios_type& (*)(std::basic_ostream<_CharT, _Traits>::__ios_type&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>, std::basic_ostream<_CharT, _Traits>::__ios_type = std::basic_ios<char>]
/usr/include/c++/4.6/ostream:119:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__ios_type& (*)(std::basic_ostream<char>::__ios_type&) {aka std::basic_ios<char>& (*)(std::basic_ios<char>&)}&#8217;
/usr/include/c++/4.6/ostream:129:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::ios_base& (*)(std::ios_base&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:129:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::ios_base& (*)(std::ios_base&)&#8217;
/usr/include/c++/4.6/ostream:167:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:167:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long int&#8217;
/usr/include/c++/4.6/ostream:171:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:171:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long unsigned int&#8217;
/usr/include/c++/4.6/ostream:175:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(bool) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:175:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;bool&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:93:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(short int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.6/bits/ostream.tcc:93:5: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;short int&#8217;
/usr/include/c++/4.6/ostream:182:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(short unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:182:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;short unsigned int&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:107:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.6/bits/ostream.tcc:107:5: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;int&#8217;
/usr/include/c++/4.6/ostream:193:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:193:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;unsigned int&#8217;
/usr/include/c++/4.6/ostream:202:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long long int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:202:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long long int&#8217;
/usr/include/c++/4.6/ostream:206:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:206:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long long unsigned int&#8217;
/usr/include/c++/4.6/ostream:211:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(double) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:211:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;double&#8217;
/usr/include/c++/4.6/ostream:215:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(float) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:215:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;float&#8217;
/usr/include/c++/4.6/ostream:223:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long double) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:223:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long double&#8217;
/usr/include/c++/4.6/ostream:227:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(const void*) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:227:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const void*&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:121:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__streambuf_type*) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__streambuf_type = std::basic_streambuf<char>]
/usr/include/c++/4.6/bits/ostream.tcc:121:5: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__streambuf_type* {aka std::basic_streambuf<char>*}&#8217;
/usr/include/unicode/ustream.h:46:35: note: std::ostream& icu_48::operator<<(std::ostream&, const icu_48::UnicodeString&)
/usr/include/unicode/ustream.h:46:35: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const icu_48::UnicodeString&&#8217;
/usr/include/c++/4.6/bits/basic_string.h:2693:5: note: template<class _CharT, class _Traits, class _Alloc> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const std::basic_string<_CharT, _Traits, _Alloc>&)
/usr/include/c++/4.6/ostream:451:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, _CharT)
/usr/include/c++/4.6/ostream:456:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, char)
/usr/include/c++/4.6/ostream:462:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, char)
/usr/include/c++/4.6/ostream:468:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, signed char)
/usr/include/c++/4.6/ostream:473:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, unsigned char)
/usr/include/c++/4.6/ostream:493:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const _CharT*)
/usr/include/c++/4.6/bits/ostream.tcc:323:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const char*)
/usr/include/c++/4.6/ostream:510:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const char*)
/usr/include/c++/4.6/ostream:523:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const signed char*)
/usr/include/c++/4.6/ostream:528:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const unsigned char*)
/usr/include/libfolia/foliautils.h:215:24: note: std::ostream& folia::operator<<(std::ostream&, const folia::AnnotationType::AnnotationType&)
/usr/include/libfolia/foliautils.h:215:24: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const folia::AnnotationType::AnnotationType&&#8217;
mbma_mod.cxx:252:10: note: std::ostream& operator<<(std::ostream&, const std::vector<waStruct>&)
mbma_mod.cxx:252:10: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const std::vector<waStruct>&&#8217;
mbma_mod.cxx:247:10: note: std::ostream& operator<<(std::ostream&, const waStruct&)
mbma_mod.cxx:247:10: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const waStruct&&#8217;
/usr/include/timbl/Matrices.h:110:22: note: template<class T> std::ostream& operator<<(std::ostream&, const SparseSymetricMatrix<T>&)
mbma_mod.cxx: In function &#8216;std::ostream& operator<<(std::ostream&, const MBMAana&)&#8217;:
mbma_mod.cxx:770:33: error: no match for &#8216;operator<<&#8217; in &#8216;std::operator<< [with _Traits = std::char_traits<char>]((* & std::operator<< [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]((* & std::operator<< [with _Traits = std::char_traits<char>]((* & std::operator<< [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]((* & os), (* & a.MBMAana::tag))), ((const char*)" "))), (* & a.MBMAana::infl))), ((const char*)" >>>> ")) << a.MBMAana::morphemes&#8217;
mbma_mod.cxx:770:33: note: candidates are:
/usr/include/c++/4.6/ostream:110:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__ostream_type& (*)(std::basic_ostream<_CharT, _Traits>::__ostream_type&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:110:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__ostream_type& (*)(std::basic_ostream<char>::__ostream_type&) {aka std::basic_ostream<char>& (*)(std::basic_ostream<char>&)}&#8217;
/usr/include/c++/4.6/ostream:119:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__ios_type& (*)(std::basic_ostream<_CharT, _Traits>::__ios_type&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>, std::basic_ostream<_CharT, _Traits>::__ios_type = std::basic_ios<char>]
/usr/include/c++/4.6/ostream:119:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__ios_type& (*)(std::basic_ostream<char>::__ios_type&) {aka std::basic_ios<char>& (*)(std::basic_ios<char>&)}&#8217;
/usr/include/c++/4.6/ostream:129:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::ios_base& (*)(std::ios_base&)) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:129:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::ios_base& (*)(std::ios_base&)&#8217;
/usr/include/c++/4.6/ostream:167:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:167:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long int&#8217;
/usr/include/c++/4.6/ostream:171:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:171:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long unsigned int&#8217;
/usr/include/c++/4.6/ostream:175:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(bool) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:175:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;bool&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:93:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(short int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.6/bits/ostream.tcc:93:5: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;short int&#8217;
/usr/include/c++/4.6/ostream:182:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(short unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:182:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;short unsigned int&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:107:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.6/bits/ostream.tcc:107:5: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;int&#8217;
/usr/include/c++/4.6/ostream:193:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:193:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;unsigned int&#8217;
/usr/include/c++/4.6/ostream:202:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long long int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:202:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long long int&#8217;
/usr/include/c++/4.6/ostream:206:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:206:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long long unsigned int&#8217;
/usr/include/c++/4.6/ostream:211:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(double) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:211:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;double&#8217;
/usr/include/c++/4.6/ostream:215:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(float) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:215:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;float&#8217;
/usr/include/c++/4.6/ostream:223:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(long double) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:223:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;long double&#8217;
/usr/include/c++/4.6/ostream:227:7: note: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(const void*) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
/usr/include/c++/4.6/ostream:227:7: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const void*&#8217;
/usr/include/c++/4.6/bits/ostream.tcc:121:5: note: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__streambuf_type*) [with _CharT = char, _Traits = std::char_traits<char>, std::basic_ostream<_CharT, _Traits>::__streambuf_type = std::basic_streambuf<char>]
/usr/include/c++/4.6/bits/ostream.tcc:121:5: note:   no known conversion for argument 1 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;std::basic_ostream<char>::__streambuf_type* {aka std::basic_streambuf<char>*}&#8217;
/usr/include/unicode/ustream.h:46:35: note: std::ostream& icu_48::operator<<(std::ostream&, const icu_48::UnicodeString&)
/usr/include/unicode/ustream.h:46:35: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const icu_48::UnicodeString&&#8217;
/usr/include/c++/4.6/bits/basic_string.h:2693:5: note: template<class _CharT, class _Traits, class _Alloc> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const std::basic_string<_CharT, _Traits, _Alloc>&)
/usr/include/c++/4.6/ostream:451:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, _CharT)
/usr/include/c++/4.6/ostream:456:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, char)
/usr/include/c++/4.6/ostream:462:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, char)
/usr/include/c++/4.6/ostream:468:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, signed char)
/usr/include/c++/4.6/ostream:473:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, unsigned char)
/usr/include/c++/4.6/ostream:493:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const _CharT*)
/usr/include/c++/4.6/bits/ostream.tcc:323:5: note: template<class _CharT, class _Traits> std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const char*)
/usr/include/c++/4.6/ostream:510:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const char*)
/usr/include/c++/4.6/ostream:523:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const signed char*)
/usr/include/c++/4.6/ostream:528:5: note: template<class _Traits> std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const unsigned char*)
/usr/include/libfolia/foliautils.h:215:24: note: std::ostream& folia::operator<<(std::ostream&, const folia::AnnotationType::AnnotationType&)
/usr/include/libfolia/foliautils.h:215:24: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const folia::AnnotationType::AnnotationType&&#8217;
mbma_mod.cxx:252:10: note: std::ostream& operator<<(std::ostream&, const std::vector<waStruct>&)
mbma_mod.cxx:252:10: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const std::vector<waStruct>&&#8217;
mbma_mod.cxx:247:10: note: std::ostream& operator<<(std::ostream&, const waStruct&)
mbma_mod.cxx:247:10: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const waStruct&&#8217;
mbma_mod.cxx:768:10: note: std::ostream& operator<<(std::ostream&, const MBMAana&)
mbma_mod.cxx:768:10: note:   no known conversion for argument 2 from &#8216;const std::vector<std::basic_string<char> >&#8217; to &#8216;const MBMAana&&#8217;
/usr/include/timbl/Matrices.h:110:22: note: template<class T> std::ostream& operator<<(std::ostream&, const SparseSymetricMatrix<T>&)
make[2]: *** [mbma_mod.o] Error 1
make[2]: Leaving directory `/home/mesfin/frog-0.12.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mesfin/frog-0.12.8'
make: *** [all] Error 2


```
the error are too long . I am trying to install the package called "frog-0.12.8" I tried the latest version of but
failed. please any hint to solve my problem.

---

### Post by steeldriver on 2013-12-21
That looks like something more basically messed up with your whole build system - not specifically related to the package you are trying to compile

What are your versions of g++ and make?

```

g++ --version

make --version

```

---

### Post by bejirond31 on 2013-12-21
the version of g++ is > [COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]g++ (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3[/SIZE][/FONT][/COLOR] 
and the version of make is >  GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This program built for i686-pc-linux-gnu 

---

### Post by steeldriver on 2013-12-21
Hmm... that looks OK, I think - fwiw I was able to build frog-0.12.8 on 12.04.3 with gcc-4.6.4 after building and installing the following dependencies 

```

libfolia-0.8  mbt-3.2.7  mbtserver-0.5  timbl-6.4.2  timblserver-1.4  ucto-0.5.1

```

It *might* be worth doing

```

make clean

./configure 

make

```

just in case there's other "stuff" from the earlier compile attempts - add ./configure options as appropriate (I actually did ./configure --prefix=/usr/local)

---

### Post by bejirond31 on 2013-12-21
I will try to remove all other versions of packages and install what you tried  and I will let you know !
Thank you again

---

### Post by bejirond31 on 2013-12-22
I spent almost a day but I could not able to install it. I try to downdrade> 
mbtserver 0.7
 mbt 3.2.10
ucto --version 0.5.3
 TiMBL 6.4.2 

each packages found in the following directory  
> /usr/include/mbtserver
/usr/include/mbt
/usr/include/timbl
/usr/include/ucto
I directed the ./configure to ./configure --prefix=/usr/include. but still I get that annoying error. I am confused
how could I trace this ?

---

