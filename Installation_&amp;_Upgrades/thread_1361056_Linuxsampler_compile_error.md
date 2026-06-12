---
title: "Linuxsampler compile error"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by jitup on 2009-12-21
hello,
I am trying to compile linuxsampler from source but sort of hit a wall this is the out put I am getting from the terminal
```
jim@ubuntu:~$ linuxsampler-1.0.0/configure 
checking for g++... g++ 
checking for C++ compiler default output file name... a.out 
checking whether the C++ compiler works... yes 
checking whether we are cross compiling... no 
checking for suffix of executables...  
checking for suffix of object files... o 
checking whether we are using the GNU C++ compiler... yes 
checking whether g++ accepts -g... yes 
checking build system type... x86_64-unknown-linux-gnu 
checking host system type... x86_64-unknown-linux-gnu 
checking for gcc... gcc 
checking whether we are using the GNU C compiler... yes 
checking whether gcc accepts -g... yes 
checking for gcc option to accept ISO C89... none needed 
checking for a sed that does not truncate output... /bin/sed 
checking for grep that handles long lines and -e... /bin/grep 
checking for egrep... /bin/grep -E 
checking for ld used by gcc... /usr/bin/ld 
checking if the linker (/usr/bin/ld) is GNU ld... yes 
checking for /usr/bin/ld option to reload object files... -r 
checking for BSD-compatible nm... /usr/bin/nm -B 
checking whether ln -s works... yes 
checking how to recognize dependent libraries... pass_all 
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
checking dlfcn.h usability... yes 
checking dlfcn.h presence... yes 
checking for dlfcn.h... yes 
checking how to run the C++ preprocessor... g++ -E 
checking for g77... no 
checking for xlf... no 
checking for f77... no 
checking for frt... no 
checking for pgf77... no 
checking for cf77... no 
checking for fort77... no 
checking for fl32... no 
checking for af77... no 
checking for xlf90... no 
checking for f90... no 
checking for pgf90... no 
checking for pghpf... no 
checking for epcf90... no 
checking for gfortran... no 
checking for g95... no 
checking for xlf95... no 
checking for f95... no 
checking for fort... no 
checking for ifort... no 
checking for ifc... no 
checking for efc... no 
checking for pgf95... no 
checking for lf95... no 
checking for ftn... no 
checking whether we are using the GNU Fortran 77 compiler... no 
checking whether  accepts -g... no 
checking the maximum length of command line arguments... 1572864 
checking command to parse /usr/bin/nm -B output from gcc object... ok 
checking for objdir... .libs 
checking for ar... ar 
checking for ranlib... ranlib 
checking for strip... strip 
checking if gcc supports -fno-rtti -fno-exceptions... no 
checking for gcc option to produce PIC... -fPIC 
checking if gcc PIC flag -fPIC works... yes 
checking if gcc static flag -static works... yes 
checking if gcc supports -c -o file.o... yes 
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes 
checking whether -lc should be explicitly linked in... no 
checking dynamic linker characteristics... GNU/Linux ld.so 
checking how to hardcode library paths into programs... immediate 
checking whether stripping libraries is possible... yes 
checking if libtool supports shared libraries... yes 
checking whether to build shared libraries... yes 
checking whether to build static libraries... yes 
configure: creating libtool 
appending configuration tag "CXX" to libtool 
checking for ld used by g++... /usr/bin/ld -m elf_x86_64 
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes 
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes 
checking for g++ option to produce PIC... -fPIC 
checking if g++ PIC flag -fPIC works... yes 
checking if g++ static flag -static works... yes 
checking if g++ supports -c -o file.o... yes 
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes 
checking dynamic linker characteristics... GNU/Linux ld.so 
(cached) (cached) checking how to hardcode library paths into programs... immediate 
appending configuration tag "F77" to libtool 
checking whether byte ordering is bigendian... no 
checking host system type... (cached) x86_64-unknown-linux-gnu 
checking for pkg-config... /usr/bin/pkg-config 
checking pkg-config is at least version 0.9.0... yes 
checking whether x86 architecture... yes 
checking for mmsystem.h... no 
checking whether UNIX98 compatible... yes 
checking features.h usability... yes 
checking features.h presence... yes 
checking for features.h... yes 
checking for the pthreads library -lpthreads... no 
checking whether pthreads work without any flags... no 
checking whether pthreads work with -Kthread... no 
checking whether pthreads work with -kthread... no 
checking for the pthreads library -llthread... no 
checking whether pthreads work with -pthread... yes 
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE 
checking if more special flags are required for pthreads... no 
checking for NPTL bug... no 
checking uuid/uuid.h usability... no 
checking uuid/uuid.h presence... no 
checking for uuid/uuid.h... no 
checking for library containing uuid_generate... no 
checking alsa/asoundlib.h usability... no 
checking alsa/asoundlib.h presence... no 
checking for alsa/asoundlib.h... no 
checking Alsa version... 1.1.1 
checking for JACK... no 
checking for artsc-config... no 
checking for ARTS artsc - version >= 0.9.5... no 
*** The artsc-config script installed by ARTS could not be found 
*** If ARTS was installed in PREFIX, make sure PREFIX/bin is in 
*** your path, or set the ARTS_CONFIG environment variable to the 
*** full path to artsc-config. 
checking for ASIO headerfile: ./ASIOSDK2/common/asio.h ....no 
checking MidiShare.h usability... no 
checking MidiShare.h presence... no 
checking for MidiShare.h... no 
checking CoreMIDI/CoreMIDI.h usability... no 
checking CoreMIDI/CoreMIDI.h presence... no 
checking for CoreMIDI/CoreMIDI.h... no 
checking CoreAudio/CoreAudio.h usability... no 
checking CoreAudio/CoreAudio.h presence... no 
checking for CoreAudio/CoreAudio.h... no 
checking for mmsystem.h... (cached) no 
checking dssi.h usability... no 
checking dssi.h presence... no 
checking for dssi.h... no 
checking for LV2... no 
checking lv2.h usability... no 
checking lv2.h presence... no 
checking for lv2.h... no 
checking AudioUnit/AudioUnit.h usability... no 
checking AudioUnit/AudioUnit.h presence... no 
checking for AudioUnit/AudioUnit.h... no 
No supported MIDI input system found! 
Sorry, LinuxSampler only supports the following MIDI drivers at the moment: 
ALSA, JACK, MIDIShare, CoreMIDI, MME. 
If you think you have one of those available on your system, make sure you 
also have the respective development (header) files installed. 
jim@ubuntu:~$ 

```
I dont get it! I have jack, and I SHOULD have the correct audio systems, after all I am running ubuntu studio 9.10 with the RT kernal. Please help, I would really like to have this work. Just let me know what any of this stuff means, and what I have to do to make it work.
Thanks
PS- Dose it have anything to do with me running 64 bit?

---

### Post by ibozzie on 2012-08-13
I know this is a bit of gravedigging, but I just came across this same problem and wanted to post a solution, since I didn't see any out there. It's actually quite simple. I followed the instructions [here]("https://help.ubuntu.com/community/CompilingEasyHowTo") about compiling and did an apt-file search for each of the missing header files I saw above the error message. After a few dead ends and some libraries that threatened to uninstall a bajillion packages, I found one that made the bad error message go away: libasound2-dev. Installing that gave it some ALSA headers and let ./configure complete properly.

However, I'll have to do some more searching to get it to recognize JACK, which I need to interface with Ardour. I'll post if I make progress on that.

---

### Post by ibozzie on 2012-08-13
libjack-jackd2-dev will give JACK support. Case closed! :)

---

