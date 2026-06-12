---
title: "compiling comedi on 8.10 failed"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by huseyinkozan on 2008-11-12
according to /usr/share/doc/comedi-source/README.Debian
giving this command
/usr/src# module-assistant auto-install comedi

```

make: Nothing to be done for `kdist_clean'.
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/comedi'
make[1]: Nothing to be done for `kdist_clean'.
make[1]: Nothing to be done for `kdist_config'.
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-7-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.27-7-generic/g ;s/#KVERS#/2.6.27-7-generic/g ; s/_KVERS_/2.6.27-7-generic/g ; s/##KDREV##/2.6.27-7.16/g ; s/#KDREV#/2.6.27-7.16/$
  done
dh_testroot
dh_clean -k
dh_installdirs lib/modules/2.6.27-7-generic/comedi
# Build the module
#/usr/bin/make -C drivers KERNEL_DIR=/usr/src/linux KVERS=2.6.27-7-generic
# Install the module
libtoolize --copy --force
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
libtoolize: Remember to add `LT_INIT' to configure.ac.
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
CFLAGS="-Wall -g -O2 -O2" ./configure \
                --host=i486-linux-gnu \
                --build=i486-linux-gnu \
                --with-rtaidir=/usr/lib/realtime \
                --enable-pcmcia
configure: error: cannot run /bin/bash ./config.sub
make[1]: *** [binary-modules] Error 1
make[1]: Leaving directory `/usr/src/modules/comedi'
make: *** [kdist_build] Error 2

```

and i tried this:
[http://groups.google.com/group/comed...3c118bc59470cc](http://groups.google.com/group/comed...3c118bc59470cc)

after this:
/usr/src/modules/comedi# ./autogen.sh

i got this:
```

configure.ac:6: installing `./config.guess'
configure.ac:6: installing `./config.sub'
Makefile.am:41: `:='-style assignments are not portable
Makefile.am:41: shell find $(srcdir: non-POSIX variable name
Makefile.am:41: (probably a GNU make extension)

```

the result was the same


also i tried download and compile packages from comedi.org and i failed again. and i don't want to use comedi.org's package for the difficulties about management of installed programs.


can anybody help me ?

---

### Post by jge026 on 2008-11-14
I am trying to do the same... with the same results.  I'll keep trying, but please let me know if you figure it out.

---

### Post by kikazaru on 2008-11-19
I'm having similar problems... perhaps I got a little bit further by:

sudo apt-get install automake
sudo apt-get install libtool

```

make  all-recursive
make[1]: Entering directory `/usr/src/modules/comedi'
Making all in comedi
make[2]: Entering directory `/usr/src/modules/comedi/comedi'
Making all in .
make[3]: Entering directory `/usr/src/modules/comedi/comedi'
if test "." != "."; then \
		for dir in . drivers kcomedilib drivers/addi-data; do \
			for file in `ls /usr/src/modules/comedi/comedi/$dir/*\.[ch] /usr/src/modules/comedi/comedi/$dir/Kbuild | /bin/grep -E -v \.mod\.c`; do \
				LINK_NAME=$dir/`basename "$file"`; \
				if test ! -e $LINK_NAME; then ln -vs $file $LINK_NAME; fi; \
			done; \
		done; \
	fi
make -I/usr/src/modules/comedi/comedi -C /usr/src/linux-source-2.6.27 M=/usr/src/modules/comedi/comedi CC="gcc -I/usr/src/modules/comedi/ \
		-I/usr/src/modules/comedi/include  " modules
