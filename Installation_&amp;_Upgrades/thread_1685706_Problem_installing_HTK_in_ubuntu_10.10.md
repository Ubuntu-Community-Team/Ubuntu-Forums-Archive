---
title: "Problem installing HTK in ubuntu 10.10"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by dmolina87 on 2011-02-11
I have a problem installing HTK 3.4.1 in ubuntu 10.10, this is the code when I use "./configure", "make all" and "make install"


diego@diego-desktop:~/htk$ [COLOR="Red"]./configure[/COLOR]

checking whether make sets $(MAKE)... yes
checking for gawk... no
checking for mawk... mawk
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for main in -lX11... yes
checking for main in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether gcc needs -traditional... no
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working strtod... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for floor... yes
checking for gettimeofday... yes
checking for memmove... yes
checking for memset... yes
checking for modf... yes
checking for pow... yes
checking for socket... yes
checking for sqrt... yes
checking for strchr... yes
checking for strcspn... yes
checking for strrchr... yes
checking for strspn... yes
checking for strstr... yes
checking for strtol... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
configure: creating ./config.status
config.status: creating HTKLib/Makefile
[COLOR="red"]config.status: WARNING:  HTKLib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HTKTools/Makefile
config.status: WARNING:  HTKTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HLMLib/Makefile
config.status: WARNING:  HLMLib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HLMTools/Makefile
config.status: WARNING:  HLMTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HTKLVRec/Makefile
config.status: WARNING:  HTKLVRec/Makefile.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting[/COLOR]

diego@diego-desktop:~/htk$ [COLOR="red"]make all[/COLOR]

(cd HTKLib && make HTKLib.a) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio «/home/diego/htk/HTKLib»
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HGraf.o HGraf.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esig_asc.o esig_asc.c
esig_asc.c: In function ‘ReadAsciiEscape’:
esig_asc.c:2025: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esig_edr.o esig_edr.c
esig_edr.c: In function ‘ReadEdrRecord’:
esig_edr.c:309: warning: ‘flags’ may be used uninitialized in this function
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esignal.o esignal.c
esignal.c: In function ‘GetLine’:
esignal.c:1760: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
esignal.c: In function ‘GetLong’:
esignal.c:1808: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esig_nat.o esig_nat.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HAdapt.o HAdapt.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HArc.o HArc.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HAudio.o HAudio.c
HAudio.c: In function ‘StartAudioInput’:
HAudio.c:2174: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HDict.o HDict.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HExactMPE.o HExactMPE.c
HExactMPE.c: In function ‘DoCorrectness’:
HExactMPE.c:288: warning: value computed is not used
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HFB.o HFB.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HFBLat.o HFBLat.c
HFBLat.c: In function ‘DoAllMixUpdates’:
HFBLat.c:1074: warning: ‘mammi’ may be used uninitialized in this function
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HLabel.o HLabel.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HLat.o HLat.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HLM.o HLM.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HMap.o HMap.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HMath.o HMath.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HMem.o HMem.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HModel.o HModel.c
HModel.c: In function ‘PutBaseClass’:
HModel.c:2958: warning: ‘stream’ may be used uninitialized in this function
HModel.c:2958: warning: ‘comp’ may be used uninitialized in this function
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HNet.o HNet.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HParm.o HParm.c
HParm.c: In function ‘OpenAsChannel’:
HParm.c:4151: warning: ‘initRows’ may be used uninitialized in this function
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HRec.o HRec.c
HRec.c: In function ‘LatFromPaths’:
HRec.c:1520: warning: ‘labid’ may be used uninitialized in this function
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HShell.o HShell.c
HShell.c: In function ‘NextArg’:
HShell.c:725: warning: ignoring return value of ‘strtod’, declared with attribute warn_unused_result
HShell.c: In function ‘KeyPressed’:
HShell.c:1489: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HSigP.o HSigP.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HTrain.o HTrain.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HUtil.o HUtil.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HVQ.o HVQ.c
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HWave.o HWave.c
HWave.c: In function ‘GetWAVHeaderInfo’:
HWave.c:1062: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1068: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1069: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1081: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1082: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1087: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1097: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1105: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1108: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1109: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1110: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c:1125: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
HWave.c: In function ‘PutESIGHeaderInfo’:
HWave.c:1342: warning: ‘inList’ may be used uninitialized in this function
gcc  -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o strarr.o strarr.c
if [ -f HTKLib.a ] ; then  /bin/rm HTKLib.a ; fi
ar rv HTKLib.a HGraf.o esig_asc.o esig_edr.o esignal.o esig_nat.o HAdapt.o HArc.o HAudio.o HDict.o HExactMPE.o HFB.o HFBLat.o HLabel.o HLat.o HLM.o HMap.o HMath.o HMem.o HModel.o HNet.o HParm.o HRec.o HShell.o HSigP.o HTrain.o HUtil.o HVQ.o HWave.o strarr.o
ar: creating HTKLib.a
a - HGraf.o
a - esig_asc.o
a - esig_edr.o
a - esignal.o
a - esig_nat.o
a - HAdapt.o
a - HArc.o
a - HAudio.o
a - HDict.o
a - HExactMPE.o
a - HFB.o
a - HFBLat.o
a - HLabel.o
a - HLat.o
a - HLM.o
a - HMap.o
a - HMath.o
a - HMem.o
a - HModel.o
a - HNet.o
a - HParm.o
a - HRec.o
a - HShell.o
a - HSigP.o
a - HTrain.o
a - HUtil.o
a - HVQ.o
a - HWave.o
a - strarr.o
ranlib HTKLib.a
make[1]: se sale del directorio «/home/diego/htk/HTKLib»
(cd HTKTools && make all) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio «/home/diego/htk/HTKTools»
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHSLab = xHSLab ] ; then \
		gcc -o HSLab -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HSLab -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
