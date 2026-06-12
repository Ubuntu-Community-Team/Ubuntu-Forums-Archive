---
title: "installation of PyMedia?"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by Nebelhom on 2010-05-05
Good evening folks,

I would like to install [pymedia]("http://pymedia.org/") on my ubuntu 9.10 karmic distribution, but I am having a bit of a hard time doing that.

I managed to install all the libraries (lame, libogg, libvorbis etc.) but when trying to run 'python setup.py build' I get an error (Shown at the end).

I found on the interwebs that it may have to do with the version of gcc c++ compiler running (currently gcc-4.4) and that it only works with gcc-3.x. Therefore I downloaded gcc-3.4 (from the old jaunty archive), and with this one still no joy. I am officially out of ideas and I am unfortunately not a wizz kid yet, so I would probably need some help.

I would be very grateful if one of you could help me out. thanks!

Nebelhom

P.S. I am not a complete newcomer to linux and python but I am not an expert so it may happen that I ask questions with a very obvious answer.

```
nebelhom@nebelhom-desktop:~/pymedia-1.3.7.3$ python setup.py build
Using UNIX configuration...

OGG          : found
VORBIS       : found
FAAD         : not found
MP3LAME      : found
VORBISENC    : found
ALSA         : found
Continue building pymedia ? [Y,n]:y
running build
running build_py
running build_ext
building 'pymedia.audio.sound' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -DBUILD_NUM=1881 -DPATH_DEV_DSP="/dev/dsp" -DPATH_DEV_MIXER="/dev/mixer" -D_FILE_OFFSET_BITS=64 -DACCEL_DETECT=1 -DHAVE_MMX=1 -DHAVE_LINUX_DVD_STRUCT=1 -DDVD_STRUCT_IN_LINUX_CDROM_H=1 -DCONFIG_VORBIS -DCONFIG_VORBIS -DCONFIG_MP3LAME -DCONFIG_VORBIS -DCONFIG_ALSA -DHAVE_AV_CONFIG_H -DUDF_CACHE=1 -INone -INone -I/usr/include/lame -INone -INone -I/home/nebelhom/pymedia-1.3.7.3 -Isound/ -I/usr/include/python2.6 -c sound/sound.cpp -o build/temp.linux-x86_64-2.6/sound/sound.o
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
sound/sound.cpp:23:20: error: Python.h: No such file or directory
sound/sound.cpp:24:26: error: structmember.h: No such file or directory
In file included from sound/sound.cpp:31:
sound/audio_alsa.h: In member function ‘int OSoundStream::Init(int, int, int, int)’:
sound/audio_alsa.h:322: warning: deprecated conversion from string constant to ‘char*’
sound/audio_alsa.h:324: warning: unused variable ‘val’
sound/audio_alsa.h: In member function ‘int ISoundStream::Init(int, int, int)’:
sound/audio_alsa.h:666: warning: deprecated conversion from string constant to ‘char*’
In file included from sound/sound.cpp:31:
sound/audio_alsa.h: In member function ‘bool Mixer::SetMuteControlValue(int, int, int, int)’:
sound/audio_alsa.h:973: warning: suggest explicit braces to avoid ambiguous ‘else’
sound/audio_alsa.h:1012: warning: suggest explicit braces to avoid ambiguous ‘else’
sound/audio_alsa.h: In constructor ‘Mixer::Mixer(int)’:
sound/audio_alsa.h:1033: warning: deprecated conversion from string constant to ‘char*’
sound/audio_alsa.h: In member function ‘bool Mixer::SetControlValue(int, int, int, int, int)’:
sound/audio_alsa.h:1330: warning: suggest explicit braces to avoid ambiguous ‘else’
sound/sound.cpp: At global scope:
sound/sound.cpp:234: error: expected constructor, destructor, or type conversion before ‘*’ token
sound/sound.cpp:239: error: ‘PyObject_HEAD’ does not name a type
sound/sound.cpp:247: error: ‘PyObject_HEAD’ does not name a type
sound/sound.cpp:258: error: ‘PyObject_HEAD’ does not name a type
sound/sound.cpp:265: error: ‘PyObject_HEAD’ does not name a type
sound/sound.cpp:272: error: ‘PyObject_HEAD’ does not name a type
sound/sound.cpp:279: error: ‘PyObject_HEAD’ does not name a type
sound/sound.cpp:293: error: expected initializer before ‘*’ token
sound/audio_alsa.h:112: warning: ‘snd_mixer_elem_t* alsamixer_find_elem(snd_mixer_t*, char*, int)’ defined but not used
error: command 'gcc' failed with exit status 1
```

---

### Post by Nebelhom on 2010-05-05
bump?

really? noone? :(

---

