---
title: "Trying to install a program from source"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by thebrotherofasis on 2009-12-20
I noticed the chess database program "Scid" is way more up-to-date from source than in the repos.

So, I am trying to install it by following the steps below, but I am stuck after doing ./configure

> 1. Download it at [http://scid.sourceforge.net/download.html](http://scid.sourceforge.net/download.html)
2. Extract it

cd ~/Downloads/
tar xjvf scid-4.0.tar.bz2
mv scid /usr/local/src/

3. Compile and install
cd /usr/local/src/scid
./configure

> I get the following

configure: Makefile configuration program for Scid
    Renaming "Makefile" to "Makefile.bak"
    Tcl/Tk version: 8.5
    Your operating system is: Linux 2.6.31-16-generic
    Location of "tcl.h": not found
    Location of "tk.h": not found
    Location of Tcl 8.5 library: /usr/lib
    Location of Tk 8.5 library: /usr/lib
    Location of X11 library: /usr/lib
    Checking if your system already has zlib installed: no.
Not all settings could be determined!
The default Makefile was written.
You will need to edit it before you can compile Scid.

If I do

```
make
```

I get 

> make: *** [src/stored.o] Error 1

The thing is I really don't know if this is a problem of dependencies or something else, since it says

> The default Makefile was written.
You will need to edit it before you can compile Scid

I tried installing 

```
sudo apt-get remove zlibc
```

But no luck.

:confused:

When I 

> gedit Makefile

I see

> ##### Makefile for Scid for Unix operating systems.

### Compiler: Most Unix systems use g++ for compiling and linking.
#
COMPILE = g++
CC = gcc
LINK = g++
DESTDIR =

# BINDIR: where the Scid programs are copied for "make install".
#
BINDIR = /usr/local/bin

# SHAREDIR: where scid.eco is copied for "make install".
#
SHAREDIR = /usr/local/share/scid

### TCL_VERSION: Set this according to the version of Tcl/Tk you have
#   installed that you want Scid to use: 8.0, 8.1, 8.2, 8.3, etc.
#
TCL_VERSION = 8.5

# TCL_INCLUDE, TCL_LIBRARY, TK_LIBRARY: these are the compiler options
#    needed for linking Scid with Tcl/Tk.  The program "./configure"
#    will try to determine them automatically, but if it cannot, you
#    can use the examples below for help in setting these variables.
#
# Sorry, "./configure" was not successful. The default settings are:
#
TCL_INCLUDE = -I/usr/include
TCL_LIBRARY = -L/usr/lib -ltcl$(TCL_VERSION) -ldl
TK_LIBRARY  = $(TCL_LIBRARY) -ltk$(TCL_VERSION) -L/usr/X11R6/lib -lX11

### Here are other commonly used settings for the Tcl/Tk compiler options:

### Linux (Red Hat and other distributions):
# TCL_INCLUDE = -I /usr/include
# TCL_LIBRARY = -L /usr/lib -ltcl$(TCL_VERSION) -ldl
# TK_LIBRARY  = $(TCL_LIBRARY) -ltk$(TCL_VERSION) -L /usr/X11R6/lib -lX11

### Solaris:
# TCL_INCLUDE = -I /usr/local/tcl/include
# TCL_LIBRARY = -L /usr/local/tcl/lib -ltcl$(TCL_VERSION) -ldl
# TK_LIBRARY  = $(TCL_LIBRARY) -ltk$(TCL_VERSION)

# Someone sent me these settings for SuSE Linux 6.1:
### Linux (SuSE distribution):
# TCL_INCLUDE = -I /usr/X11R6/include
# TCL_LIBRARY = -L /usr/lib -ltcl$(TCL_VERSION) -ldl
# TK_LIBRARY  = $(TCL_LIBRARY) -L /usr/X11R6/lib -ltk$(TCL_VERSION) -lX11

# Someone sent me these settings for FreeBSD with Tcl/Tk 8.0:
### FreeBSD:
# TCL_INCLUDE = -I /usr/local/include/tcl8.0 -I /usr/local/include/tk8.0
# TCL_LIBRARY = -L /usr/local/lib -ltcl80 -ldl
# TK_LIBRARY  = $(TCL_LIBRARY) -ltk80 -L /usr/X11/lib -lX11


########################################
### Compiler options:

### TB: Using Nalimov tablebases with Scid. Use "TB = -DSCID_USE_TB" for 
#      tablebase support, or just "TB = " for no tablebase capability.
#      Use "TB = -DSCID_USE_TB -DT41_INCLUDE" to include use of 4-1
#      (King + 3 pieces vs lone king) tablebases.
#
TB = -DSCID_USE_TB -DT41_INCLUDE

### SCIDFLAGS: Scid customization flags.
#      Use -DZLIB if your system does not have zlib and you need
#      to include the code in the src/zlib directory.
#      The default is to use the system zlib library.
#
SCIDFLAGS =  -DZLIB

### OPTIMIZE: Optimization options for C++ compiler.
#      -O4 is the most optimization for g++. I have found -O2 to do
#      just as well, but someone reported a noticable difference in speed
#      between -O4 and -O2 so the default here is -O4.
#      On some systems, adding "-fno-rtti" and "-fno-exceptions" produces
#      smaller, faster programs since Scid does not use those C++ features.
#
OPTIMIZE = -O4 -fno-rtti -fno-exceptions

### DEBUG: Defining the macro ASSERTIONS will turn on assertions, which
#       helps to track bugs after modifications, but the programs will run 
#       a little faster with assertions turned off.
#
DEBUG = #-DASSERTIONS

### WARNINGS: I always compile with all warnings on (-Wall), and all the
#       files should compile warning-free using g++.
#
WARNINGS = -Wall

### PROFILE: Set this to "-pg" for profiling in g++ and gcc.
#
PROFILE = 

### CPP_FLAGS: Flags for C++ compilation.
#
CPP_FLAGS = $(PROFILE) $(OPTIMIZE) $(WARNINGS) $(DEBUG) $(SCIDFLAGS)

### CFLAGS: Flags for C compilation (only used for compiling zlib).
#
CFLAGS = -O2 -Wall $(PROFILE)

### LANGUAGES: List of additional Tcl files to include in Scid for
#       multi-language menu support.
#       By default, it is all the contributed languages, but you
#       can reduce the size of the Scid program by only specifying
#       the languages you want supported.
#
LANGUAGES = tcl/lang/deutsch.tcl tcl/lang/francais.tcl tcl/lang/italian.tcl tcl/lang/nederlan.tcl tcl/lang/spanish.tcl tcl/lang/portbr.tcl tcl/lang/swedish.tcl tcl/lang/norsk.tcl tcl/lang/polish.tcl tcl/lang/czech.tcl tcl/lang/hungary.tcl tcl/lang/serbian.tcl tcl/lang/catalan.tcl tcl/lang/russian.tcl


############################################################
#
# You should not need to edit anything below this line.
#
############################################################

### EXECS: executable programs compiled from C++ files.
#     Note: scidt and eco2epd are obsolete and not compiled by default.
#			PG : put back scidt has it appears to be useful in certain cases
#
EXECS= pgnscid tkscid tcscid scmerge scidlet scidt

### SCIDOBJS: not all the .o files that make up Scid, just the standard ones 
#     that most of the programs include.
#
SCIDOBJS= src/misc.o src/index.o src/date.o src/namebase.o src/position.o \
      src/game.o src/gfile.o src/matsig.o src/bytebuf.o src/textbuf.o \
      src/myassert.o src/stralloc.o src/mfile.o src/dstring.o src/pgnparse.o \
      src/stored.o src/movelist.o \
			src/polyglot/attack.o src/polyglot/board.o src/polyglot/book.o \
			src/polyglot/book_make.o src/polyglot/book_merge.o src/polyglot/colour.o \
      src/polyglot/fen.o src/polyglot/game.o src/polyglot/hash.o \
      src/polyglot/io.o src/polyglot/line.o src/polyglot/list.o src/polyglot/main.o src/polyglot/move.o \
      src/polyglot/move_do.o src/polyglot/move_gen.o src/polyglot/move_legal.o src/polyglot/option.o \
      src/polyglot/parse.o src/polyglot/pgn.o src/polyglot/piece.o src/polyglot/random.o \
      src/polyglot/san.o src/polyglot/search.o src/polyglot/square.o src/polyglot/util.o

### ZLIBOBJS: object files in the zlib compression library.
#
ZLIBOBJS= src/zlib/adler32.o src/zlib/compress.o src/zlib/crc32.o \
      src/zlib/gzio.o src/zlib/uncompr.o src/zlib/deflate.o src/zlib/trees.o \
      src/zlib/zutil.o src/zlib/inflate.o src/zlib/infblock.o \
      src/zlib/inftrees.o src/zlib/infcodes.o src/zlib/infutil.o \
      src/zlib/inffast.o

       
### ZLIB: Should be "-lz" if your system has zlib, "" otherwise.
#
ZLIB = 

### OBJS: Will be "$(SCIDOBJS)", "$(POLYGLOTOBJS)", and also "$(ZLIBOBJS)" if they are
#      needed on your system.
OBJS= $(SCIDOBJS) $(ZLIBOBJS)

### TCLS: all the .tcl files that make up "scid".
#
TCLS= \
  tcl/start.tcl \
  tcl/config.tcl \
  tcl/bitmaps.tcl \
  tcl/language.tcl \
  tcl/utils.tcl \
    tcl/utils/date.tcl tcl/utils/font.tcl tcl/utils/graph.tcl tcl/utils/history.tcl \
    tcl/utils/pane.tcl tcl/utils/sound.tcl tcl/utils/string.tcl tcl/utils/tooltip.tcl \
    tcl/utils/validate.tcl tcl/utils/win.tcl \
  tcl/misc/misc.tcl tcl/htext.tcl \
  tcl/file.tcl \
    tcl/file/finder.tcl tcl/file/bookmark.tcl tcl/file/recent.tcl tcl/file/epd.tcl \
    tcl/file/spellchk.tcl tcl/file/maint.tcl \
  tcl/edit.tcl \
  tcl/game.tcl \
    tcl/game/browser.tcl \
  tcl/windows.tcl \
    tcl/windows/gamelist.tcl tcl/windows/pgn.tcl tcl/windows/book.tcl \
    tcl/windows/comment.tcl tcl/windows/eco.tcl \
    tcl/windows/stats.tcl tcl/windows/tree.tcl tcl/windows/crosstab.tcl \
    tcl/windows/pfinder.tcl tcl/windows/tourney.tcl tcl/windows/switcher.tcl \
  tcl/search/search.tcl \
    tcl/search/board.tcl tcl/search/header.tcl tcl/search/material.tcl \
  tcl/contrib/ezsmtp/ezsmtp.tcl \
    tcl/tools/email.tcl \
    tcl/tools/import.tcl \
    tcl/tools/optable.tcl tcl/tools/preport.tcl tcl/tools/pinfo.tcl \
    tcl/tools/analysis.tcl tcl/tools/wbdetect.tcl \
    tcl/tools/reper.tcl tcl/tools/graphs.tcl tcl/tools/tablebase.tcl tcl/tools/ptracker.tcl \
  tcl/help/help.tcl tcl/help/tips.tcl \
  tcl/menus.tcl tcl/board.tcl tcl/move.tcl tcl/main.tcl tcl/tools/correspondence.tcl \
    tcl/lang/english.tcl $(LANGUAGES) \
  tcl/tools/uci.tcl tcl/end.tcl tcl/tools/tacgame.tcl tcl/tools/sergame.tcl tcl/tools/calvar.tcl tcl/tools/fics.tcl tcl/tools/opening.tcl tcl/tools/tactics.tcl tcl/tools/reviewgame.tcl tcl/utils/metadata.tcl  tcl/tools/inputengine.tcl tcl/tools/novag.tcl tcl/misc/flags.tcl 


### SCRIPTS:
# Small extra programs. Most are written in Tcl using tcscid, but
# a few contributed ones may be in Python or other languages.
#
SCRIPTS= sc_addmove sc_epgn sc_spell sc_eco sc_import sc_remote sc_tree scidpgn pgnfix spliteco spf2spi

####################

### Type "make" or "make all" to make all programs:
#
all: all_scid all_engines

all_scid: scid $(SCRIPTS) $(EXECS)

all_engines: phalanx-scid toga

phalanx-scid:
	cd engines/phalanx-scid/ && $(MAKE) && cd ../../

toga:
	cd engines/togaII1.2.1a/src/ && $(MAKE) && cd ../../

### To copy all executables to $BINDIR, with read and execute permission 
#   for all users, and put extra files in $SHAREDIR, type "make install".
#

install: install_scid install_engines

install_scid: all_scid
	install -m 755 -d $(DESTDIR)$(SHAREDIR)
	install -m 755 -d $(DESTDIR)$(BINDIR)
	install -m 755 -d $(DESTDIR)$(SHAREDIR)/data/
	install -m 755 scid $(SCRIPTS) $(EXECS) $(DESTDIR)$(BINDIR)
	install -m 644 -p scid.eco $(DESTDIR)$(SHAREDIR)/data/
	install -m 755 -d $(DESTDIR)$(SHAREDIR)/books
	install -m 666 ./books/*.* $(DESTDIR)$(SHAREDIR)/books/
	install -m 755 -d $(DESTDIR)$(SHAREDIR)/bases
	install -m 666 ./bases/*.* $(DESTDIR)$(SHAREDIR)/bases/
	install -m 755 -d $(DESTDIR)$(SHAREDIR)/html
	cp -r ./html/* $(DESTDIR)$(SHAREDIR)/html/

install_engines: all_engines
	install -m 755 -d $(SHAREDIR)/engines
	install -m 755 -d $(SHAREDIR)/engines/phalanx-scid
	install ./engines/phalanx-scid/phalanx-scid $(SHAREDIR)/engines/phalanx-scid
	install -m 755 -d $(SHAREDIR)/engines/togaII1.2.1a
	install ./engines/togaII1.2.1a/src/togaII $(SHAREDIR)/engines/togaII1.2.1a/

uninstall:
	rm -rf $(SHAREDIR)/engines
	rm -rf $(SHAREDIR)/books
	rm -rf $(SHAREDIR)/bases
	rm -rf $(SHAREDIR)/data/
	rm -f $(SHAREDIR)/data/scid.eco
	rm -f $(BINDIR)/scid $(BINDIR)/sc_addmove $(BINDIR)/sc_epgn
	rm -f $(BINDIR)/sc_spell $(BINDIR)/sc_eco $(BINDIR)/sc_import
	rm -f $(BINDIR)/sc_remote $(BINDIR)/sc_tree $(BINDIR)/scidpgn
	rm -f $(BINDIR)/pgnfix $(BINDIR)/spliteco
	rm -f $(BINDIR)/pgnscid $(BINDIR)/tkscid $(BINDIR)/tcscid
	rm -f $(BINDIR)/scmerge $(BINDIR)/scidlet
	rm -rf $(SHAREDIR)/html
	
### To remove Scid files placed in the BINDIR and SHAREDIR directories,
#   type "make distclean".
#
distclean:
	cd $(BINDIR) && rm -f $(EXECS) $(SCRIPTS)
	-rm -f $(SHAREDIR)/scid.eco

### To remove object and executable files: type "make clean".
#
clean:
	rm -f game.* learn* tkscid.so tkscid.dll position.* src/*.o src/zlib/*.o src/zlib/*.a src/polyglot/*.o $(EXECS) scid $(SCRIPTS)
	cd engines/phalanx-scid/ && make clean && cd ../../
	cd engines/togaII1.2.1a/src/ && make clean && cd ../../../
	cd pocket/toga/src/ && make clean && cd ../../../
	cd pocket/toga134/src/ && make clean && cd ../../../
#	cd pocket/toga141SE/src/ && make clean && cd ../../../
	cd pocket/fruit_21/src/ && make clean && cd ../../../
	cd pocket/gambitfruit/src/ && make clean && cd ../../../
	cd pocket/glaurung/src/ && make clean && cd ../../../
	cd pocket/phalanx/src/ && make clean && cd ../../../
	cd pocket/scorpio/src/ && make clean && cd ../../../
	cd pocket/viper01/src/ && make clean && cd ../../../
	cd pocket/greko/src/ && make clean && cd ../../../
	cd pocket/scidlet/src/ && make clean && cd ../../../
	rm -f pocket/toga.exe pocket/glaurung.exe
	rm -rf pocket/scid_pocket

### To make the executable files smaller: type "make strip".
#
strip:
	strip $(EXECS)

### To compress scid and executables with gzexe: type "make gzexe".
#
gzexe:
	gzexe $(EXECS) scid


scid: $(TCLS)
	rm -f ./scid
	cat $(TCLS) > ./scid
	chmod +x scid

sc_addmove: scripts/sc_addmove.tcl
	cp scripts/sc_addmove.tcl ./sc_addmove
	chmod +x sc_addmove

sc_epgn: scripts/sc_epgn.tcl
	cp scripts/sc_epgn.tcl ./sc_epgn
	chmod +x sc_epgn

sc_spell: scripts/sc_spell.tcl
	cp scripts/sc_spell.tcl ./sc_spell
	chmod +x sc_spell

sc_eco: scripts/sc_eco.tcl
	cp scripts/sc_eco.tcl ./sc_eco
	chmod +x sc_eco

sc_import: scripts/sc_import.tcl
	cp scripts/sc_import.tcl ./sc_import
	chmod +x sc_import

sc_remote: scripts/sc_remote.tk
	cp scripts/sc_remote.tk ./sc_remote
	chmod +x sc_remote

sc_tree: scripts/sc_tree.tcl
	cp scripts/sc_tree.tcl ./sc_tree
	chmod +x sc_tree

sc_maketree: scripts/sc_maketree.tcl
	cp scripts/sc_maketree.tcl ./sc_maketree
	chmod +x sc_maketree

scidpgn: scripts/scidpgn.tcl
	cp scripts/scidpgn.tcl ./scidpgn
	chmod +x scidpgn

spliteco: scripts/spliteco.tcl
	cp scripts/spliteco.tcl ./spliteco
	chmod +x spliteco

tbstats: scripts/tbstats.tcl
	cp scripts/tbstats.tcl ./tbstats
	chmod +x tbstats

wmtest: scripts/wmtest.tk
	cp scripts/wmtest.tk ./wmtest
	chmod +x wmtest

pgnfix: scripts/pgnfix.py
	cp scripts/pgnfix.py ./pgnfix
	chmod +x pgnfix

eco2pgn: scripts/eco2pgn.py
	cp scripts/eco2pgn.py ./eco2pgn
	chmod +x eco2pgn

twic2pgn: scripts/twic2pgn.py
	cp scripts/twic2pgn.py ./twic2pgn
	chmod +x twic2pgn

spf2spi: scripts/spf2spi.tcl
	cp scripts/spf2spi.tcl ./spf2spi
	chmod +x spf2spi

scmerge: src/scmerge.o src/misc.o src/index.o src/date.o src/namebase.o \
          src/gfile.o src/bytebuf.o src/textbuf.o src/myassert.o \
          src/stralloc.o src/position.o
	$(LINK) -o scmerge src/scmerge.o $(OBJS) $(ZLIB)

pgnscid: src/pgnscid.o $(OBJS)
	$(LINK) $(PROFILE) -o pgnscid src/pgnscid.o $(OBJS) $(ZLIB)

scidlet: src/scidlet.o src/engine.o src/recog.o src/misc.o src/position.o \
          src/dstring.o src/movelist.o
	$(LINK) -o scidlet src/scidlet.o src/engine.o src/recog.o src/misc.o src/position.o src/movelist.o src/dstring.o

scidt: src/scidt.o $(OBJS)
	$(LINK) -o scidt src/scidt.o $(OBJS) $(ZLIB)

tkscid: src/tkscid.o $(OBJS) src/tree.o src/filter.o src/pbook.o src/crosstab.o \
          src/spellchk.o src/probe.o src/optable.o src/engine.o src/recog.o
	$(LINK) -o tkscid src/tkscid.o $(OBJS) src/tree.o src/filter.o src/pbook.o src/crosstab.o src/spellchk.o src/probe.o src/optable.o src/engine.o src/recog.o $(ZLIB) $(TK_LIBRARY)

tcscid: src/tcscid.o $(OBJS) src/tree.o src/filter.o src/pbook.o src/crosstab.o \
          src/spellchk.o src/probe.o src/optable.o src/engine.o src/recog.o
	$(LINK) -o tcscid src/tcscid.o $(OBJS) src/tree.o src/filter.o src/pbook.o src/crosstab.o src/spellchk.o src/probe.o src/optable.o src/engine.o src/recog.o $(ZLIB) $(TCL_LIBRARY)

# eco2epd is now optional extra program NOT compiled by default, since
# scid now reads the .eco file format directly.
eco2epd: src/eco2epd.o $(OBJS) src/pbook.o
	$(LINK) -o eco2epd src/eco2epd.o $(OBJS) src/pbook.o $(ZLIB)

### Rules to create .o files from .cpp files:
#
src/tcscid.o: src/tkscid.cpp
	$(COMPILE) $(CPP_FLAGS) $(TCL_INCLUDE) -DTCL_ONLY -o src/tcscid.o -c src/tkscid.cpp

src/tkscid.o: src/tkscid.cpp
	$(COMPILE) $(CPP_FLAGS) $(TCL_INCLUDE) -o src/tkscid.o -c src/tkscid.cpp

### The endgame tablebase code in the egtb/ subdirectory (not written by me)
#   gives many warnings, so compile probe.cpp with warnings turned off:
#
src/probe.o: src/probe.cpp src/egtb/tbindex.cpp src/egtb/tbdecode.c
	$(COMPILE) $(PROFILE) $(OPTIMIZE) $(DEBUG) $(SCIDFLAGS) $(TB) -o src/probe.o -c src/probe.cpp

### Generic rule for all other .cpp files:
#
%.o: %.cpp
	$(COMPILE) $(CPP_FLAGS) $(TCL_INCLUDE) -o $@ -c $<

### Rule for compiling zlib source files:
#
src/zlib/%.o: src/zlib/%.c
	$(CC) $(CFLAGS) -o $@ -c $<

#####
# Main Dependencies
# src/.depend:
#	$(COMPILE) $(CPP_FLAGS) $(TCL_INCLUDE) -MM $(SCIDOBJS:.o=.cpp) > $@
#####
src/misc.o: src/misc.cpp src/common.h src/tclmy.h src/myassert.h src/error.h \
  src/sqmove.h src/misc.h
src/index.o: src/index.cpp src/common.h src/tclmy.h src/myassert.h \
  src/error.h src/sqmove.h src/index.h src/matsig.h src/namebase.h \
  src/date.h src/misc.h src/stralloc.h src/strtree.h src/mfile.h \
  src/dstring.h src/game.h src/position.h src/movelist.h src/sqlist.h \
  src/sqset.h src/tokens.h src/textbuf.h src/bytebuf.h src/stored.h
src/date.o: src/date.cpp src/common.h src/tclmy.h src/myassert.h src/error.h \
  src/sqmove.h src/date.h src/misc.h
src/namebase.o: src/namebase.cpp src/common.h src/tclmy.h src/myassert.h \
  src/error.h src/sqmove.h src/namebase.h src/date.h src/misc.h \
  src/stralloc.h src/strtree.h
src/position.o: src/position.cpp src/common.h src/tclmy.h src/myassert.h \
  src/error.h src/sqmove.h src/position.h src/dstring.h src/misc.h \
  src/movelist.h src/sqlist.h src/sqset.h src/tokens.h src/attacks.h \
  src/hash.h
src/game.o: src/game.cpp src/common.h src/tclmy.h src/myassert.h src/error.h \
  src/sqmove.h src/game.h src/date.h src/index.h src/matsig.h \
  src/namebase.h src/misc.h src/stralloc.h src/strtree.h src/mfile.h \
  src/dstring.h src/position.h src/movelist.h src/sqlist.h src/sqset.h \
  src/tokens.h src/textbuf.h src/bytebuf.h src/gfile.h src/pgnparse.h \
  src/naglatex.h src/nagtext.h src/stored.h
src/gfile.o: src/gfile.cpp src/common.h src/tclmy.h src/myassert.h \
  src/error.h src/sqmove.h src/gfile.h src/bytebuf.h src/mfile.h \
  src/dstring.h src/misc.h
src/matsig.o: src/matsig.cpp src/matsig.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h
src/bytebuf.o: src/bytebuf.cpp src/error.h src/bytebuf.h src/common.h \
  src/tclmy.h src/myassert.h src/sqmove.h
src/textbuf.o: src/textbuf.cpp src/error.h src/textbuf.h src/common.h \
  src/tclmy.h src/myassert.h src/sqmove.h src/misc.h
src/myassert.o: src/myassert.cpp src/myassert.h
src/stralloc.o: src/stralloc.cpp src/stralloc.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h src/misc.h
src/mfile.o: src/mfile.cpp src/common.h src/tclmy.h src/myassert.h \
  src/error.h src/sqmove.h src/mfile.h src/dstring.h src/misc.h
src/dstring.o: src/dstring.cpp src/dstring.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h src/misc.h src/mfile.h
src/pgnparse.o: src/pgnparse.cpp src/pgnparse.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h src/tokens.h src/game.h \
  src/date.h src/index.h src/matsig.h src/namebase.h src/misc.h \
  src/stralloc.h src/strtree.h src/mfile.h src/dstring.h src/position.h \
  src/movelist.h src/sqlist.h src/sqset.h src/textbuf.h src/bytebuf.h
src/stored.o: src/stored.cpp src/stored.h src/game.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h src/date.h src/index.h \
  src/matsig.h src/namebase.h src/misc.h src/stralloc.h src/strtree.h \
  src/mfile.h src/dstring.h src/position.h src/movelist.h src/sqlist.h \
  src/sqset.h src/tokens.h src/textbuf.h src/bytebuf.h src/pgnparse.h \
  src/timer.h src/tkscid.h src/engine.h src/gfile.h src/tree.h \
  src/filter.h src/pbook.h src/crosstab.h src/spellchk.h src/probe.h \
  src/optable.h src/polyglot.h
src/movelist.o: src/movelist.cpp src/movelist.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h src/misc.h

### End of Makefile

This is my second attempt to compile a program from source. (The first one was successful :) since it didn't need any dependencies being solved)

I am following this guide [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

But so far no success.

Any help is greatly appreciated. Thanks.

---

### Post by oldos2er on 2009-12-20
"Checking if your system already has zlib installed: no."

Try installing libghc6-zlib-dev, then retry ./configure

---

### Post by thebrotherofasis on 2009-12-21
> **oldos2er said:**
> "Checking if your system already has zlib installed: no."

Try installing libghc6-zlib-dev, then retry ./configure

Alright, now it finds it > Checking if your system already has zlib installed: yes.

However, when I do ./configure it still doesn't find the other requirenments, and "make" fails to succeed

```
user@user-laptop:/usr/local/src/scid$ ./configure
configure: Makefile configuration program for Scid
    Renaming "Makefile" to "Makefile.bak"
    Tcl/Tk version: 8.5
    Your operating system is: Linux 2.6.31-16-generic
    Location of "tcl.h": not found
    Location of "tk.h": not found
    Location of Tcl 8.5 library: /usr/lib
    Location of Tk 8.5 library: /usr/lib
    Location of X11 library: /usr/lib
    Checking if your system already has zlib installed: yes.
Not all settings could be determined!
The default Makefile was written.
You will need to edit it before you can compile Scid.
```

Here are the results of make

> g++  -O4 -fno-rtti -fno-exceptions -Wall   -I/usr/include -o src/stored.o -c src/stored.cpp
In file included from src/stored.cpp:328:
src/tkscid.h:57:17: error: tcl.h: No such file or directory
src/tkscid.h:59:18: error: tk.h: No such file or directory
In file included from src/stored.cpp:328:
src/tkscid.h:196: error: ‘setResult’ declared as an ‘inline’ variable
src/tkscid.h:196: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:196: error: ‘ti’ was not declared in this scope
src/tkscid.h:196: error: expected primary-expression before ‘const’
src/tkscid.h:196: error: initializer expression list treated as compound expression
src/tkscid.h:197: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:210: error: ‘errorResult’ declared as an ‘inline’ variable
src/tkscid.h:210: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:210: error: ‘ti’ was not declared in this scope
src/tkscid.h:210: error: expected primary-expression before ‘const’
src/tkscid.h:210: error: initializer expression list treated as compound expression
src/tkscid.h:211: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:221: error: ‘setBoolResult’ declared as an ‘inline’ variable
src/tkscid.h:221: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:221: error: ‘ti’ was not declared in this scope
src/tkscid.h:221: error: expected primary-expression before ‘bool’
src/tkscid.h:221: error: initializer expression list treated as compound expression
src/tkscid.h:222: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:232: error: ‘setIntResult’ declared as an ‘inline’ variable
src/tkscid.h:232: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:232: error: ‘ti’ was not declared in this scope
src/tkscid.h:232: error: expected primary-expression before ‘int’
src/tkscid.h:232: error: initializer expression list treated as compound expression
src/tkscid.h:233: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:245: error: ‘setUintResult’ declared as an ‘inline’ variable
src/tkscid.h:245: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:245: error: ‘ti’ was not declared in this scope
src/tkscid.h:245: error: expected primary-expression before ‘i’
src/tkscid.h:245: error: initializer expression list treated as compound expression
src/tkscid.h:246: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:258: error: ‘appendIntResult’ declared as an ‘inline’ variable
src/tkscid.h:258: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:258: error: ‘ti’ was not declared in this scope
src/tkscid.h:258: error: expected primary-expression before ‘int’
src/tkscid.h:258: error: initializer expression list treated as compound expression
src/tkscid.h:259: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:271: error: ‘appendUintResult’ declared as an ‘inline’ variable
src/tkscid.h:271: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:271: error: ‘ti’ was not declared in this scope
src/tkscid.h:271: error: expected primary-expression before ‘i’
src/tkscid.h:271: error: initializer expression list treated as compound expression
src/tkscid.h:272: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:284: error: ‘appendUintElement’ declared as an ‘inline’ variable
src/tkscid.h:284: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:284: error: ‘ti’ was not declared in this scope
src/tkscid.h:284: error: expected primary-expression before ‘i’
src/tkscid.h:284: error: initializer expression list treated as compound expression
src/tkscid.h:285: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:297: error: ‘setUintWidthResult’ declared as an ‘inline’ variable
src/tkscid.h:297: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:297: error: ‘ti’ was not declared in this scope
src/tkscid.h:297: error: expected primary-expression before ‘i’
src/tkscid.h:297: error: expected primary-expression before ‘width’
src/tkscid.h:297: error: initializer expression list treated as compound expression
src/tkscid.h:298: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:309: error: ‘setCharResult’ declared as an ‘inline’ variable
src/tkscid.h:309: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:309: error: ‘ti’ was not declared in this scope
src/tkscid.h:309: error: expected primary-expression before ‘char’
src/tkscid.h:309: error: initializer expression list treated as compound expression
src/tkscid.h:310: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:323: error: ‘appendCharResult’ declared as an ‘inline’ variable
src/tkscid.h:323: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:323: error: ‘ti’ was not declared in this scope
src/tkscid.h:323: error: expected primary-expression before ‘char’
src/tkscid.h:323: error: initializer expression list treated as compound expression
src/tkscid.h:324: error: expected ‘,’ or ‘;’ before ‘{’ token
src/tkscid.h:339: error: ‘translate’ declared as an ‘inline’ variable
src/tkscid.h:339: error: ‘Tcl_Interp’ was not declared in this scope
src/tkscid.h:339: error: ‘ti’ was not declared in this scope
src/tkscid.h:339: error: expected primary-expression before ‘const’
src/tkscid.h:339: error: expected primary-expression before ‘const’
src/tkscid.h:339: error: initializer expression list treated as compound expression
src/tkscid.h:340: error: expected ‘,’ or ‘;’ before ‘{’ token
make: *** [src/stored.o] Error 1


And here's what Makefile shows

> ##### Makefile for Scid for Unix operating systems.

### Compiler: Most Unix systems use g++ for compiling and linking.
#
COMPILE = g++
CC = gcc
LINK = g++
DESTDIR =

# BINDIR: where the Scid programs are copied for "make install".
#
BINDIR = /usr/local/bin

# SHAREDIR: where scid.eco is copied for "make install".
#
SHAREDIR = /usr/local/share/scid

### TCL_VERSION: Set this according to the version of Tcl/Tk you have
#   installed that you want Scid to use: 8.0, 8.1, 8.2, 8.3, etc.
#
TCL_VERSION = 8.5

# TCL_INCLUDE, TCL_LIBRARY, TK_LIBRARY: these are the compiler options
#    needed for linking Scid with Tcl/Tk.  The program "./configure"
#    will try to determine them automatically, but if it cannot, you
#    can use the examples below for help in setting these variables.
#
# Sorry, "./configure" was not successful. The default settings are:
#
TCL_INCLUDE = -I/usr/include
TCL_LIBRARY = -L/usr/lib -ltcl$(TCL_VERSION) -ldl
TK_LIBRARY  = $(TCL_LIBRARY) -ltk$(TCL_VERSION) -L/usr/X11R6/lib -lX11

### Here are other commonly used settings for the Tcl/Tk compiler options:

### Linux (Red Hat and other distributions):
# TCL_INCLUDE = -I /usr/include
# TCL_LIBRARY = -L /usr/lib -ltcl$(TCL_VERSION) -ldl
# TK_LIBRARY  = $(TCL_LIBRARY) -ltk$(TCL_VERSION) -L /usr/X11R6/lib -lX11

### Solaris:
# TCL_INCLUDE = -I /usr/local/tcl/include
# TCL_LIBRARY = -L /usr/local/tcl/lib -ltcl$(TCL_VERSION) -ldl
# TK_LIBRARY  = $(TCL_LIBRARY) -ltk$(TCL_VERSION)

# Someone sent me these settings for SuSE Linux 6.1:
### Linux (SuSE distribution):
# TCL_INCLUDE = -I /usr/X11R6/include
# TCL_LIBRARY = -L /usr/lib -ltcl$(TCL_VERSION) -ldl
# TK_LIBRARY  = $(TCL_LIBRARY) -L /usr/X11R6/lib -ltk$(TCL_VERSION) -lX11

# Someone sent me these settings for FreeBSD with Tcl/Tk 8.0:
### FreeBSD:
# TCL_INCLUDE = -I /usr/local/include/tcl8.0 -I /usr/local/include/tk8.0
# TCL_LIBRARY = -L /usr/local/lib -ltcl80 -ldl
# TK_LIBRARY  = $(TCL_LIBRARY) -ltk80 -L /usr/X11/lib -lX11


########################################
### Compiler options:

### TB: Using Nalimov tablebases with Scid. Use "TB = -DSCID_USE_TB" for 
#      tablebase support, or just "TB = " for no tablebase capability.
#      Use "TB = -DSCID_USE_TB -DT41_INCLUDE" to include use of 4-1
#      (King + 3 pieces vs lone king) tablebases.
#
TB = -DSCID_USE_TB -DT41_INCLUDE

### SCIDFLAGS: Scid customization flags.
#      Use -DZLIB if your system does not have zlib and you need
#      to include the code in the src/zlib directory.
#      The default is to use the system zlib library.
#
SCIDFLAGS = 

### OPTIMIZE: Optimization options for C++ compiler.
#      -O4 is the most optimization for g++. I have found -O2 to do
#      just as well, but someone reported a noticable difference in speed
#      between -O4 and -O2 so the default here is -O4.
#      On some systems, adding "-fno-rtti" and "-fno-exceptions" produces
#      smaller, faster programs since Scid does not use those C++ features.
#
OPTIMIZE = -O4 -fno-rtti -fno-exceptions

### DEBUG: Defining the macro ASSERTIONS will turn on assertions, which
#       helps to track bugs after modifications, but the programs will run 
#       a little faster with assertions turned off.
#
DEBUG = #-DASSERTIONS

### WARNINGS: I always compile with all warnings on (-Wall), and all the
#       files should compile warning-free using g++.
#
WARNINGS = -Wall

### PROFILE: Set this to "-pg" for profiling in g++ and gcc.
#
PROFILE = 

### CPP_FLAGS: Flags for C++ compilation.
#
CPP_FLAGS = $(PROFILE) $(OPTIMIZE) $(WARNINGS) $(DEBUG) $(SCIDFLAGS)

### CFLAGS: Flags for C compilation (only used for compiling zlib).
#
CFLAGS = -O2 -Wall $(PROFILE)

### LANGUAGES: List of additional Tcl files to include in Scid for
#       multi-language menu support.
#       By default, it is all the contributed languages, but you
#       can reduce the size of the Scid program by only specifying
#       the languages you want supported.
#
LANGUAGES = tcl/lang/deutsch.tcl tcl/lang/francais.tcl tcl/lang/italian.tcl tcl/lang/nederlan.tcl tcl/lang/spanish.tcl tcl/lang/portbr.tcl tcl/lang/swedish.tcl tcl/lang/norsk.tcl tcl/lang/polish.tcl tcl/lang/czech.tcl tcl/lang/hungary.tcl tcl/lang/serbian.tcl tcl/lang/catalan.tcl tcl/lang/russian.tcl


############################################################
#
# You should not need to edit anything below this line.
#
############################################################

### EXECS: executable programs compiled from C++ files.
#     Note: scidt and eco2epd are obsolete and not compiled by default.
#			PG : put back scidt has it appears to be useful in certain cases
#
EXECS= pgnscid tkscid tcscid scmerge scidlet scidt

### SCIDOBJS: not all the .o files that make up Scid, just the standard ones 
#     that most of the programs include.
#
SCIDOBJS= src/misc.o src/index.o src/date.o src/namebase.o src/position.o \
      src/game.o src/gfile.o src/matsig.o src/bytebuf.o src/textbuf.o \
      src/myassert.o src/stralloc.o src/mfile.o src/dstring.o src/pgnparse.o \
      src/stored.o src/movelist.o \
			src/polyglot/attack.o src/polyglot/board.o src/polyglot/book.o \
			src/polyglot/book_make.o src/polyglot/book_merge.o src/polyglot/colour.o \
      src/polyglot/fen.o src/polyglot/game.o src/polyglot/hash.o \
      src/polyglot/io.o src/polyglot/line.o src/polyglot/list.o src/polyglot/main.o src/polyglot/move.o \
      src/polyglot/move_do.o src/polyglot/move_gen.o src/polyglot/move_legal.o src/polyglot/option.o \
      src/polyglot/parse.o src/polyglot/pgn.o src/polyglot/piece.o src/polyglot/random.o \
      src/polyglot/san.o src/polyglot/search.o src/polyglot/square.o src/polyglot/util.o

### ZLIBOBJS: object files in the zlib compression library.
#
ZLIBOBJS= src/zlib/adler32.o src/zlib/compress.o src/zlib/crc32.o \
      src/zlib/gzio.o src/zlib/uncompr.o src/zlib/deflate.o src/zlib/trees.o \
      src/zlib/zutil.o src/zlib/inflate.o src/zlib/infblock.o \
      src/zlib/inftrees.o src/zlib/infcodes.o src/zlib/infutil.o \
      src/zlib/inffast.o

       
### ZLIB: Should be "-lz" if your system has zlib, "" otherwise.
#
ZLIB = -lz

### OBJS: Will be "$(SCIDOBJS)", "$(POLYGLOTOBJS)", and also "$(ZLIBOBJS)" if they are
#      needed on your system.
OBJS= $(SCIDOBJS)

### TCLS: all the .tcl files that make up "scid".
#
TCLS= \
  tcl/start.tcl \
  tcl/config.tcl \
  tcl/bitmaps.tcl \
  tcl/language.tcl \
  tcl/utils.tcl \
    tcl/utils/date.tcl tcl/utils/font.tcl tcl/utils/graph.tcl tcl/utils/history.tcl \
    tcl/utils/pane.tcl tcl/utils/sound.tcl tcl/utils/string.tcl tcl/utils/tooltip.tcl \
    tcl/utils/validate.tcl tcl/utils/win.tcl \
  tcl/misc/misc.tcl tcl/htext.tcl \
  tcl/file.tcl \
    tcl/file/finder.tcl tcl/file/bookmark.tcl tcl/file/recent.tcl tcl/file/epd.tcl \
    tcl/file/spellchk.tcl tcl/file/maint.tcl \
  tcl/edit.tcl \
  tcl/game.tcl \
    tcl/game/browser.tcl \
  tcl/windows.tcl \
    tcl/windows/gamelist.tcl tcl/windows/pgn.tcl tcl/windows/book.tcl \
    tcl/windows/comment.tcl tcl/windows/eco.tcl \
    tcl/windows/stats.tcl tcl/windows/tree.tcl tcl/windows/crosstab.tcl \
    tcl/windows/pfinder.tcl tcl/windows/tourney.tcl tcl/windows/switcher.tcl \
  tcl/search/search.tcl \
    tcl/search/board.tcl tcl/search/header.tcl tcl/search/material.tcl \
  tcl/contrib/ezsmtp/ezsmtp.tcl \
    tcl/tools/email.tcl \
    tcl/tools/import.tcl \
    tcl/tools/optable.tcl tcl/tools/preport.tcl tcl/tools/pinfo.tcl \
    tcl/tools/analysis.tcl tcl/tools/wbdetect.tcl \
    tcl/tools/reper.tcl tcl/tools/graphs.tcl tcl/tools/tablebase.tcl tcl/tools/ptracker.tcl \
  tcl/help/help.tcl tcl/help/tips.tcl \
  tcl/menus.tcl tcl/board.tcl tcl/move.tcl tcl/main.tcl tcl/tools/correspondence.tcl \
    tcl/lang/english.tcl $(LANGUAGES) \
  tcl/tools/uci.tcl tcl/end.tcl tcl/tools/tacgame.tcl tcl/tools/sergame.tcl tcl/tools/calvar.tcl tcl/tools/fics.tcl tcl/tools/opening.tcl tcl/tools/tactics.tcl tcl/tools/reviewgame.tcl tcl/utils/metadata.tcl  tcl/tools/inputengine.tcl tcl/tools/novag.tcl tcl/misc/flags.tcl 


### SCRIPTS:
# Small extra programs. Most are written in Tcl using tcscid, but
# a few contributed ones may be in Python or other languages.
#
SCRIPTS= sc_addmove sc_epgn sc_spell sc_eco sc_import sc_remote sc_tree scidpgn pgnfix spliteco spf2spi

####################

### Type "make" or "make all" to make all programs:
#
all: all_scid all_engines

all_scid: scid $(SCRIPTS) $(EXECS)

all_engines: phalanx-scid toga

phalanx-scid:
	cd engines/phalanx-scid/ && $(MAKE) && cd ../../

toga:
	cd engines/togaII1.2.1a/src/ && $(MAKE) && cd ../../

### To copy all executables to $BINDIR, with read and execute permission 
#   for all users, and put extra files in $SHAREDIR, type "make install".
#

install: install_scid install_engines

install_scid: all_scid
	install -m 755 -d $(DESTDIR)$(SHAREDIR)
	install -m 755 -d $(DESTDIR)$(BINDIR)
	install -m 755 -d $(DESTDIR)$(SHAREDIR)/data/
	install -m 755 scid $(SCRIPTS) $(EXECS) $(DESTDIR)$(BINDIR)
	install -m 644 -p scid.eco $(DESTDIR)$(SHAREDIR)/data/
	install -m 755 -d $(DESTDIR)$(SHAREDIR)/books
	install -m 666 ./books/*.* $(DESTDIR)$(SHAREDIR)/books/
	install -m 755 -d $(DESTDIR)$(SHAREDIR)/bases
	install -m 666 ./bases/*.* $(DESTDIR)$(SHAREDIR)/bases/
	install -m 755 -d $(DESTDIR)$(SHAREDIR)/html
	cp -r ./html/* $(DESTDIR)$(SHAREDIR)/html/

install_engines: all_engines
	install -m 755 -d $(SHAREDIR)/engines
	install -m 755 -d $(SHAREDIR)/engines/phalanx-scid
	install ./engines/phalanx-scid/phalanx-scid $(SHAREDIR)/engines/phalanx-scid
	install -m 755 -d $(SHAREDIR)/engines/togaII1.2.1a
	install ./engines/togaII1.2.1a/src/togaII $(SHAREDIR)/engines/togaII1.2.1a/

uninstall:
	rm -rf $(SHAREDIR)/engines
	rm -rf $(SHAREDIR)/books
	rm -rf $(SHAREDIR)/bases
	rm -rf $(SHAREDIR)/data/
	rm -f $(SHAREDIR)/data/scid.eco
	rm -f $(BINDIR)/scid $(BINDIR)/sc_addmove $(BINDIR)/sc_epgn
	rm -f $(BINDIR)/sc_spell $(BINDIR)/sc_eco $(BINDIR)/sc_import
	rm -f $(BINDIR)/sc_remote $(BINDIR)/sc_tree $(BINDIR)/scidpgn
	rm -f $(BINDIR)/pgnfix $(BINDIR)/spliteco
	rm -f $(BINDIR)/pgnscid $(BINDIR)/tkscid $(BINDIR)/tcscid
	rm -f $(BINDIR)/scmerge $(BINDIR)/scidlet
	rm -rf $(SHAREDIR)/html
	
### To remove Scid files placed in the BINDIR and SHAREDIR directories,
#   type "make distclean".
#
distclean:
	cd $(BINDIR) && rm -f $(EXECS) $(SCRIPTS)
	-rm -f $(SHAREDIR)/scid.eco

### To remove object and executable files: type "make clean".
#
clean:
	rm -f game.* learn* tkscid.so tkscid.dll position.* src/*.o src/zlib/*.o src/zlib/*.a src/polyglot/*.o $(EXECS) scid $(SCRIPTS)
	cd engines/phalanx-scid/ && make clean && cd ../../
	cd engines/togaII1.2.1a/src/ && make clean && cd ../../../
	cd pocket/toga/src/ && make clean && cd ../../../
	cd pocket/toga134/src/ && make clean && cd ../../../
#	cd pocket/toga141SE/src/ && make clean && cd ../../../
	cd pocket/fruit_21/src/ && make clean && cd ../../../
	cd pocket/gambitfruit/src/ && make clean && cd ../../../
	cd pocket/glaurung/src/ && make clean && cd ../../../
	cd pocket/phalanx/src/ && make clean && cd ../../../
	cd pocket/scorpio/src/ && make clean && cd ../../../
	cd pocket/viper01/src/ && make clean && cd ../../../
	cd pocket/greko/src/ && make clean && cd ../../../
	cd pocket/scidlet/src/ && make clean && cd ../../../
	rm -f pocket/toga.exe pocket/glaurung.exe
	rm -rf pocket/scid_pocket

### To make the executable files smaller: type "make strip".
#
strip:
	strip $(EXECS)

### To compress scid and executables with gzexe: type "make gzexe".
#
gzexe:
	gzexe $(EXECS) scid


scid: $(TCLS)
	rm -f ./scid
	cat $(TCLS) > ./scid
	chmod +x scid

sc_addmove: scripts/sc_addmove.tcl
	cp scripts/sc_addmove.tcl ./sc_addmove
	chmod +x sc_addmove

sc_epgn: scripts/sc_epgn.tcl
	cp scripts/sc_epgn.tcl ./sc_epgn
	chmod +x sc_epgn

sc_spell: scripts/sc_spell.tcl
	cp scripts/sc_spell.tcl ./sc_spell
	chmod +x sc_spell

sc_eco: scripts/sc_eco.tcl
	cp scripts/sc_eco.tcl ./sc_eco
	chmod +x sc_eco

sc_import: scripts/sc_import.tcl
	cp scripts/sc_import.tcl ./sc_import
	chmod +x sc_import

sc_remote: scripts/sc_remote.tk
	cp scripts/sc_remote.tk ./sc_remote
	chmod +x sc_remote

sc_tree: scripts/sc_tree.tcl
	cp scripts/sc_tree.tcl ./sc_tree
	chmod +x sc_tree

sc_maketree: scripts/sc_maketree.tcl
	cp scripts/sc_maketree.tcl ./sc_maketree
	chmod +x sc_maketree

scidpgn: scripts/scidpgn.tcl
	cp scripts/scidpgn.tcl ./scidpgn
	chmod +x scidpgn

spliteco: scripts/spliteco.tcl
	cp scripts/spliteco.tcl ./spliteco
	chmod +x spliteco

tbstats: scripts/tbstats.tcl
	cp scripts/tbstats.tcl ./tbstats
	chmod +x tbstats

wmtest: scripts/wmtest.tk
	cp scripts/wmtest.tk ./wmtest
	chmod +x wmtest

pgnfix: scripts/pgnfix.py
	cp scripts/pgnfix.py ./pgnfix
	chmod +x pgnfix

eco2pgn: scripts/eco2pgn.py
	cp scripts/eco2pgn.py ./eco2pgn
	chmod +x eco2pgn

twic2pgn: scripts/twic2pgn.py
	cp scripts/twic2pgn.py ./twic2pgn
	chmod +x twic2pgn

spf2spi: scripts/spf2spi.tcl
	cp scripts/spf2spi.tcl ./spf2spi
	chmod +x spf2spi

scmerge: src/scmerge.o src/misc.o src/index.o src/date.o src/namebase.o \
          src/gfile.o src/bytebuf.o src/textbuf.o src/myassert.o \
          src/stralloc.o src/position.o
	$(LINK) -o scmerge src/scmerge.o $(OBJS) $(ZLIB)

pgnscid: src/pgnscid.o $(OBJS)
	$(LINK) $(PROFILE) -o pgnscid src/pgnscid.o $(OBJS) $(ZLIB)

scidlet: src/scidlet.o src/engine.o src/recog.o src/misc.o src/position.o \
          src/dstring.o src/movelist.o
	$(LINK) -o scidlet src/scidlet.o src/engine.o src/recog.o src/misc.o src/position.o src/movelist.o src/dstring.o

scidt: src/scidt.o $(OBJS)
	$(LINK) -o scidt src/scidt.o $(OBJS) $(ZLIB)

tkscid: src/tkscid.o $(OBJS) src/tree.o src/filter.o src/pbook.o src/crosstab.o \
          src/spellchk.o src/probe.o src/optable.o src/engine.o src/recog.o
	$(LINK) -o tkscid src/tkscid.o $(OBJS) src/tree.o src/filter.o src/pbook.o src/crosstab.o src/spellchk.o src/probe.o src/optable.o src/engine.o src/recog.o $(ZLIB) $(TK_LIBRARY)

tcscid: src/tcscid.o $(OBJS) src/tree.o src/filter.o src/pbook.o src/crosstab.o \
          src/spellchk.o src/probe.o src/optable.o src/engine.o src/recog.o
	$(LINK) -o tcscid src/tcscid.o $(OBJS) src/tree.o src/filter.o src/pbook.o src/crosstab.o src/spellchk.o src/probe.o src/optable.o src/engine.o src/recog.o $(ZLIB) $(TCL_LIBRARY)

# eco2epd is now optional extra program NOT compiled by default, since
# scid now reads the .eco file format directly.
eco2epd: src/eco2epd.o $(OBJS) src/pbook.o
	$(LINK) -o eco2epd src/eco2epd.o $(OBJS) src/pbook.o $(ZLIB)

### Rules to create .o files from .cpp files:
#
src/tcscid.o: src/tkscid.cpp
	$(COMPILE) $(CPP_FLAGS) $(TCL_INCLUDE) -DTCL_ONLY -o src/tcscid.o -c src/tkscid.cpp

src/tkscid.o: src/tkscid.cpp
	$(COMPILE) $(CPP_FLAGS) $(TCL_INCLUDE) -o src/tkscid.o -c src/tkscid.cpp

### The endgame tablebase code in the egtb/ subdirectory (not written by me)
#   gives many warnings, so compile probe.cpp with warnings turned off:
#
src/probe.o: src/probe.cpp src/egtb/tbindex.cpp src/egtb/tbdecode.c
	$(COMPILE) $(PROFILE) $(OPTIMIZE) $(DEBUG) $(SCIDFLAGS) $(TB) -o src/probe.o -c src/probe.cpp

### Generic rule for all other .cpp files:
#
%.o: %.cpp
	$(COMPILE) $(CPP_FLAGS) $(TCL_INCLUDE) -o $@ -c $<

### Rule for compiling zlib source files:
#
src/zlib/%.o: src/zlib/%.c
	$(CC) $(CFLAGS) -o $@ -c $<

#####
# Main Dependencies
# src/.depend:
#	$(COMPILE) $(CPP_FLAGS) $(TCL_INCLUDE) -MM $(SCIDOBJS:.o=.cpp) > $@
#####
src/misc.o: src/misc.cpp src/common.h src/tclmy.h src/myassert.h src/error.h \
  src/sqmove.h src/misc.h
src/index.o: src/index.cpp src/common.h src/tclmy.h src/myassert.h \
  src/error.h src/sqmove.h src/index.h src/matsig.h src/namebase.h \
  src/date.h src/misc.h src/stralloc.h src/strtree.h src/mfile.h \
  src/dstring.h src/game.h src/position.h src/movelist.h src/sqlist.h \
  src/sqset.h src/tokens.h src/textbuf.h src/bytebuf.h src/stored.h
src/date.o: src/date.cpp src/common.h src/tclmy.h src/myassert.h src/error.h \
  src/sqmove.h src/date.h src/misc.h
src/namebase.o: src/namebase.cpp src/common.h src/tclmy.h src/myassert.h \
  src/error.h src/sqmove.h src/namebase.h src/date.h src/misc.h \
  src/stralloc.h src/strtree.h
src/position.o: src/position.cpp src/common.h src/tclmy.h src/myassert.h \
  src/error.h src/sqmove.h src/position.h src/dstring.h src/misc.h \
  src/movelist.h src/sqlist.h src/sqset.h src/tokens.h src/attacks.h \
  src/hash.h
src/game.o: src/game.cpp src/common.h src/tclmy.h src/myassert.h src/error.h \
  src/sqmove.h src/game.h src/date.h src/index.h src/matsig.h \
  src/namebase.h src/misc.h src/stralloc.h src/strtree.h src/mfile.h \
  src/dstring.h src/position.h src/movelist.h src/sqlist.h src/sqset.h \
  src/tokens.h src/textbuf.h src/bytebuf.h src/gfile.h src/pgnparse.h \
  src/naglatex.h src/nagtext.h src/stored.h
src/gfile.o: src/gfile.cpp src/common.h src/tclmy.h src/myassert.h \
  src/error.h src/sqmove.h src/gfile.h src/bytebuf.h src/mfile.h \
  src/dstring.h src/misc.h
src/matsig.o: src/matsig.cpp src/matsig.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h
src/bytebuf.o: src/bytebuf.cpp src/error.h src/bytebuf.h src/common.h \
  src/tclmy.h src/myassert.h src/sqmove.h
src/textbuf.o: src/textbuf.cpp src/error.h src/textbuf.h src/common.h \
  src/tclmy.h src/myassert.h src/sqmove.h src/misc.h
src/myassert.o: src/myassert.cpp src/myassert.h
src/stralloc.o: src/stralloc.cpp src/stralloc.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h src/misc.h
src/mfile.o: src/mfile.cpp src/common.h src/tclmy.h src/myassert.h \
  src/error.h src/sqmove.h src/mfile.h src/dstring.h src/misc.h
src/dstring.o: src/dstring.cpp src/dstring.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h src/misc.h src/mfile.h
src/pgnparse.o: src/pgnparse.cpp src/pgnparse.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h src/tokens.h src/game.h \
  src/date.h src/index.h src/matsig.h src/namebase.h src/misc.h \
  src/stralloc.h src/strtree.h src/mfile.h src/dstring.h src/position.h \
  src/movelist.h src/sqlist.h src/sqset.h src/textbuf.h src/bytebuf.h
src/stored.o: src/stored.cpp src/stored.h src/game.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h src/date.h src/index.h \
  src/matsig.h src/namebase.h src/misc.h src/stralloc.h src/strtree.h \
  src/mfile.h src/dstring.h src/position.h src/movelist.h src/sqlist.h \
  src/sqset.h src/tokens.h src/textbuf.h src/bytebuf.h src/pgnparse.h \
  src/timer.h src/tkscid.h src/engine.h src/gfile.h src/tree.h \
  src/filter.h src/pbook.h src/crosstab.h src/spellchk.h src/probe.h \
  src/optable.h src/polyglot.h
src/movelist.o: src/movelist.cpp src/movelist.h src/common.h src/tclmy.h \
  src/myassert.h src/error.h src/sqmove.h src/misc.h

### End of Makefile

I see the following files are contained in the directory


```
user@user-laptop:/usr/local/src/scid$ ls
bases      COPYING     Makefile              Makefile.cygwin      sc_addmove    scid_fr.eco  sc_import  spliteco
bitmaps    engines     Makefile~             Makefile.mingw       sc_eco        scid.ico     sc_remote  src
bitmaps2   help        Makefile.85           Makefile.pocket_x86  sc_epgn       scid.js      scripts    svg
books      html        Makefile.arm          Makefile.vc          scid          scidlet.ini  sc_spell   tcl
ChangeLog  Info.plist  Makefile.bak          pgnfix               scid.css      scidlet.sbk  sc_tree    THANKS
CHANGES    log         Makefile.conf         pocket               scid.eco      scidpgn      sounds     TODO
configure  mac_icons   Makefile.conf.darwin  README               scid-esp.eco  scid.rc      spf2spi

```

Does it have to do with this lines after I do ./configure ?

>     Location of "tcl.h": not found
    Location of "tk.h": not found

How do I go about making it find "tcl.h" and "tk.h"?

---

### Post by oldos2er on 2009-12-21
If configure doesn't complete successfully, there's no point running make.

"How do I go about making it find "tcl.h" and "tk.h"?"

You need to install the dev packages containing tcl and tk. If you downloaded the source code from a website, I'd search there to see if there's a list of dependencies. Or read the README.

Here's some more info on compiling: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) and [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by thebrotherofasis on 2009-12-21
> **oldos2er said:**
> If configure doesn't complete successfully, there's no point running make.

"How do I go about making it find "tcl.h" and "tk.h"?"

You need to install the dev packages containing tcl and tk. If you downloaded the source code from a website, I'd search there to see if there's a list of dependencies. Or read the README.

Here's some more info on compiling: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) and [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

How can I search / find the dev packages of tcl.h and tk.h if the site doesn't provide info nor the README file?

---

### Post by oldos2er on 2009-12-21
Run something like **apt-cache search tcl** or **apt-cache search tk**
Or use Synaptic's search function (not quick search).

---