HSLab.c: In function ‘DoSpecial’:
HSLab.c:1596: warning: ignoring return value of ‘system’, declared with attribute warn_unused_result
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HSLab /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHBuild = xHSLab ] ; then \
		gcc -o HBuild -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HBuild.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HBuild -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HBuild.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HBuild /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHCompV = xHSLab ] ; then \
		gcc -o HCompV -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HCompV.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HCompV -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HCompV.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HCompV /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHCopy = xHSLab ] ; then \
		gcc -o HCopy -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HCopy.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HCopy -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HCopy.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HCopy /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHDMan = xHSLab ] ; then \
		gcc -o HDMan -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HDMan.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HDMan -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HDMan.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HDMan /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHERest = xHSLab ] ; then \
		gcc -o HERest -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HERest.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HERest -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HERest.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HERest /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHHEd = xHSLab ] ; then \
		gcc -o HHEd -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HHEd.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HHEd -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HHEd.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HHEd /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHInit = xHSLab ] ; then \
		gcc -o HInit -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HInit.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HInit -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HInit.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HInit /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHLEd = xHSLab ] ; then \
		gcc -o HLEd -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HLEd.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HLEd -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HLEd.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HLEd /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHList = xHSLab ] ; then \
		gcc -o HList -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HList.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HList -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HList.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HList /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHLRescore = xHSLab ] ; then \
		gcc -o HLRescore -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HLRescore.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HLRescore -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HLRescore.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HLRescore /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHLStats = xHSLab ] ; then \
		gcc -o HLStats -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HLStats.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HLStats -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HLStats.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HLStats /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHMMIRest = xHSLab ] ; then \
		gcc -o HMMIRest -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HMMIRest.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HMMIRest -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HMMIRest.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HMMIRest /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHParse = xHSLab ] ; then \
		gcc -o HParse -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HParse.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HParse -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HParse.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HParse /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHQuant = xHSLab ] ; then \
		gcc -o HQuant -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HQuant.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HQuant -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HQuant.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HQuant /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHRest = xHSLab ] ; then \
		gcc -o HRest -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HRest.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HRest -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HRest.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HRest /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHResults = xHSLab ] ; then \
		gcc -o HResults -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HResults.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HResults -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HResults.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HResults /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHSGen = xHSLab ] ; then \
		gcc -o HSGen -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSGen.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HSGen -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSGen.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HSGen /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHSmooth = xHSLab ] ; then \
		gcc -o HSmooth -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSmooth.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HSmooth -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSmooth.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HSmooth /usr/local/bin  ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHVite = xHSLab ] ; then \
		gcc -o HVite -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HVite.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HVite -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HVite.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HVite /usr/local/bin  ; fi
