---
title: "Compiler Trouble"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by the_flumps on 2006-10-15
Hi all, I'm trying to do a manual compile/install of the latest audacity beta on dapper 6.06, and I'm having major problems getting the compiler to run the ./configure script. I've installed 'build-essential' using synaptic and can only presume I've got a dependancy issue going on. Here's the output from the ./configure script:
```
 ./configure
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
configure: Determining what libraries are available in this tree and on the system
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
checking for vorbis_bitrate_addblock in -lvorbisfile... no
checking vorbis/vorbisfile.h usability... no
checking vorbis/vorbisfile.h presence... no
checking for vorbis/vorbisfile.h... no
configure: Vorbis libraries are NOT available as system libraries
checking for ./lib-src/libvorbis/include/vorbis/vorbisenc.h... no
checking for ./lib-src/libogg/include/ogg/ogg.h... no
configure: Vorbis libraries are NOT available in this source tree
checking for mad_decoder_init in -lmad... no
checking mad.h usability... no
checking mad.h presence... no
checking for mad.h... no
configure: libmad libraries are NOT available as system libraries
checking for ./lib-src/libmad/frame.h... no
configure: libmad libraries are NOT available in the local tree
checking for FLAC__file_decoder_new in -lFLAC... no
checking FLAC/format.h usability... no
checking FLAC/format.h presence... no
checking for FLAC/format.h... no
configure: FLAC/FLAC++ libraries are NOT available as system libraries
checking for ./lib-src/libflac/include/FLAC/format.h... no
checking for ./lib-src/libflac/include/FLAC++/decoder.h... no
configure: FLAC libraries are NOT available in this source tree
checking for pkg-config... /usr/bin/pkg-config
checking for sndfile >= 1.0.0... configure: Libsndfile libraries are NOT available as system libraries
checking for ./lib-src/libsndfile/src/sndfile.h.in... yes
configure: libsndfile libraries are available in this source tree
checking for id3_file_open in -lid3tag... no
checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
configure: Libid3tag libraries are NOT available as system libraries
checking for ./lib-src/libid3tag/frame.h... no
configure: libid3tag libraries are NOT available in the local tree
checking for samplerate >= 0.15.0... configure: Libsamplerate libraries are NOT available as system libraries
checking for ./lib-src/libsamplerate/src/samplerate.h... no
configure: libsamplerate libraries are NOT available in the local tree
checking for ./lib-src/libresample/include/libresample.h... yes
configure: libresample libraries are available in the local tree
checking for ./lib-src/soundtouch/include/SoundTouch.h... yes
configure: libsoundtouch libraries are available in the local tree
checking for ./lib-src/libnyquist/nyx/nyx.h... yes
configure: nyquist libraries are available in the local tree
configure: Figuring out what libraries to enable
configure: disabling LIBVORBIS
configure: disabling LIBMAD
configure: disabling LIBFLAC
configure: Using LOCAL libraries for LIBSNDFILE
configure: disabling LIBID3TAG
configure: disabling LIBSAMPLERATE
configure: Using LOCAL libraries for LIBRESAMPLE
configure: Using LOCAL libraries for LIBSOUNDTOUCH
configure: Using LOCAL libraries for LIBNYQUIST
checking for zip... /usr/bin/zip
checking for wx-config... no
configure: error: "Could not find wx-config: is wxWindows installed? is wx-config in your path?"

```

I also notice that wx-config is missing? I've no idea if it matters or not though :-).

Anyway, if anyone knows how I can sort this, I'm all ears.

TIA.

---

### Post by taurus on 2006-10-15
Use synaptic and search for wxWindows or wx*!  You need to install those dependencies and their dev packages if you want to compile something from source...

---

### Post by the_flumps on 2006-10-16
Hi mate, that was a partial success. I downloaded all the wx** libs I could find, and it lets me ./configure, but falls apart at the make install stage. I get loads of wx** reference errors resulting in an error 2 code at the end.
I think I'll give up for now ...
Thanks for your help though!

---

### Post by taurus on 2006-10-16
Can you include the output of ./configure again?  Need to see exactly what the problem is.

---

### Post by the_flumps on 2006-10-16
Here it is:

