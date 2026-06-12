---
title: "install effectv newest version"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by jorgecarrillo150990 on 2007-11-29
I have been using Ubuntu for 8 moths, I had considered myself a pro...until yesterday.

I want to install the newest effectv, but there is no .deb file (if there is one please link)

So it basically say I have to modify the config.mk and the makefile.
I will post both files so you can give me some help on how to fill it.

======CONFIG.MK============0

###Common configuration file for Makefiles of EffecTV

### Install
## the following lines set destination directory for a compiled program and
## manual page.
prefix = /usr/local
exec_prefix = ${prefix}

bindir = $(DESTDIR)${exec_prefix}/bin
mandir = $(DESTDIR)${prefix}/man

### Architecture
## choose your architecture (only one)
## Linux for intel architecture
ARCH = i686-linux
## Linux for PlayStation2
# ARCH = ps2-linux

### Multimedia extension code set
## MMX
## comment out next line if you want not to enable MMX operation.
USE_MMX = yes

### NASM
## comment out next line if you want not to use NASM.
USE_NASM = yes

### vloopback
## comment out next line if you want to disable vloopback support.
USE_VLOOPBACK = yes

## choose vloopback version (only one).
# version 0.91 or later
VLOOPBACK_VERSION = 91
## version 0.83 or former (obsolete!!)
# VLOOPBACK_VERSION = 83

### Default settings
## Set a default device file name of the video input.
DEFAULT_VIDEO_DEVICE = "/dev/video0"

### Memory debug
#MEM_DEBUG = yes

################################################## #############################
### none user configurable settings

## architecture dependent settings
## i686-linux
ifeq ($(ARCH), i686-linux)
CONFIG.arch = -DI686
CFLAGS.opt = -march=pentiumpro -O3 -fomit-frame-pointer -funroll-loops
endif

## PlayStaion2
ifeq ($(ARCH), ps2-linux)
CONFIG.arch = -DPS2
CFLAGS.opt = -O3 -fomit-frame-pointer -funroll-loops
USE_NASM = no
USE_MMX = no
USE_VLOOPBACK = no
CONFIG += -DRGB_BGR_CONVERSION
LIBS.extra = -ldl -L/usr/X11R6/lib -lX11 -lXext
endif

ifeq ($(USE_NASM), yes)
CONFIG += -DUSE_NASM
endif

ifeq ($(USE_MMX), yes)
CONFIG += -DUSE_MMX
endif

ifeq ($(USE_VLOOPBACK), yes)
CONFIG += -DUSE_VLOOPBACK
CONFIG += -DVLOOPBACK_VERSION=$(VLOOPBACK_VERSION)
endif

CONFIG += -DDEFAULT_VIDEO_DEVICE=\"$(DEFAULT_VIDEO_DEVICE)\"

ifeq ($(MEM_DEBUG), yes)
CONFIG += -DMEM_DEBUG
CFLAGS.opt = -g -O2
endif



============ MAKEFILE==============

# Makefile for EffecTV

include ./config.mk

CC = gcc
NASM = nasm
INSTALL = /usr/bin/install -c

CFLAGS = $(CONFIG) $(CONFIG.arch) $(CFLAGS.opt) -Iv4lutils `sdl-config --cflags`
LIBS = v4lutils/libv4lutils.a -lm `sdl-config --libs` $(LIBS.extra)

PROGRAM = effectv

COREOBJS = main.o screen.o video.o frequencies.o palette.o
VLOOPBACKOBJS = vloopback.o
UTILS = utils.o yuv.o buffer.o image.o

OBJS = $(COREOBJS) $(UTILS)

ifeq ($(USE_VLOOPBACK), yes)
OBJS += $(VLOOPBACKOBJS)
endif

LIBEFFECTS = effects/libeffects.a
SUBDIRS = effects v4lutils tools

### rules

%.o: %.c
$(CC) $(CFLAGS) -Wall -c -o $@ $<
%.o: %.nas
$(NASM) -f elf $<

all-recursive:
@list='$(SUBDIRS)'; for subdir in $$list; do \
(cd $$subdir && $(MAKE) all-recursive) || exit 1;\
done; \
$(MAKE) all-am

all-am: $(PROGRAM)

$(PROGRAM): $(OBJS) $(LIBEFFECTS) v4lutils/libv4lutils.a
$(CC) -o $@ $(OBJS) $(LIBEFFECTS) $(LIBS)

$(OBJS): EffecTV.h screen.h video.h palette.h frequencies.h vloopback.h utils.h

install: all-am
$(INSTALL) -s $(PROGRAM) $(bindir)/
$(INSTALL) effectv.1 $(mandir)/man1/

clean:
rm -f *.o $(PROGRAM)
cd effects && $(MAKE) clean
cd v4lutils && $(MAKE) clean
cd tools && $(MAKE) clean

---

### Post by jorgecarrillo150990 on 2007-11-30
I need some help filling out those files in order to make a complete installation

---

### Post by jorgecarrillo150990 on 2007-12-02
Please....

---

### Post by awkwardmoment on 2008-01-19
heres a .deb: [http://debian.mirror.inra.fr/debian/pool/main/e/effectv/effectv_0.3.11-1_i386.deb](http://debian.mirror.inra.fr/debian/pool/main/e/effectv/effectv_0.3.11-1_i386.deb)

---

