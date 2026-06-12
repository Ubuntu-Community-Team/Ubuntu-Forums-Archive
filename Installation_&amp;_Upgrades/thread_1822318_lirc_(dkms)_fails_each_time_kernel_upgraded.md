---
title: "lirc (dkms) fails each time kernel upgraded"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by mike_perth on 2011-08-10
hi,

each time i upgrade my kernel, my installation of lirc fails to work after the upgrade, and i have to re-compile (against new kernel) and install the lirc modules... which i do via something like:

  ```

sudo modprobe -r lirc_imon
sudo dpkg-reconfigure lirc-modules-source
 sudo modprobe lirc_imon

```after which all is well. this of course is a problem that DKMS should solve for me but it doesn't do it.

also i get this message in my messages log:

```
dkms_autoinstaller: lirc (): AUTOINSTALL not set in its dkms.conf.
```however the contents of /var/lib/dkms/lirc/0.8.7~pre3/build/dkms.conf  and  /usr/src/lirc-0.8.7~pre3/dkms.conf (which are identical files) are as follows:

```
PACKAGE_NAME="lirc"
PACKAGE_VERSION="0.8.7~pre3"
CLEAN="rm -f *.*o"
MAKE[0]="make dkms KSRC=$kernel_source_dir KVER=$kernelver"
AUTOINSTALL="yes"

BUILT_MODULE_NAME[0]="lirc_dev"
BUILT_MODULE_LOCATION[0]="modules"
DEST_MODULE_LOCATION[0]="/updates/lirc"

BUILT_MODULE_NAME[1]="lirc_atiusb"
BUILT_MODULE_LOCATION[1]="modules"
DEST_MODULE_LOCATION[1]="/updates/lirc"

BUILT_MODULE_NAME[2]="lirc_bt829"
BUILT_MODULE_LOCATION[2]="modules"
DEST_MODULE_LOCATION[2]="/updates/lirc"

BUILT_MODULE_NAME[3]="lirc_ite8709"
BUILT_MODULE_LOCATION[3]="modules"
DEST_MODULE_LOCATION[3]="/updates/lirc"

BUILT_MODULE_NAME[4]="lirc_i2c"
BUILT_MODULE_LOCATION[4]="modules"
DEST_MODULE_LOCATION[4]="/updates/lirc"

BUILT_MODULE_NAME[5]="lirc_igorplugusb"
BUILT_MODULE_LOCATION[5]="modules"
DEST_MODULE_LOCATION[5]="/updates/lirc"

BUILT_MODULE_NAME[6]="lirc_imon"
BUILT_MODULE_LOCATION[6]="modules"
DEST_MODULE_LOCATION[6]="/updates/lirc"

BUILT_MODULE_NAME[7]="lirc_it87"
BUILT_MODULE_LOCATION[7]="modules"
DEST_MODULE_LOCATION[7]="/updates/lirc"

BUILT_MODULE_NAME[8]="lirc_mceusb"
BUILT_MODULE_LOCATION[8]="modules"
DEST_MODULE_LOCATION[8]="/updates/lirc"

BUILT_MODULE_NAME[9]="lirc_ttusbir"
BUILT_MODULE_LOCATION[9]="modules"
DEST_MODULE_LOCATION[9]="/updates/lirc"

BUILT_MODULE_NAME[10]="lirc_sasem"
BUILT_MODULE_LOCATION[10]="modules"
DEST_MODULE_LOCATION[10]="/updates/lirc"

BUILT_MODULE_NAME[11]="lirc_serial"
BUILT_MODULE_LOCATION[11]="modules"
DEST_MODULE_LOCATION[11]="/updates/lirc"

BUILT_MODULE_NAME[12]="lirc_sir"
BUILT_MODULE_LOCATION[12]="modules"
DEST_MODULE_LOCATION[12]="/updates/lirc"

BUILT_MODULE_NAME[13]="lirc_streamzap"
BUILT_MODULE_LOCATION[13]="modules"
DEST_MODULE_LOCATION[13]="/updates/lirc"

BUILT_MODULE_NAME[14]="lirc_ene0100"
BUILT_MODULE_LOCATION[14]="modules"
DEST_MODULE_LOCATION[14]="/updates/lirc"

BUILT_MODULE_NAME[15]="lirc_wpc8769l"
BUILT_MODULE_LOCATION[15]="modules"
DEST_MODULE_LOCATION[15]="/updates/lirc"
```... which seems to have autoinstall activated.

