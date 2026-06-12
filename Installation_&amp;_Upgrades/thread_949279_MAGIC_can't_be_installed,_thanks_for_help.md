---
title: "MAGIC can't be installed, thanks for help"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by geng on 2008-10-16
I followed the install instruction on [http://opencircuitdesign.com/magic/](http://opencircuitdesign.com/magic/)
after i did ./configure
it says:
-----------------------------------------------------------

Use 'make' to compile and 'make install' to install.

Errors may not be printed to stdout:  see files 'make.log' 
  and 'install.log' for complete error summary.

when i look into make.log, it says,
make[1]: Entering directory `/home/geng/Desktop/magic-7.5.151'
--- making header file database/database.h
./scripts/makedbh database/database.h.in database/database.h
/bin/bash: ./scripts/makedbh: /bin/csh: bad interpreter: No such file or directory
make[1]: *** [database/database.h] Error 126
make[1]: Leaving directory `/home/geng/Desktop/magic-7.5.151'



when i look into install.log, it says

make[1]: Entering directory `/home/geng/Desktop/magic-7.5.151'
./scripts/mkdirs /usr/local/bin /usr/local/man \
		/usr/local/lib/magic/sys /usr/local/lib/magic/scm
mkdir /usr/local/lib/magic
mkdir /usr/local/lib/magic/sys
mkdir /usr/local/lib/magic
mkdir /usr/local/lib/magic/scm
for dir in windows doc scmos ; do \
		(cd $dir && make install); done
make[2]: Entering directory `/home/geng/Desktop/magic-7.5.151/windows'
--- installing glyphs to /usr/local/lib/magic/sys
for i in windows7.glyphs windows11.glyphs windows14.glyphs windows22.glyphs  vfont.B.12 vfont.I.12 vfont.R.8; do \
		(cd /usr/local/lib/magic/sys && rm -f $i); \
		cp $i /usr/local/lib/magic/sys; done
make[2]: Leaving directory `/home/geng/Desktop/magic-7.5.151/windows'
make[2]: Entering directory `/home/geng/Desktop/magic-7.5.151/doc'
cd latexfiles && make install
make[3]: Entering directory `/home/geng/Desktop/magic-7.5.151/doc/latexfiles'
../../scripts/mkdirs /usr/local/lib/magic/doc
mkdir /usr/local/lib/magic
mkdir /usr/local/lib/magic/doc
cp ../psfiles/tut1.ps /usr/local/lib/magic/doc/tut1.ps
make[3]: Leaving directory `/home/geng/Desktop/magic-7.5.151/doc/latexfiles'
make[2]: Leaving directory `/home/geng/Desktop/magic-7.5.151/doc'
make[2]: Entering directory `/home/geng/Desktop/magic-7.5.151/scmos'
cd cif_template; make clean; make;
make[3]: Entering directory `/home/geng/Desktop/magic-7.5.151/scmos/cif_template'
rm -f objs/CIFin objs/CIFout objs/IBMCIFin objs/IBMCIFout objs/TMCIFin \
	objs/TMCIFout objs/SUBCIFin objs/SUBCIFout
make[3]: Leaving directory `/home/geng/Desktop/magic-7.5.151/scmos/cif_template'
make[3]: Entering directory `/home/geng/Desktop/magic-7.5.151/scmos/cif_template'
../../scripts/mkdirs objs
mkdir objs
rm -f objs/CIFin
gcc -E -x c -DSTANDARD cifin.c | sed -e "/^#/D" -e "s/(gen )/(gen)/" -e "s/(nowell )/(nowell)/" -e "s/(nwell )/(nwell)/" -e "s/(pwell )/(pwell)/" > objs/CIFin
rm -f objs/CIFout
gcc -E -x c -DSTANDARD cifout.c | sed -e "/^#/D" -e "s/(gen )/(gen)/" -e "s/(nowell )/(nowell)/" -e "s/(nwell )/(nwell)/" -e "s/(pwell )/(pwell)/" > objs/CIFout
rm -f objs/IBMCIFin
gcc -E -x c -DIBM cifin.c | sed -e "/^#/D" -e "s/(gen )/(gen)/" -e "s/(nowell )/(nowell)/" -e "s/(nwell )/(nwell)/" -e "s/(pwell )/(pwell)/" > objs/IBMCIFin
rm -f objs/IBMCIFout
gcc -E -x c -DIBM cifout.c | sed -e "/^#/D" -e "s/(gen )/(gen)/" -e "s/(nowell )/(nowell)/" -e "s/(nwell )/(nwell)/" -e "s/(pwell )/(pwell)/" > objs/IBMCIFout
rm -f objs/TMCIFin
gcc -E -x c -DTIGHTMETAL cifin.c | sed -e "/^#/D" -e "s/(gen )/(gen)/" -e "s/(nowell )/(nowell)/" -e "s/(nwell )/(nwell)/" -e "s/(pwell )/(pwell)/" > objs/TMCIFin
rm -f objs/TMCIFout
gcc -E -x c -DTIGHTMETAL cifout.c | sed -e "/^#/D" -e "s/(gen )/(gen)/" -e "s/(nowell )/(nowell)/" -e "s/(nwell )/(nwell)/" -e "s/(pwell )/(pwell)/" > objs/TMCIFout
rm -f objs/SUBCIFin
gcc -E -x c -DSUBMICRON cifin.c | sed -e "/^#/D" -e "s/(gen )/(gen)/" -e "s/(nowell )/(nowell)/" -e "s/(nwell )/(nwell)/" -e "s/(pwell )/(pwell)/" > objs/SUBCIFin
rm -f objs/SUBCIFout
gcc -E -x c -DSUBMICRON cifout.c | sed -e "/^#/D" -e "s/(gen )/(gen)/" -e "s/(nowell )/(nowell)/" -e "s/(nwell )/(nwell)/" -e "s/(pwell )/(pwell)/" > objs/SUBCIFout
make[3]: Leaving directory `/home/geng/Desktop/magic-7.5.151/scmos/cif_template'
/usr/bin/m4 minimum.tech.m4 > minimum.tech
/usr/bin/m4 gdsquery.tech.m4 > gdsquery.tech
gcc -E -x c -I./extract_template -DV5 -DSTANDARD scmos.tech.in > scmos.tech
gcc -E -x c -I./extract_template -DV5 -DHPTECH -DTIGHTMETAL scmos.tech.in > scmos-tm.tech
gcc -E -x c -I./extract_template -DV5 -DSUBMICRON scmos.tech.in > scmos-sub.tech
gcc -E -x c -I./extract_template -DV5 -DSTANDARD -DWELL_ROUTE_CHECK scmos.tech.in > scmosWR.tech
for i in mos.7bit.dstyle mos.7bit.std.cmap mos.24bit.dstyle mos.24bit.std.cmap mos.7bit.mraster_dstyle mos.7bit.mraster.cmap mos.OpenGL.dstyle mos.OpenGL.std.cmap minimum.tech gdsquery.tech scmos.tech scmos-tm.tech scmos-sub.tech scmosWR.tech; do \
		cp $i /usr/local/lib/magic/sys; done
make[2]: Leaving directory `/home/geng/Desktop/magic-7.5.151/scmos'
make[1]: Leaving directory `/home/geng/Desktop/magic-7.5.151'



Please help, thanks.

---

### Post by prshah on 2008-10-16
> **geng said:**
> 
/bin/bash: ./scripts/makedbh: /bin/csh: bad interpreter: No such file or directory

Here's a couple of wild suggestions; It seems to be failing because it cannot find "csh"-"C Shell". As far as I know, Ubuntu uses bash for scripts. So try:

a) Install csh ```
sudo apt-get install csh
```

OR

b) Change the shell used:```
SHELL=/bin/bash ./configure
```

OR

c) create a link from bash to csh```
sudo ln -s /bin/bash /bin/csh
```

---

### Post by geng on 2008-10-16
> **prshah said:**
> Here's a couple of wild suggestions; It seems to be failing because it cannot find "csh"-"C Shell". As far as I know, Ubuntu uses bash for scripts. So try:

a) Install csh ```
sudo apt-get install csh
```

OR

b) Change the shell used:```
SHELL=/bin/bash ./configure
```

OR

c) create a link from bash to csh```
sudo ln -s /bin/bash /bin/csh
```

thanks very much.

---

