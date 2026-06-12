---
title: "Alsa mixer installation error"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2010-03-21
Hi I have dowloaded the latest version of alsa mixer and done cd, configure etc until I got to make install, where it gives me the following error....

I am using xubuntu 9.10 on an AAO 

what does it mean?

abelito@Ernestino:~/Downloads/alsa-driver-1.0.22.1$ make install
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/abelito/Downloads/alsa-driver-1.0.22.1/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
rm: cannot remove `/usr/include/sound/ac97_codec.h': Permission denied
install: cannot remove `/usr/include/sound/ac97_codec.h': Permission denied
make: *** [install-headers] Error 1

---

### Post by n0dix on 2010-03-21
Try with: sudo make install

---

### Post by abelito8 on 2010-03-21
thank you, it helped with alsa-lib but alsa-driver still gives me an error, shall I post the new results?

---

### Post by n0dix on 2010-03-21
If you want.

---

### Post by abelito8 on 2010-03-21
THis is the result of make

abelito@Ernestino:~/Downloads/alsa-driver-1.0.22.1$ make
make dep
make[1]: Entering directory `/home/abelito/Downloads/alsa-driver-1.0.22.1'
make[2]: Entering directory `/home/abelito/Downloads/alsa-driver-1.0.22.1/include'
make -C sound prepare
make[3]: Entering directory `/home/abelito/Downloads/alsa-driver-1.0.22.1/include/sound'
make prepare2
make[4]: Entering directory `/home/abelito/Downloads/alsa-driver-1.0.22.1/include/sound'
ln -s ../../alsa-kernel/include/cs4231-regs.h
ln -s ../../alsa-kernel/include/cs46xx.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_scb_types.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_spos.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_task_types.h
ln -s ../../alsa-kernel/include/cs8403.h
ln -s ../../alsa-kernel/include/cs8427.h
ln -s ../../alsa-kernel/include/emu10k1.h
ln -s ../../alsa-kernel/include/emu10k1_synth.h
ln -s ../../alsa-kernel/include/emu8000.h
ln -s ../../alsa-kernel/include/emu8000_reg.h
ln -s ../../alsa-kernel/include/emux_legacy.h
ln -s ../../alsa-kernel/include/emux_synth.h
ln -s ../../alsa-kernel/include/es1688.h
ln -s ../../alsa-kernel/include/gus.h
ln -s ../../alsa-kernel/include/hda_hwdep.h
ln -s ../../alsa-kernel/include/hdsp.h
ln -s ../../alsa-kernel/include/hdspm.h
ln -s ../../alsa-kernel/include/hwdep.h
ln -s ../../alsa-kernel/include/i2c.h
ln -s ../../alsa-kernel/include/info.h
ln -s ../../alsa-kernel/include/initval.h
ln -s ../../alsa-kernel/include/jack.h
ln -s ../../alsa-kernel/include/l3.h
ln -s ../../alsa-kernel/include/memalloc.h
ln -s ../../alsa-kernel/include/minors.h
ln -s ../../alsa-kernel/include/mixer_oss.h
ln -s ../../alsa-kernel/include/mpu401.h
ln -s ../../alsa-kernel/include/opl3.h
ln -s ../../alsa-kernel/include/opl4.h
ln -s ../../alsa-kernel/include/pcm-indirect.h
cp ../../alsa-kernel/include/pcm.h .
patch -p0 -i pcm.patch pcm.h
make[4]: patch: Command not found
make[4]: *** [pcm.h] Error 127
make[4]: Leaving directory `/home/abelito/Downloads/alsa-driver-1.0.22.1/include/sound'
make[3]: *** [prepare] Error 2
make[3]: Leaving directory `/home/abelito/Downloads/alsa-driver-1.0.22.1/include/sound'
make[2]: *** [prepare] Error 2
make[2]: Leaving directory `/home/abelito/Downloads/alsa-driver-1.0.22.1/include'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/abelito/Downloads/alsa-driver-1.0.22.1'
make: *** [include/sndversions.h] Error 2

and this is sudo make install

abelito@Ernestino:~/Downloads/alsa-driver-1.0.22.1$ sudo make install
[sudo] password for abelito: 
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/abelito/Downloads/alsa-driver-1.0.22.1/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
find /lib/modules/2.6.31-20-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.31-20-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.31-20-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.31-20-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/abelito/Downloads/alsa-driver-1.0.22.1/include'
make[1]: Nothing to be done for `modules_install'.
make[1]: Leaving directory `/home/abelito/Downloads/alsa-driver-1.0.22.1/include'
make[1]: Entering directory `/home/abelito/Downloads/alsa-driver-1.0.22.1/acore'
mkdir -p /lib/modules/2.6.31-20-generic/kernel/sound/acore
cp snd-hrtimer.ko snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-timer.ko snd.ko /lib/modules/2.6.31-20-generic/kernel/sound/acore
cp: cannot stat `snd-hrtimer.ko': No such file or directory
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/abelito/Downloads/alsa-driver-1.0.22.1/acore'
make: *** [install-modules] Error 1

and this is when I try with alsa user

abelito@Ernestino:~/Downloads/alsa-utils-1.0.22$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.16... found.
checking for snd_ctl_open in -lasound... yes
checking for alsa/pcm.h... yes
checking for alsa/mixer.h... yes
checking for alsa/rawmidi.h... yes
checking for alsa/seq.h... yes
checking for librt... checking for clock_gettime in -lrt... yes
checking for xmlto... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for ncursesw5-config... yes
checking for curses library... ncursesw
checking for curses header name... <ncurses.h>
checking for curses compiler flags... -I/usr/include/ncursesw
checking for curses NLS support... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking panel.h usability... no
checking panel.h presence... no
checking for panel.h... no
configure: error: required curses helper header not found

---

### Post by n0dix on 2010-03-21
First focus in make, 
Install this: sudo aptitude install build-essential patch 
And run the make, post if it is an error.

Btw, the order is ./configure, make and make install

---