make[4]: Entering directory `/usr/src/linux-source-2.6.27'
  CC [M]  /usr/src/modules/comedi/comedi/comedi_fops.o
In file included from /usr/src/modules/comedi/include/linux/mutex.h:41,
                 from include/linux/notifier.h:13,
                 from include/linux/memory_hotplug.h:6,
                 from include/linux/mmzone.h:560,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /usr/src/modules/comedi/include/linux/slab.h:8,
                 from include/linux/percpu.h:5,
                 from include/linux/rcupdate.h:39,
                 from include/linux/rculist.h:10,
                 from include/linux/dcache.h:6,
                 from include/linux/fs.h:281,
                 from /usr/src/modules/comedi/comedi/comedi_compat32.h:31,
                 from /usr/src/modules/comedi/comedi/comedi_fops.c:28:
/usr/src/modules/comedi/include/asm/semaphore.h:18:32: error: asm/semaphore.h: No such file or directory
In file included from include/linux/notifier.h:15,
                 from include/linux/memory_hotplug.h:6,
                 from include/linux/mmzone.h:560,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /usr/src/modules/comedi/include/linux/slab.h:8,
                 from include/linux/percpu.h:5,
                 from include/linux/rcupdate.h:39,
                 from include/linux/rculist.h:10,
                 from include/linux/dcache.h:6,
                 from include/linux/fs.h:281,
                 from /usr/src/modules/comedi/comedi/comedi_compat32.h:31,
                 from /usr/src/modules/comedi/comedi/comedi_fops.c:28:
include/linux/srcu.h:37: error: field ‘semaphore’ has incomplete type
In file included from include/linux/memory_hotplug.h:6,
                 from include/linux/mmzone.h:560,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /usr/src/modules/comedi/include/linux/slab.h:8,
                 from include/linux/percpu.h:5,
                 from include/linux/rcupdate.h:39,
                 from include/linux/rculist.h:10,
                 from include/linux/dcache.h:6,
                 from include/linux/fs.h:281,
                 from /usr/src/modules/comedi/comedi/comedi_compat32.h:31,
                 from /usr/src/modules/comedi/comedi/comedi_fops.c:28:
include/linux/notifier.h:71: error: field ‘semaphore’ has incomplete type
In file included from include/asm/acpi.h:30,
                 from include/asm/fixmap_32.h:28,
                 from include/asm/fixmap.h:5,
                 from include/asm/apic.h:8,
                 from include/asm/smp.h:13,
                 from include/linux/smp.h:28,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:683,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /usr/src/modules/comedi/include/linux/slab.h:8,
                 from include/linux/percpu.h:5,
                 from include/linux/rcupdate.h:39,
                 from include/linux/rculist.h:10,
                 from include/linux/dcache.h:6,
                 from include/linux/fs.h:281,
                 from /usr/src/modules/comedi/comedi/comedi_compat32.h:31,
                 from /usr/src/modules/comedi/comedi/comedi_fops.c:28:
include/asm/mmu.h:19: error: field ‘lock’ has incomplete type
/usr/src/modules/comedi/comedi/comedi_fops.c: In function ‘comedi_open’:
/usr/src/modules/comedi/comedi/comedi_fops.c:1766: warning: format not a string literal and no format arguments
/usr/src/modules/comedi/comedi/comedi_fops.c: In function ‘comedi_init’:
/usr/src/modules/comedi/comedi/comedi_fops.c:1918: error: implicit declaration of function ‘class_device_create’
/usr/src/modules/comedi/comedi/comedi_fops.c:1918: warning: assignment makes pointer from integer without a cast
/usr/src/modules/comedi/comedi/comedi_fops.c: In function ‘comedi_cleanup’:
/usr/src/modules/comedi/comedi/comedi_fops.c:1947: error: implicit declaration of function ‘class_device_destroy’
make[5]: *** [/usr/src/modules/comedi/comedi/comedi_fops.o] Error 1
make[4]: *** [_module_/usr/src/modules/comedi/comedi] Error 2
make[4]: Leaving directory `/usr/src/linux-source-2.6.27'
make[3]: [all-local] Error 2 (ignored)
make[3]: Leaving directory `/usr/src/modules/comedi/comedi'
Making all in kcomedilib
make[3]: Entering directory `/usr/src/modules/comedi/comedi/kcomedilib'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/modules/comedi/comedi/kcomedilib'
Making all in drivers
make[3]: Entering directory `/usr/src/modules/comedi/comedi/drivers'
Making all in addi-data
make[4]: Entering directory `/usr/src/modules/comedi/comedi/drivers/addi-data'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/src/modules/comedi/comedi/drivers/addi-data'
make[4]: Entering directory `/usr/src/modules/comedi/comedi/drivers'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/usr/src/modules/comedi/comedi/drivers'
make[3]: Leaving directory `/usr/src/modules/comedi/comedi/drivers'
make[2]: Leaving directory `/usr/src/modules/comedi/comedi'
Making all in include
make[2]: Entering directory `/usr/src/modules/comedi/include'
Making all in asm
make[3]: Entering directory `/usr/src/modules/comedi/include/asm'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/modules/comedi/include/asm'
Making all in linux
make[3]: Entering directory `/usr/src/modules/comedi/include/linux'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/modules/comedi/include/linux'
Making all in pcmcia
make[3]: Entering directory `/usr/src/modules/comedi/include/pcmcia'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/modules/comedi/include/pcmcia'
make[3]: Entering directory `/usr/src/modules/comedi/include'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/src/modules/comedi/include'
make[2]: Leaving directory `/usr/src/modules/comedi/include'
make[2]: Entering directory `/usr/src/modules/comedi'
make[2]: Leaving directory `/usr/src/modules/comedi'
make[1]: Leaving directory `/usr/src/modules/comedi'