```
./configure checking for gcc... gcc
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
configure: Determining what libraries are available in this tree and on the system
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
checking for vorbis_bitrate_addblock in -lvorbisfile... no
checking vorbis/vorbisfile.h usability... no
checking vorbis/vorbisfile.h presence... no
checking for vorbis/vorbisfile.h... no
configure: Vorbis libraries are NOT available as system libraries
checking for ./lib-src/libvorbis/include/vorbis/vorbisenc.h... no
checking for ./lib-src/libogg/include/ogg/ogg.h... no
configure: Vorbis libraries are NOT available in this source tree
checking for mad_decoder_init in -lmad... no
checking mad.h usability... no
checking mad.h presence... no
checking for mad.h... no
configure: libmad libraries are NOT available as system libraries
checking for ./lib-src/libmad/frame.h... no
configure: libmad libraries are NOT available in the local tree
checking for FLAC__file_decoder_new in -lFLAC... no
checking FLAC/format.h usability... no
checking FLAC/format.h presence... no
checking for FLAC/format.h... no
configure: FLAC/FLAC++ libraries are NOT available as system libraries
checking for ./lib-src/libflac/include/FLAC/format.h... no
checking for ./lib-src/libflac/include/FLAC++/decoder.h... no
configure: FLAC libraries are NOT available in this source tree
checking for pkg-config... /usr/bin/pkg-config
checking for sndfile >= 1.0.0... configure: Libsndfile libraries are NOT available as system libraries
checking for ./lib-src/libsndfile/src/sndfile.h.in... yes
configure: libsndfile libraries are available in this source tree
checking for id3_file_open in -lid3tag... no
checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
configure: Libid3tag libraries are NOT available as system libraries
checking for ./lib-src/libid3tag/frame.h... no
configure: libid3tag libraries are NOT available in the local tree
checking for samplerate >= 0.15.0... configure: Libsamplerate libraries are NOT available as system libraries
checking for ./lib-src/libsamplerate/src/samplerate.h... no
configure: libsamplerate libraries are NOT available in the local tree
checking for ./lib-src/libresample/include/libresample.h... yes
configure: libresample libraries are available in the local tree
checking for ./lib-src/soundtouch/include/SoundTouch.h... yes
configure: libsoundtouch libraries are available in the local tree
checking for ./lib-src/libnyquist/nyx/nyx.h... yes
configure: nyquist libraries are available in the local tree
configure: Figuring out what libraries to enable
configure: disabling LIBVORBIS
configure: disabling LIBMAD
configure: disabling LIBFLAC
configure: Using LOCAL libraries for LIBSNDFILE
configure: disabling LIBID3TAG
configure: disabling LIBSAMPLERATE
configure: Using LOCAL libraries for LIBRESAMPLE
configure: Using LOCAL libraries for LIBSOUNDTOUCH
configure: Using LOCAL libraries for LIBNYQUIST
checking for zip... /usr/bin/zip
checking for wx-config... /usr/bin/wx-config
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
config.status: creating lib-src/portaudio/pa_unix_oss/Makefile
config.status: creating locale/Makefile
config.status: creating tests/Makefile
config.status: creating src/configunix.h
config.status: src/configunix.h is unchanged

Finished configure:
LIBVORBIS: disabled
LIBMAD: disabled
LIBFLAC: disabled
LIBSNDFILE: using LOCAL libraries
LIBID3TAG: disabled
LIBSAMPLERATE: disabled
LIBRESAMPLE: using LOCAL libraries
LIBSOUNDTOUCH: using LOCAL libraries
LIBNYQUIST: using LOCAL libraries
ladspa: enabled
audiounits: disabled
prefix=/usr/local

Note: portaudio v18 only supports OSS.  If your system supports
ALSA, you may want to reconfigure --with-portaudio=v19, though
portaudio v19 is newer and possibly less stable.

Run 'configure --help' for an explanation of these options,
otherwise run 'make' to build Audacity.

```

---

### Post by taurus on 2006-10-16
Actually, that is not an error message.  It's telling you that you have compiled it using OSS and if you want to use ALSA, newer, then you need to include an argument in your ./configure!  So, do you want to use OSS or ALSA?  If you want to use OSS, then continue with "make" and "sudo make checkinstall" or else run the config again with

```
./configure --with-portaudio=v19
make
sudo make checkinstall

```

---

### Post by the_flumps on 2006-10-17
The saga continues ....

If I go for OSS and run make install here's the output I get:

```
:/usr/include/wx/string.h:307: undefined reference to `wxString::InitWith(char const*, unsigned int, unsigned int)'
libaudacity.a(BlockFile.o): In function `AliasBlockFile::GetSpaceUsage()':/home/gadgerama/audacity-src-1.3.0b-beta/src/BlockFile.cpp:577: undefined reference to `wxFFile::wxFFile(char const*, char const*)'
libaudacity.a(BlockFile.o): In function `AliasBlockFile::WriteSummary()':/home/gadgerama/audacity-src-1.3.0b-beta/src/BlockFile.cpp:498: undefined reference to `wxFFile::wxFFile(char const*, char const*)'
:/home/gadgerama/audacity-src-1.3.0b-beta/src/BlockFile.cpp:504: undefined reference to `wxLogError(char const*, ...)'
libaudacity.a(BlockFile.o): In function `AliasBlockFile::ReadSummary(void*)':/home/gadgerama/audacity-src-1.3.0b-beta/src/BlockFile.cpp:532: undefined reference to `wxFFile::wxFFile(char const*, char const*)'
libaudacity.a(BlockFile.o): In function `AliasBlockFile':/home/gadgerama/audacity-src-1.3.0b-beta/src/BlockFile.cpp:467: undefined reference to `operator+(wxString const&, char const*)'
:/home/gadgerama/audacity-src-1.3.0b-beta/src/BlockFile.cpp:467: undefined reference to `operator+(wxString const&, char const*)'
collect2: ld returned 1 exit status
make[1]: *** [../audacity] Error 1
make[1]: Leaving directory `/home/gadgerama/audacity-src-1.3.0b-beta/src'
make: *** [audacity] Error 2

```

Obviously, this isn't the whole thing, but there are loads of undefined references to wx* files, and eventually it exits with some errors as shown. As far as I can tell, I've downloaded all the wx* related files held by synaptic.

Also, if I try the ALSA route, I get this output at the end of ./configure  --with-portaudio=v19:

```
configure: error: *** PortAudio v19 does not work with PortMixer (at least not yet)

``` 

Runing a make install after this gives similar results to the 1st code in this response.

---