the output of "dkms status -m lirc" is:

```

lirc, 0.8.7~pre3, 2.6.35-30-generic, i686: installed 

```so i don't understand why the message log has the line in it saying autoinstall isn't on... so that is question number one.

question number two is, given that DKMS does seem to be trying to compile my lirc modules, why is it failing? The contents of /var/lib/dkms/lirc/kernel-2.6.35-30-generic-i686/log/make.log are (partially) included below, note the error (which occurs over and over in that file, perhaps once per lirc module it tries to build?):

```
DKMS make.log for lirc-0.8.7~pre3 for kernel 2.6.35-30-generic (i686)
Tue Aug  9 01:18:35 WST 2011
mkdir modules
make -C drivers SUBDIRS="lirc_dev"
make[1]: Entering directory `/var/lib/dkms/lirc/0.8.7~pre3/build/drivers'
Making all in lirc_dev
make[2]: Entering directory `/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev'
cp ./../lirc_dev/Module*.symvers .
cp: cannot stat `./../lirc_dev/Module*.symvers': No such file or directory
make[2]: [lirc_dev.o] Error 1 (ignored)
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
    make -C /lib/modules/2.6.35-30-generic/build SUBDIRS=/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev modules \
        KBUILD_VERBOSE=1
make[3]: Entering directory `/usr/src/linux-headers-2.6.35-30-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/.tmp_versions ; rm -f /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev
  gcc -Wp,-MD,/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/linux-headers-2.6.35-30-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/../.. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/../.. -I/lib/modules/2.6.35-30-generic/build/include/ -I/lib/modules/2.6.35-30-generic/build/drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)"  -c -o /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/.tmp_lirc_dev.o /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/lirc_dev.c
  set -e ; perl /usr/src/linux-headers-2.6.35-30-generic/scripts/recordmcount.pl "i386" "little" "32" "objdump" "objcopy" "gcc" "ld" "nm" "" "" "1" "/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/lirc_dev.o";
(cat /dev/null;   echo kernel//var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/lirc_dev.ko;) > /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/modules.order
make -f /usr/src/linux-headers-2.6.35-30-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.35-30-generic/Module.symvers -I /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/Module.symvers  -o /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/Module.symvers -S -w  -s
  gcc -Wp,-MD,/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/.lirc_dev.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/linux-headers-2.6.35-30-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/../.. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/../.. -I/lib/modules/2.6.35-30-generic/build/include/ -I/lib/modules/2.6.35-30-generic/build/drivers/media/video/  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)"  -DMODULE -c -o /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/lirc_dev.mod.o /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/lirc_dev.mod.c
  ld -r -m elf_i386 -T /usr/src/linux-headers-2.6.35-30-generic/scripts/module-common.lds --build-id -o /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/lirc_dev.ko /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/lirc_dev.o /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev/lirc_dev.mod.o
make[3]: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic'
mv Makefile.automake Makefile
make[2]: Leaving directory `/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_dev'
make[2]: Entering directory `/var/lib/dkms/lirc/0.8.7~pre3/build/drivers'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/var/lib/dkms/lirc/0.8.7~pre3/build/drivers'
make[1]: Leaving directory `/var/lib/dkms/lirc/0.8.7~pre3/build/drivers'
cp drivers/lirc_dev/lirc_dev.ko modules
make -C drivers SUBDIRS="lirc_atiusb"
make[1]: Entering directory `/var/lib/dkms/lirc/0.8.7~pre3/build/drivers'
Making all in lirc_atiusb
make[2]: Entering directory `/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_atiusb'
cp ./../lirc_dev/Module*.symvers .
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
    make -C /lib/modules/2.6.35-30-generic/build SUBDIRS=/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_atiusb modules \
        KBUILD_VERBOSE=1
make[3]: Entering directory `/usr/src/linux-headers-2.6.35-30-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_atiusb/.tmp_versions ; rm -f /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_atiusb/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_atiusb
  gcc -Wp,-MD,/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_atiusb/.lirc_atiusb.o.d  -nostdinc -isystem /usr/lib/gcc/i
```so i don't understand what's going on! can anyone help? i suspect that 'kernel configuration is invalid' is the problem but don't know how to prevent that when dkms is supposed to be doing everything itself...

thanks heaps

Mike

p.s. i'm on Maverick now but i had this same issue back with Lucid so it's not the whole "lirc is built into the kernel as of maverick" issue!

