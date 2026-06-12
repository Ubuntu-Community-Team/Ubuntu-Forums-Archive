---
title: "Error Compiling Audacity 1.2.6 from source in Edgy"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by shewbox on 2006-12-21
The Audacity packages in Synaptic are 1.2.4b, and I want the newest, stable release of Audacity 1.2.6.  I don't know of any other way to do this except to attempt to compile it from source.  I downloaded the source package, and, after installing all the wx2.4 packages from synaptic (as per instructions from Audacity), I attempted to compile and make, but ran into a wall I'm not sure how to get around.  Any help would be appreciated!  Here is the output of './configure && make' in the Audacity directory.

```
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
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
checking sndfile.h usability... no
checking sndfile.h presence... no
checking for sndfile.h... no
checking for lib-src/libmad/frame.h... no
checking for lib-src/libvorbis/include/vorbis/vorbisenc.h... no
checking for lib-src/libid3tag/frame.h... no
checking for lib-src/libsamplerate/src/samplerate.h... no
checking for lib-src/libresample/include/libresample.h... yes
checking for lib-src/soundtouch/include/SoundTouch.h... yes
checking for lib-src/libflac/include/FLAC/all.h... no
checking mad.h usability... no
checking mad.h presence... no
checking for mad.h... no
checking vorbis/vorbisenc.h usability... no
checking vorbis/vorbisenc.h presence... no
checking for vorbis/vorbisenc.h... no
checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
checking FLAC/all.h usability... no
checking FLAC/all.h presence... no
checking for FLAC/all.h... no
checking for zip... /usr/bin/zip
checking for wx-config... /usr/bin/wx-config
configure: Checking that the installed version of wxWidgets is 2.4.x
Great, you're using wxWidgets 2.4.x!
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for lrint... yes
checking for lrintf... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating lib-src/Makefile
config.status: creating lib-src/allegro/Makefile
config.status: creating lib-src/expat/Makefile
config.status: creating lib-src/libnyquist/Makefile
config.status: creating locale/Makefile
config.status: creating src/configunix.h
config.status: src/configunix.h is unchanged

Finished configure:
  with    libsndfile (local)
  with    libresample
  without libid3tag
  without libmad
  with    LADSPA plug-in support
  with    Nyquist plug-in support
  without libvorbis
  with    portmixer
  with    portaudio v18
  with    soundtouch (local)
  with    help
prefix=/usr/local

Note: portaudio v18 only supports OSS.  If your system supports
ALSA, you may want to reconfigure --with-portaudio=v19, though
portaudio v19 is newer and possibly less stable.

Run 'configure --help' for an explanation of these options,
otherwise run 'make' to build Audacity.
make -C lib-src
make[1]: Entering directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src'
cd soundtouch && make
make[2]: Entering directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch'
Making all in include
make[3]: Entering directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch/include'
make[4]: Entering directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch'
make[4]: Leaving directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch'
make  all-am
make[4]: Entering directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch/include'
make[5]: Entering directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch'
make[5]: Leaving directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch'
make[4]: Leaving directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch/include'
make[3]: Leaving directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch/include'
Making all in source
make[3]: Entering directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch/source'
Making all in SoundTouch
make[4]: Entering directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch/source/SoundTouch'
if /bin/bash ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include   -O3 -fcheck-new -I../../include  -MT sse_optimized.lo -MD -MP -MF ".deps/sse_optimized.Tpo" -c -o sse_optimized.lo sse_optimized.cpp; \
        then mv -f ".deps/sse_optimized.Tpo" ".deps/sse_optimized.Plo"; else rm -f ".deps/sse_optimized.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -O3 -fcheck-new -I../../include -MT sse_optimized.lo -MD -MP -MF .deps/sse_optimized.Tpo -c sse_optimized.cpp -o sse_optimized.o
In file included from sse_optimized.cpp:70:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/xmmintrin.h:34:3: error: #error "SSE instruction set not enabled"
sse_optimized.cpp: In member function 'virtual double soundtouch::TDStretchSSE::calcCrossCorrStereo(const float*, const float*) const':
sse_optimized.cpp:76: error: '__m128' was not declared in this scope
sse_optimized.cpp:76: error: expected `;' before 'vSum'
sse_optimized.cpp:106: error: 'pVec2' was not declared in this scope
sse_optimized.cpp:106: error: expected primary-expression before ')' token
sse_optimized.cpp:106: error: expected `;' before 'pV2'
sse_optimized.cpp:107: error: 'vSum' was not declared in this scope
sse_optimized.cpp:107: error: '_mm_setzero_ps' was not declared in this scope
sse_optimized.cpp:113: error: '_mm_load_ps' was not declared in this scope
sse_optimized.cpp:113: error: '_mm_mul_ps' was not declared in this scope
sse_optimized.cpp:113: error: '_mm_add_ps' was not declared in this scope
sse_optimized.cpp: In member function 'virtual uint soundtouch::FIRFilterSSE::evaluateFilterStereo(float*, const float*, uint) const':
sse_optimized.cpp:296: error: expected initializer before '*' token
sse_optimized.cpp:297: error: '__m128' was not declared in this scope
sse_optimized.cpp:297: error: expected `;' before 'sum1'
sse_optimized.cpp:301: error: 'pFil' was not declared in this scope
sse_optimized.cpp:301: error: expected primary-expression before ')' token
sse_optimized.cpp:301: error: expected `;' before 'filterCoeffsAlign'
sse_optimized.cpp:303: error: 'sum1' was not declared in this scope
sse_optimized.cpp:303: error: 'sum2' was not declared in this scope
sse_optimized.cpp:303: error: '_mm_setzero_ps' was not declared in this scope
sse_optimized.cpp:313: error: '_mm_loadu_ps' was not declared in this scope
sse_optimized.cpp:313: error: '_mm_mul_ps' was not declared in this scope
sse_optimized.cpp:313: error: '_mm_add_ps' was not declared in this scope
sse_optimized.cpp:334: error: '_MM_SHUFFLE' was not declared in this scope
sse_optimized.cpp:334: error: '_mm_shuffle_ps' was not declared in this scope
sse_optimized.cpp:336: error: '_mm_add_ps' was not declared in this scope
sse_optimized.cpp:336: error: '_mm_storeu_ps' was not declared in this scope
make[4]: *** [sse_optimized.lo] Error 1
make[4]: Leaving directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch/source/SoundTouch'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch/source'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src/soundtouch'
make[1]: *** [soundtouch/source/SoundTouch/.libs/libSoundTouch.a] Error 2
make[1]: Leaving directory `/home/ben/sandbox/audacity-src-1.2.6/lib-src'
make: *** [audacity] Error 2

```

---

