---
title: "I', having big time trouble in compiling froma a source code!"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by LightSeeker1445 on 2007-09-26
Ok, I'm running a Ubuntu Studio and want to install Audacity 1.3. beta, which is only available in the form of a source code for the Linux systems.

Since I am a beginner, I read some stuff on the internet and got acquainted with the ./configure and make commands and such. 

So i entered the configure command and after installing all the libraries that I needed, I was on to enetering the MAKE command. Then I got this message:

It's a repeating pattern, but sadly I don't know what it is repeating about, I just know that something is wrong. Could somebody please help me? 

[I]Desktop/audacity-src-1.3.3-beta$ make
make -C lib-src
make[1]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src'
make -C libsndfile
make[2]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile'
Making all in man
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/man'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/man'
Making all in doc
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/doc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/doc'
Making all in Win32
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/Win32'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/Win32'
Making all in Octave
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/Octave'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/Octave'
Making all in src
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/src'
make  all-recursive
make[4]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/src'
Making all in GSM610
make[5]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/src/GSM610'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/src/GSM610'
Making all in G72x
make[5]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/src/G72x'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/src/G72x'
make[5]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/src'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/src'
make[4]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/src'
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/src'
Making all in examples
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/examples'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/examples'
Making all in regtest
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/regtest'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/regtest'
Making all in tests
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/tests'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile/tests'
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile'
make[2]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libsndfile'
ln -sf libsndfile/src/.libs/libsndfile.a libsndfile.a
make -C libresample
make[2]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libresample'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/libresample'
ln -sf libresample/libresample.a libresample.a
make -C soundtouch
make[2]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch'
Making all in include
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch/include'
make  all-am
make[4]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch/include'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch/include'
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch/include'
Making all in source
make[3]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch/source'
Making all in SoundTouch
make[4]: Entering directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch/source/SoundTouch'
/bin/bash ../../libtool --tag=CXX --mode=link g++ -O3 -msse -fcheck-new -I../../include    -o libSoundTouch.la -rpath /usr/local/lib  AAFilter.lo FIRFilter.lo FIFOSampleBuffer.lo mmx_optimized.lo sse_optimized.lo RateTransposer.lo SoundTouch.lo TDStretch.lo cpu_detect_x86_gcc.lo  -lm 
libtool: link: `sse_optimized.lo' is not a valid libtool object
make[4]: *** [libSoundTouch.la] Error 1
make[4]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch/source/SoundTouch'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch/source'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch'
make[1]: *** [soundtouch-recursive] Error 2
make[1]: Leaving directory `/home/irenej/Desktop/audacity-src-1.3.3-beta/lib-src'
make: *** [audacity] Error 2
[/I]

---

### Post by LightSeeker1445 on 2007-09-26
Anybody have an idea of what's wrong? Ireally need this program to work, since I saved all of my recordings in a 1.3.3 version on my previous window XP System. Without this program, the whole Os is useless to me :(

---

### Post by LightSeeker1445 on 2007-09-26
Ok, now Im just annoying :) But I can't help it:)

---

### Post by kklingerman on 2007-09-29
I am having the same issue.  Anyone have any ideas?  Thanks.

---