```

---

### Post by Partyboi2 on 2008-11-19
What version of comedi are you trying to install?

---

### Post by kikazaru on 2008-11-19
The latest, i.e., 0.7.76 at this time.

The funny thing is, I followed the instructions on the Comedi wiki (copied below) and it seems to have worked. It's the same version as that of the ubuntu comedi package providing the kernel source so I don't understand what was wrong with the source in the package...

Compile/Install comedilib (userspace)

   1. Download: comedilib.tar.gz
   2. "tar xzvf comedilib.tar.gz"
   3. "cd comedilib"
   4. If you've downloaded from the cvs type: "sh autogen.sh"
   5.
         1. For old hotplug: "./configure --enable-etc-hotplug --sysconfdir=/etc"
         2. For new udev: "./configure --with-udev-hotplug=/lib --sysconfdir=/etc" 
   6. "make"
   7. "su"
   8. "make dev"
   9. "make install"
  10. "add /usr/local/lib to /etc/ld.so.conf"

---

### Post by huseyinkozan on 2008-11-19
before the comedi.org's original package try, i tried to install the packages that ubuntu have. someone said libtool's vesion must be <2, but i couldn't find in repos.

this is the link that emailing list thread:
[http://groups.google.com/group/comedi_list/browse_thread/thread/4b8b23d58302c2c7/6bec3603c1bda8d7?lnk=gst&q=libtool#6bec3603c1bda8d7]("http://groups.google.com/group/comedi_list/browse_thread/thread/4b8b23d58302c2c7/6bec3603c1bda8d7?lnk=gst&q=libtool#6bec3603c1bda8d7")

did anyone try that way

---

### Post by kikazaru on 2008-11-19
To add to my further report, I don't have it working properly yet. I managed to compile the kernel module by downloading the latest unstable version:

cvs -d :pserver:anonymous@cvs.comedi.org:/cvs/comedi co comedi

I just did

./configure
./make
./sudo install

Then when I plug in my usbdux I get ( from dmesg ):

```

[ 5412.604133] usb 8-1: new high speed USB device using ehci_hcd and address 5
[ 5412.736768] usb 8-1: configuration #1 chosen from 1 choice
[ 5412.738690] comedi_: usbdux_: finding a free structure for the usb-device
[ 5412.738703] comedi_: usbdux: usbduxsub[0] is ready to connect to comedi.
[ 5412.738708] comedi_: usbdux: ifnum=0
[ 5412.776508] comedi_: usbdux0 has been successfully initialised.

```

This is correct, but in my case I still need to load the usbdux firmware. It's disappointing that this doesn't happen automatically, but adding the udev etc. explicitly to the configure command causes the make to fail. Likewise, if I use the recommended manual method of loading the firmware:

comedi_config -i /usr/local/share/usb/usbdux_firmware.hex /dev/comedi0 usbdux 

I get a bunch of ugly errors on dmesg, and no action from my usbdux.

Still persevering...

---

### Post by huseyinkozan on 2008-11-20
my card is  PCMCIA and i can not load pcmcia module with, 
modprobe pcmcia

there is no sign in the dmesg about pcmcia and ni_mio_cs after 
modprobe ni_mio_cs

how can i sure that PCMCIA module works properly ?

---

### Post by huseyinkozan on 2008-11-20
i've just found this:

> Hi,
thank you so much for the prompt replies - I would never have figured out how to get things running otherwise!!
SO just a short summary of what I needed to get my PCMCIA data acquisition card working:
- debian linux kernel 2.4.22
- PCMCIA kernel support, not the pcmcia-cs packages
- ISA support, otherwise the IRQ is not assigned correctly. I also have Plug and Play support as a module, but I don't know, if that is necessary.

I will now start the REAL work with comedi ....
thanks again,
miriam

original link:
[http://osdir.com/ml/linux.comedi/2003-10/msg00109.html]("http://osdir.com/ml/linux.comedi/2003-10/msg00109.html")

i will try to compile kernel by hand to get PCMCIA kernel support

---

### Post by jeesbut on 2008-11-26
I have exactly the same problem that kikazaru had in the post 3. How you got rid of this?

---

### Post by huseyinkozan on 2008-11-27
I am so sorry guys. 
I was trying to load a PCMCIA Card into an Express Card slot.

I am very stupid :D

---

### Post by kikazaru on 2008-11-27
Well, I'm happy to hear your problem is solved. Incidentally, for installing non-packaged stuff you can use "checkinstall" to simultaneously build a package file which you can use to tidily remove and indeed reinstall the software. It's a useful trick I just learned.

Anyway, I am still no further with this problem and and really looking forward to some help with it... anyone?

---