---

### Post by mike_perth on 2011-08-10
actually, now that i look at that huge chunk of /var/lib/dkms/lirc/kernel-2.6.35-30-generic-i686/log/make.log that i pasted above, i see that it wasn't actually necessarily saying an error had occured, the script just seems to have spat out some code about echoing an error if some condition was met. so maybe the compile via DKMS worked - but perhaps this log was created by me invoking dpkg-reconfigure when i was fixing everything after the kernel upgrade...?

perhaps this is more useful, i've found the apt log from when DKMS seems to have worked but installing the modules doesn't seem to have worked:

```
Log started: 2011-08-09  01:18:07
warning, in file '/var/lib/dpkg/status' near line 47726 package 'virtualbox-2.2': 
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
warning, in file '/var/lib/dpkg/status' near line 47727 package 'virtualbox-2.2': 
 error in Config-Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
warning, in file '/var/lib/dpkg/available' near line 50014 package 'virtualbox-2.2': 
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 191719 files and directories currently installed.) 
Preparing to replace lirc 0.8.7~pre3-0ubuntu1 (using .../lirc_0.8.7~pre3-0ubuntu1_i386.deb) ... 
 * Stopping remote control daemon(s): LIRC       [80G  [74G[ OK ] 
Unpacking replacement lirc ... 
Preparing to replace lirc-modules-source 0.8.7~pre3-0ubuntu1 (using .../lirc-modules-source_0.8.7~pre3-0ubuntu1_all.deb) ... 
warning, in file '/var/lib/dpkg/status' near line 47726 package 'virtualbox-2.2': 
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
warning, in file '/var/lib/dpkg/status' near line 47727 package 'virtualbox-2.2': 
 error in Config-Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
warning, in file '/var/lib/dpkg/available' near line 50014 package 'virtualbox-2.2': 
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
Removing all DKMS Modules 
Done. 
Unpacking replacement lirc-modules-source ... 
Processing triggers for doc-base ... 
Processing 1 changed doc-base file(s)... 
Registering documents with scrollkeeper... 
Processing triggers for man-db ... 
Processing triggers for hal ... 
Regenerating hal fdi cache ... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
warning, in file '/var/lib/dpkg/status' near line 47728 package 'virtualbox-2.2': 
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
warning, in file '/var/lib/dpkg/status' near line 47729 package 'virtualbox-2.2': 
 error in Config-Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
warning, in file '/var/lib/dpkg/available' near line 50014 package 'virtualbox-2.2': 
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
Setting up lirc (0.8.7~pre3-0ubuntu1) ... 
 * Loading LIRC modules       [80G  [74G[ OK ] 
 [31m*[39;49m Unable to load LIRC kernel modules. Verify your 
 [31m*[39;49m selected kernel modules in /etc/lirc/hardware.conf 
Setting up lirc-modules-source (0.8.7~pre3-0ubuntu1) ... 
warning, in file '/var/lib/dpkg/status' near line 47728 package 'virtualbox-2.2': 
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
warning, in file '/var/lib/dpkg/status' near line 47729 package 'virtualbox-2.2': 
 error in Config-Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
warning, in file '/var/lib/dpkg/available' near line 50014 package 'virtualbox-2.2': 
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number 
Loading new lirc-0.8.7~pre3 DKMS files... 
Building only for 2.6.35-30-generic 
Building for architecture i686 
Building initial module for 2.6.35-30-generic 
Done. 
 
lirc_dev.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_atiusb.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_bt829.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_ite8709.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_i2c.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_igorplugusb.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_imon.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_it87.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_mceusb.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_ttusbir.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_sasem.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_serial.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_sir.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_streamzap.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_ene0100.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
lirc_wpc8769l.ko: 
Running module version sanity check. 
 - Original module 
 - Installation 
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/ 
 
depmod.... 
 
DKMS: install Completed. 
Log ended: 2011-08-09  01:19:01
```again i don't know for sure if this is from when the new kernel came in, or from after then when i fixed lirc via dpkg-reconfigure :-(.  Note however the line that says "Unable to load LIRC kernel modules" after stopping lirc daemon...

also the script doesn't say anything about stopping LCDd which is another daemon that uses these modules. perhaps by not stpping that daemon before doing the dkms stuff, installing the new DKMS modules doesn't work? i wouldn't think so given that DKMS should be preparing the modules for use after the next reboot (i.e. when i reboot to the newly installed kernel).

---