make[1]: se sale del directorio «/home/diego/htk/HTKTools»
(cd HLMLib && make all) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio «/home/diego/htk/HLMLib»
gcc -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -DSANITY -I. -I../HTKLib/   -c -o LModel.o LModel.c
gcc -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -DSANITY -I. -I../HTKLib/   -c -o LPMerge.o LPMerge.c
LPMerge.c:423: warning: ‘NormaliseFE’ defined but not used
gcc -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -DSANITY -I. -I../HTKLib/   -c -o LPCalc.o LPCalc.c
gcc -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -DSANITY -I. -I../HTKLib/   -c -o LUtil.o LUtil.c
gcc -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -DSANITY -I. -I../HTKLib/   -c -o LWMap.o LWMap.c
gcc -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -DSANITY -I. -I../HTKLib/   -c -o LCMap.o LCMap.c
gcc -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -DSANITY -I. -I../HTKLib/   -c -o LGBase.o LGBase.c
if [ -f HLMLib.a ] ; then  /bin/rm HLMLib.a ; fi
ar rv HLMLib.a LModel.o LPMerge.o LPCalc.o LUtil.o LWMap.o LCMap.o LGBase.o
ar: creating HLMLib.a
a - LModel.o
a - LPMerge.o
a - LPCalc.o
a - LUtil.o
a - LWMap.o
a - LCMap.o
a - LGBase.o
ranlib HLMLib.a
make[1]: se sale del directorio «/home/diego/htk/HLMLib»
(cd HLMTools && make all) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio «/home/diego/htk/HLMTools»
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o Cluster -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  Cluster.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
Cluster.c: In function ‘do_recovery’:
Cluster.c:870: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
Cluster.c:874: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
Cluster.c:887: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
Cluster.c:896: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
Cluster.c:906: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
Cluster.c: In function ‘import_classmap’:
Cluster.c:1354: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 Cluster /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o HLMCopy -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  HLMCopy.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 HLMCopy /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LAdapt -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LAdapt.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LAdapt /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LBuild -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LBuild.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LBuild /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LFoF -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LFoF.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LFoF /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LGCopy -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LGCopy.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LGCopy /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LGList -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LGList.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LGList /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LGPrep -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LGPrep.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LGPrep /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LLink -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LLink.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
LLink.c: In function ‘main’:
LLink.c:145: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
LLink.c:179: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LLink /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LMerge -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LMerge.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LMerge /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LNewMap -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LNewMap.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LNewMap /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LNorm -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LNorm.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LNorm /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LPlex -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LPlex.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LPlex /usr/local/bin ; fi
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
gcc -o LSubset -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I../HTKLib -I../HLMLib  LSubset.c ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -L/usr/X11R6/lib  ../HTKLib/HTKLib.a ../HLMLib/HLMLib.a -lm
if [ X_ = X_yes ] ; then /usr/bin/install -c -m 755 LSubset /usr/local/bin ; fi
[COLOR="red"]make[1]: se sale del directorio «/home/diego/htk/HLMTools»[/COLOR]

diego@diego-desktop:~/htk$ [COLOR="red"]make install[/COLOR]
(cd HTKTools && make all) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio «/home/diego/htk/HTKTools»
make[1]: No se hace nada para «all».
make[1]: se sale del directorio «/home/diego/htk/HTKTools»
(cd HTKTools && make install) \
	|| case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio «/home/diego/htk/HTKTools»
if [ ! -d /usr/local/bin ] ; then mkdir /usr/local/bin ; fi
for program in HSLab HBuild HCompV HCopy HDMan HERest HHEd HInit HLEd 	HList HLRescore HLStats HMMIRest HParse HQuant HRest HResults HSGen HSmooth HVite  ; do /usr/bin/install -c -m 755 ${program} /usr/local/bin ; done
/usr/bin/install: no se puede borrar «/usr/local/bin/HSLab»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HBuild»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HCompV»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HCopy»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HDMan»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HERest»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HHEd»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HInit»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HLEd»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HList»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HLRescore»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HLStats»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HMMIRest»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HParse»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HQuant»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HRest»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HResults»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HSGen»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HSmooth»: Permiso denegado
/usr/bin/install: no se puede borrar «/usr/local/bin/HVite»: Permiso denegado
make[1]: *** [install] Error 1
make[1]: se sale del directorio «/home/diego/htk/HTKTools»
make: *** [install-htktools] Error 1

---

### Post by nawwara on 2011-02-13
hi,
i have a problem how to install htk on ubunto 10.10
make all ant make install don' t work i tried the code" sudo apt-getinstall libc6-dev-i386 but nothing work.
if someone have a solution please tell me.
thanks.

---

### Post by dabraude on 2011-10-20
run

sudo apt-get install build-essential libc6-i386 libc6-dev-i386 xorg-dev libx11-xcb-dev ia32-libs

(if you get an error reinstall libx11-dev)

To do live recognition follow this link:
[http://ubuntuforums.org/showthread.php?p=11341143#post11341143](http://ubuntuforums.org/showthread.php?p=11341143#post11341143)

---

