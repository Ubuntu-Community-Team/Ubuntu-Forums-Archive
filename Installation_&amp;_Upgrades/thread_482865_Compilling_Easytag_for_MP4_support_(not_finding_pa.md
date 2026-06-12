---
title: "Compilling Easytag for MP4 support (not finding package)"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by mikeym on 2007-06-24
Hi,

I'm trying to compile Easytag 2.1 to get MP4 support and I'm having some difficulty getting it to find the package libmp4v2. Now I have checked that it is installed from the repositories and I have installed the version it's looking for for good measure using checkinstall.

```

Source code location ....: .
Host System Type ........: i686-pc-linux-gnu
Preprocessor ............: gcc
Compiler ................: gcc -g -O2 -Wall
Linker ..................: gcc -lwavpack -lm -lm -lz -lstdc++ -lid3 -lFLAC -lm -lvorbisfile -lvorbis -logg -lm
GTK2 version ............: 2.10.6
MP3 file support ........: yes (id3lib-3.8.3)
Ogg Vorbis file support .: yes
FLAC file support .......: yes (flac-1.1.2)
MP4 file support ........: no
WavPack support .........: yes
NLS/gettext .............: yes
Install path ............: /usr/local

```


But when I check the installed packages

```

$ aptitude search mp4v2 wavpack libflac libid3 libvorbis

iB  libflac++-dev                   - Free Lossless Audio Codec - C++ developmen
id  libflac++5c2                    - Free Lossless Audio Codec - C++ runtime li
i   libflac-dev                     - Free Lossless Audio Codec - C development 
p   libflac-doc                     - Free Lossless Audio Codec - library docume
i   libflac7                        - Free Lossless Audio Codec - runtime C libr
i   libid3-3.8.3-dev                - ID3 Tag Library: Development Libraries and
i   libid3-3.8.3c2a                 - Library for manipulating ID3v1 and ID3v2 t
v   libid3-dev                      -                                           
i   libid3tag0                      - ID3 tag reading library from the MAD proje
p   libid3tag0-dev                  - ID3 tag reading library from the MAD proje
i   libmp4v2                        - library for AAC and mp4 files             
i   libmp4v2-0                      - MP4 container library - runtime files     
i   libmp4v2-dev                    - MP4 container library - development files 
i   libvorbis-dev                   - The Vorbis General Audio Compression Codec
p   libvorbis-ocaml                 - OCaml bindings for vorbis library         
p   libvorbis-ocaml-dev             - OCaml bindings for the vorbis library     
p   libvorbis-perl                  - Perl extension for Ogg Vorbis streams     
i   libvorbis0a                     - The Vorbis General Audio Compression Codec
i   libvorbisenc2                   - The Vorbis General Audio Compression Codec
p   libvorbisfile-ruby              - Ogg Vorbis support library for Ruby       
p   libvorbisfile-ruby1.8           - Ogg Vorbis support library for Ruby       
i   libvorbisfile3                  - The Vorbis General Audio Compression Codec
i   libwavpack-dev                  - an audio codec (lossy and lossless) - deve
i   libwavpack0                     - an audio codec (lossy and lossless) - libr
p   wavpack                         - an audio codec (lossy and lossless) - enco

```

I've attached files showing the full output of ./configure (for easytag) and a list of the included files in the checkinstall package for libmp4v2.

I'm a little stumped on this one so help would be appreciated.

---

### Post by mikeym on 2007-06-24
I hope this is in the right section but I decided that it was more to do with installing the thing than the multimedia application.

---

### Post by overkillm on 2007-08-18
I was having similar difficulties with EasyTag.  The version I was finally able to compile and install was 2.0, but hopefully this helps with 2.1 also.

I wasn't successful with this until I *removed* the libpm4v2, libmp4v2-0, and libmp4v2-dev packages that were installed from the repos (be sure to take note of any other packages which depend on these, of course, they will be removed also), and built and installed mpeg4ip 1.5 instead.  This can be found on sourceforge:

[http://mpeg4ip.sourceforge.net/]("http://mpeg4ip.sourceforge.net/")

I configured it with:

```
./configure --enable-mp4live=no
```

then did make, make install, and when I tried to build easytag 2.0 again, it finally recognized that I had libmp4v2 installed and I was able to build it properly with mp4 support.  So far it works great.

(one note: I did have to copy the file libmp4v2.so.0 from /usr/local/lib to /usr/lib in order to get EasyTag to run.  I'm not sure why... probably because I spent so long building, adding, and removing various packages and libraries trying to get this to work that I accidentally screwed something up in the process...)

I'm pretty new at building apps from source, so this is probably a kludgy solution and I'm sure there's a more elegant one, but it's what worked for me after days of trying.  Hope it works for you.  :)

Alternatively, you can try the easytag-aac .deb package available here: 

[http://www.debian-multimedia.org/pool/main/e/easytag-aac/]("http://www.debian-multimedia.org/pool/main/e/easytag-aac/")

I haven't tried this at all, though... it was going to be my last resort if I wasn't able to build EasyTag after my last attempt.  So, no idea if it will work properly.

---

