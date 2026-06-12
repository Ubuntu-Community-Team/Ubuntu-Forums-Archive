---
title: "How-to: use custom DSDT in Karmic"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by cyberey66 on 2009-11-29
I've seen a lot of threads with users who are having troubles due to the inability to load a custom DSDT file in kernels after 2.6.30.  This prevents many users from upgrading simply because their hardware will not run correctly without a fixed DSDT.  I fell into this category with my gateway lt3103u netbook and compiled a working kernel (2.6.31_15.50).  I figured I would show what I did so people can do the same.  If your laptop overheats or CPU scaling doesn't work, this might be for you.

What you need to upgrade:

1. A working DSDT tabled (compiled):
For gateway LT31 users:
[http://www.pow.za.net/index.html](http://www.pow.za.net/index.html)

Thread on fixing your specific DSDT file:
[http://ubuntuforums.org/showthread.php?t=1036051&highlight=buggy+dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=buggy+dsdt)

2. Kernel source for the kernel you wish to compile:
Download linux-source-2.6.31-<version-number-here>.deb from:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/)
and install using 
```
sudo dpkg -i linux-source-<version-number-here>.deb
```or use apt for current kernel

```
apt-get install linux-source
```3. Any patches you wish to apply. (ie powernow patch for netbook CPUs)

Now we can begin compiling the Kernel, I am following this guide:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

First get nessessary packages:
```
sudo apt-get install fakeroot kernel-wedge build-essential makedumpfile[FONT=monospace]
[/FONT]sudo apt-get build-dep linux[FONT=monospace]
[/FONT]sudo apt-get install qt3-dev-tools libqt3-mt-dev
```Now we make a directory and extract the kernel source into it:
```
mkdir ~/src[FONT=monospace]
[/FONT]cd ~/src[FONT=monospace]
[/FONT]tar xjvf /usr/src/linux-source-<version-number-here>.tar.bz2[FONT=monospace]
[/FONT]cd linux-source-<version-number-here>
```Now we copy over our current kernel configuration so we only have to change the DSDT option in the new kernel
```
cp -vi /boot/config-`uname -r` .config
```Now we configure the kernel use our custom DSDT table.  You need to know the path to the compiled DSDT table you are using.  In my case, I copied my DSTS table from 'dsdt.hex' to '/dsdt/dsdt_table.h'.
run xconfig
```
make xconfig
```Now we will point to the DSDT table in xconfig:
- On the left pane, highlight "ACPI (Advanced ..."
- Now, in the right pan doubleclick "Custom DSDT Table file to include: "
and enter the full path to your DSDT table
[IMG]http://people.virginia.edu/%7Emc8qr/screenshot_11-29-09.png[/IMG]
- Save the configuration and exit.

If you do not have patches to apply, skip this part:  Apply any patches you have now using
```
 cp path-to-patchs ~/src/linux-source-<version-number-here>/
patch -p0 < patch_name.diff
```Now we compile the kernel:
```
fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers
```After this is finished, the deb file will be located in ~/src/, and now we can install it:
```
echo vesafb | sudo tee -a /etc/initramfs-tools/modules
echo fbcon | sudo tee -a /etc/initramfs-tools/modules[FONT=monospace]
[/FONT]sudo dpkg -i linux-image-<version-number-here>_i386.deb[FONT=monospace]
[/FONT]sudo dpkg -i linux-headers-<version-number-here>_i386.deb
```I tested this with my gateway lt3103u using kernel source 2.6.31-15.50 from the ubuntu repositories and my custom DSDT works perfectly.

This is my first how-to, so let me know if there are mistakes/suggestions

---

### Post by spaceballl on 2009-12-16
Thanks so much for doing this. My brother is going to be getting the same netbook you mention this upcoming Christmas. A couple questions for you...

1) If he updates his packages and a new kernel comes out, will it just overwrite all the manual labor I did above?

2) Any chance that CPU scaling / powernow will be supported by default in a future kernel? Thanks!

---

### Post by mscdex on 2009-12-21
> **spaceballl said:**
> Thanks so much for doing this. My brother is going to be getting the same netbook you mention this upcoming Christmas. A couple questions for you...

1) If he updates his packages and a new kernel comes out, will it just overwrite all the manual labor I did above?

2) Any chance that CPU scaling / powernow will be supported by default in a future kernel? Thanks!

1) If a new kernel is released by the Ubuntu team for your version of Ubuntu, it will not remove your installed custom kernel. However, you may have to repeat the recompiling and patching (if applicable) steps if you want to take advantage of any fixes or new features in the new kernel.

2) The 2.6.32 kernel already contains the powernow patch, but you may still need to recompile the kernel in order to set the location of your dsdt file. However, 2.6.32 is slated for inclusion in the Ubuntu Lucid release, not Karmic. Despite this, you can always grab the latest 2.6.32 kernel sources from the Ubuntu kernel PPA here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I'm compiling 2.6.32(.2) right now because I believe (from bug reports I read) the connectivity issues with the ath9k wifi driver have been fixed in 2.6.32, without sacrificing power management.

---

### Post by meatwad64 on 2010-01-21
Have you tried the 2.6.32 kernels? I tried one of the debs from that mainline that was for 2.6.32.4 and wireless seems better but powernow doesn't seem to be working for me. I'm not sure why but when I tried to patch the kernel from the sources the patch failed on most of the changes:

Hunk #1 succeeded at 863 with fuzz 2 (offset 8 lines).
Hunk #2 FAILED at 879.
Hunk #3 FAILED at 951.
Hunk #4 FAILED at 992.
3 out of 4 hunks FAILED -- saving rejects to file arch/x86/kernel/cowernow-k8.c.rej

---

### Post by cyberey66 on 2010-01-21
> **meatwad64 said:**
> Have you tried the 2.6.32 kernels? I tried one of the debs from that mainline that was for 2.6.32.4 and wireless seems better but powernow doesn't seem to be working for me. I'm not sure why but when I tried to patch the kernel from the sources the patch failed on most of the changes:

Hunk #1 succeeded at 863 with fuzz 2 (offset 8 lines).
Hunk #2 FAILED at 879.
Hunk #3 FAILED at 951.
Hunk #4 FAILED at 992.
3 out of 4 hunks FAILED -- saving rejects to file arch/x86/kernel/cowernow-k8.c.rej

The powernow patch is included in the new kernel releases, so no more patching of it is needed!  Or it should be at least.

Edit, I'll ask here too.  Does anyone know anything about SUSE still patching their kernels to allow loading a custom DSDT?  I heard rumors but haven't found any information.  I asked on the SUSE forums, but haven't heard a response yet.

Edit, I'll try the new kernel source and post back.  It will be a day or two though, I'm pretty busy.

---

### Post by meatwad64 on 2010-01-22
Yeah I tried to patch it because the 2.6.32.4 kernel doesn't have powernow. cpufreq-info says:

analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU


and uname -a gives me the kernel of:

2.6.32-02063204-generic #02063204 SMP

I was able to re-compile my own kernel from 2.6.32.4 sources but video is very garbled but it was throttling the cpu correctly.

---

### Post by cyberey66 on 2010-01-22
I'm running 2.6.32.4-2.6.32 now and everything seems to work.  That includes wifi, video, and cpu--frequency scaling.

Just copy over your old kernel config and point it to your patched DSDT file with xconfig, compile, and it should work.

Or, you can use my config to compile:  This is for 32bit

[http://people.virginia.edu/~mc8qr/config-2.6.32.4-2.6.32latest]("http://people.virginia.edu/%7Emc8qr/config-2.6.32.4-2.6.32latest")

---

### Post by spaceballl on 2010-01-25
> **cyberey66 said:**
> I'm running 2.6.32.4-2.6.32 now and everything seems to work.  That includes wifi, video, and cpu--frequency scaling.

Just copy over your old kernel config and point it to your patched DSDT file with xconfig, compile, and it should work.

Or, you can use my config to compile:  This is for 32bit

[http://people.virginia.edu/~mc8qr/config-2.6.32.4-2.6.32latest]("http://people.virginia.edu/%7Emc8qr/config-2.6.32.4-2.6.32latest")
When you say everything seems to work... does that mean that you don't need to do ANYTHING? Like you didn't need to make a custom DSDT, everything just works like a charm? :P:P

---

### Post by cyberey66 on 2010-01-25
> **spaceballl said:**
> When you say everything seems to work... does that mean that you don't need to do ANYTHING? Like you didn't need to make a custom DSDT, everything just works like a charm? :P:P

Sadly that is not the case.  You will always have to recompile the kernel unless they start including the patch again.

But, if you just recompile and point to the DSDT file, everything should work.

---

### Post by Sentello on 2010-04-26
Hi :guitar:
Today I download a new Ubuntu 10.04 RC. I tired this guide to apply DSDT which I using in the 9.04.
Ubuntu 10.04 have 2.6.32-21-generic.

I try and this is the output:
 
```
sentello@ubuntu:~/src$ cd linux-source-2.6.32/
sentello@ubuntu:~/src/linux-source-2.6.32$ 
sentello@ubuntu:~/src/linux-source-2.6.32$ fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers
unlink debian/docs/README
unlink debian/docs/Kernel.htm
unlink debian/docs/ImageLoaders/SiloDefault
unlink debian/docs/ImageLoaders/QuikDefault
unlink debian/docs/ImageLoaders/LiloDefault
unlink debian/docs/ImageLoaders/VmeliloDefault
rmdir ImageLoaders
unlink debian/docs/ChangeLog
unlink debian/docs/linux.1
unlink debian/docs/Rationale
unlink debian/docs/LinkPolicy
unlink debian/docs/README.modules
rmdir docs
unlink debian/Control.bin86
unlink debian/rules
unlink debian/po/fr.po
unlink debian/po/ja.po
unlink debian/po/de.po
unlink debian/po/POTFILES.in
unlink debian/po/templates.pot
rmdir po
unlink debian/pkg/source/README
unlink debian/pkg/source/postrm
unlink debian/pkg/source/copyright
unlink debian/pkg/source/preinst
unlink debian/pkg/source/ChangeLog
unlink debian/pkg/source/prerm
unlink debian/pkg/source/postinst
rmdir source
unlink debian/pkg/doc/README
unlink debian/pkg/doc/postrm
unlink debian/pkg/doc/copyright
unlink debian/pkg/doc/preinst
unlink debian/pkg/doc/ChangeLog
unlink debian/pkg/doc/prerm
unlink debian/pkg/doc/postinst
rmdir doc
unlink debian/pkg/image/README
unlink debian/pkg/image/postrm
unlink debian/pkg/image/copyright
unlink debian/pkg/image/preinst
unlink debian/pkg/image/ChangeLog
unlink debian/pkg/image/prerm
unlink debian/pkg/image/postinst
unlink debian/pkg/image/config
rmdir image
unlink debian/pkg/headers/README
unlink debian/pkg/headers/postrm
unlink debian/pkg/headers/copyright
unlink debian/pkg/headers/preinst
unlink debian/pkg/headers/ChangeLog
unlink debian/pkg/headers/prerm
unlink debian/pkg/headers/postinst
unlink debian/pkg/headers/create_link
rmdir headers
unlink debian/pkg/virtual/xen/prerm
unlink debian/pkg/virtual/xen/postinst
rmdir xen
unlink debian/pkg/virtual/um/prerm
unlink debian/pkg/virtual/um/postinst
rmdir um
rmdir virtual
rmdir pkg
unlink debian/changelog
unlink debian/Control
unlink debian/ruleset/kernel_version.mk
unlink debian/ruleset/minimal.mk
unlink debian/ruleset/local-vars.mk
unlink debian/ruleset/arches/hppa.mk
unlink debian/ruleset/arches/powerpc.mk
unlink debian/ruleset/arches/mipsel.mk
unlink debian/ruleset/arches/m68k.mk
unlink debian/ruleset/arches/ia64.mk
unlink debian/ruleset/arches/uml.mk
unlink debian/ruleset/arches/armel.mk
unlink debian/ruleset/arches/mips.mk
unlink debian/ruleset/arches/what_is_ppc_called_today.mk
unlink debian/ruleset/arches/ChangeLog
unlink debian/ruleset/arches/sparc.mk
unlink debian/ruleset/arches/alpha.mk
unlink debian/ruleset/arches/README.txt
unlink debian/ruleset/arches/i386.mk
unlink debian/ruleset/arches/armeb.mk
unlink debian/ruleset/arches/m32r.mk
unlink debian/ruleset/arches/amd64.mk
unlink debian/ruleset/arches/s390.mk
unlink debian/ruleset/arches/arm.mk
rmdir arches
unlink debian/ruleset/modules.mk
unlink debian/ruleset/common/README
unlink debian/ruleset/common/archvars.mk
unlink debian/ruleset/common/install_cmds.mk
unlink debian/ruleset/common/copt.mk
unlink debian/ruleset/common/pkgvars.mk
unlink debian/ruleset/common/automake.mk
unlink debian/ruleset/common/targets.mk
unlink debian/ruleset/common/perlvars.mk
unlink debian/ruleset/common/checklibs
unlink debian/ruleset/common/ChangeLog
unlink debian/ruleset/common/targets.dot
unlink debian/ruleset/common/debconf.mk
rmdir common
unlink debian/ruleset/architecture.mk
unlink debian/ruleset/targets/common.mk
unlink debian/ruleset/targets/source.mk
unlink debian/ruleset/targets/debug.mk
unlink debian/ruleset/targets/headers.mk
unlink debian/ruleset/targets/README
unlink debian/ruleset/targets/doc.mk
unlink debian/ruleset/targets/image.mk
unlink debian/ruleset/targets/ChangeLog
unlink debian/ruleset/targets/manual.mk
rmdir targets
unlink debian/ruleset/ChangeLog
unlink debian/ruleset/local.mk
unlink debian/ruleset/misc/config.mk
unlink debian/ruleset/misc/modules.mk
unlink debian/ruleset/misc/README
unlink debian/ruleset/misc/version_vars.mk
unlink debian/ruleset/misc/pkg_names.mk
unlink debian/ruleset/misc/ChangeLog
unlink debian/ruleset/misc/kernel_arch.mk
unlink debian/ruleset/misc/checks.mk
unlink debian/ruleset/misc/defaults.mk
rmdir misc
rmdir ruleset
unlink debian/ChangeLog
unlink debian/templates.in
unlink debian/control
unlink debian/examples/sample.module.control
unlink debian/examples/ChangeLog
unlink debian/examples/etc/sample.kernel-img.conf
unlink debian/examples/etc/kernel/postrm.d/grub_rm
unlink debian/examples/etc/kernel/postrm.d/yaird
unlink debian/examples/etc/kernel/postrm.d/force-build-link
unlink debian/examples/etc/kernel/postrm.d/initramfs
rmdir postrm.d
unlink debian/examples/etc/kernel/header_postinst.d/link
rmdir header_postinst.d
unlink debian/examples/etc/kernel/postinst.d/yaird
unlink debian/examples/etc/kernel/postinst.d/grub_conf
unlink debian/examples/etc/kernel/postinst.d/symlink_hook
unlink debian/examples/etc/kernel/postinst.d/force-build-link
unlink debian/examples/etc/kernel/postinst.d/initramfs
rmdir postinst.d
unlink debian/examples/etc/kernel/header_prerm.d/link
rmdir header_prerm.d
unlink debian/examples/etc/kernel/header_postrm.d/link
rmdir header_postrm.d
rmdir kernel
rmdir etc
rmdir examples
unlink debian/Config/config.k7
unlink debian/Config/config.ixp4xx
unlink debian/Config/config.mac
unlink debian/Config/config.m68k
unlink debian/Config/config.686
unlink debian/Config/config.mvme147
unlink debian/Config/config.powerpc-smp
unlink debian/Config/config.32
unlink debian/Config/config.xen0
unlink debian/Config/config.i386
unlink debian/Config/config.em64t-p4-smp
unlink debian/Config/config.amd64
unlink debian/Config/config.amd64-k8-smp
unlink debian/Config/config.prep
unlink debian/Config/config.s390
unlink debian/Config/config.alpha
unlink debian/Config/config.em64t-p4
unlink debian/Config/config.pmac
unlink debian/Config/config.mbx
unlink debian/Config/config.hppa
unlink debian/Config/config.386
unlink debian/Config/config.common
unlink debian/Config/config.itanium-smp
unlink debian/Config/config.amd64-generic
unlink debian/Config/config.s390x
unlink debian/Config/config.i486
unlink debian/Config/config.xenu
unlink debian/Config/config.amd64-k8
unlink debian/Config/config.mips
unlink debian/Config/config.64-smp
unlink debian/Config/config.powerpc
unlink debian/Config/config.powerpc-miboot
unlink debian/Config/config.i686
unlink debian/Config/config.powermac
unlink debian/Config/config.mckinley
unlink debian/Config/config.ia64
unlink debian/Config/config.footbridge
unlink debian/Config/config.apus
unlink debian/Config/config.sparc64
unlink debian/Config/config.bvme6000
unlink debian/Config/config.mckinley-smp
unlink debian/Config/config.armel
unlink debian/Config/config.itanium
unlink debian/Config/ChangeLog
unlink debian/Config/config.mvme16x
unlink debian/Config/config.sparc
unlink debian/Config/config.m32r
unlink debian/Config/config.hp
unlink debian/Config/config.q40
unlink debian/Config/config.um
unlink debian/Config/config.64
unlink debian/Config/config.alpha-generic
unlink debian/Config/config.s390-tape
unlink debian/Config/config.686-smp
unlink debian/Config/config.arm
unlink debian/Config/config.rpc
unlink debian/Config/config.sun3
unlink debian/Config/config.sparc64-smp
unlink debian/Config/config.powerpc64
unlink debian/Config/config
unlink debian/Config/config.chrp
unlink debian/Config/config.s3c2410
unlink debian/Config/config.atari
unlink debian/Config/config.amiga
unlink debian/Config/config.k7-smp
unlink debian/Config/config.i586
unlink debian/Config/config.alpha-smp
unlink debian/Config/config.32-smp
rmdir Config
rmdir build
unlink debian/stamp/conf/vars
unlink debian/stamp/conf/minimal_debian
unlink debian/stamp/conf/kernel-conf
unlink debian/stamp/conf/full-changelog
rmdir conf
rmdir stamp
unlink debian/config
unlink debian/scripts/kpkg-vercheck
unlink debian/scripts/ChangeLog
rmdir scripts
rmdir debian
exec make kpkg_version=12.032 -f /usr/share/kernel-package/ruleset/minimal.mk debian APPEND_TO_VERSION=-some-string-here  INITRD=YES 
====== making target debian/stamp/conf/minimal_debian [new prereqs: ]======
This is kernel package version 12.032.
test -d debian             || mkdir debian
test ! -e stamp-building || rm -f stamp-building
install -p -m 755 /usr/share/kernel-package/rules debian/rules
for file in ChangeLog  Control  Control.bin86 config templates.in rules; do                                      \
            cp -f  /usr/share/kernel-package/$file ./debian/;                               \
        done
for dir  in Config docs examples ruleset scripts pkg po;  do                                      \
          cp -af /usr/share/kernel-package/$dir  ./debian/;                                 \
        done
test -f debian/control || sed         -e 's/=V/2.6.32.11+drm33.2-some-string-here/g'  \
                -e 's/=D/2.6.32.11+drm33.2-some-string-here-10.00.Custom/g'         -e 's/=A/i386/g'  \
        -e 's/=SA//g'  \
        -e 's/=I//g'                    \
        -e 's/=CV/2.6/g'                \
        -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                \
        -e 's/=ST/linux/g'      -e 's/=B/i386/g'    \
                  /usr/share/kernel-package/Control > debian/control
test -f debian/changelog ||  sed -e 's/=V/2.6.32.11+drm33.2-some-string-here/g'       \
            -e 's/=D/2.6.32.11+drm33.2-some-string-here-10.00.Custom/g'        -e 's/=A/i386/g'       \
            -e 's/=ST/linux/g'     -e 's/=B/i386/g'         \
            -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                            \
             /usr/share/kernel-package/changelog > debian/changelog
chmod 0644 debian/control debian/changelog
test -d ./debian/stamp || mkdir debian/stamp 
make -f debian/rules debian/stamp/conf/kernel-conf
make[1]: Entering directory `/home/sentello/src/linux-source-2.6.32'
====== making target debian/stamp/conf/kernel-conf [new prereqs: ]======
make EXTRAVERSION=.11+drm33.2-some-string-here   ARCH=i386 \
                    oldconfig;                                      
make[2]: Entering directory `/home/sentello/src/linux-source-2.6.32'
scripts/kconfig/conf -o arch/x86/Kconfig
#
# configuration written to .config
#
make[2]: Leaving directory `/home/sentello/src/linux-source-2.6.32'
make EXTRAVERSION=.11+drm33.2-some-string-here   ARCH=i386 prepare
make[2]: Entering directory `/home/sentello/src/linux-source-2.6.32'
scripts/kconfig/conf -s arch/x86/Kconfig
make[2]: Leaving directory `/home/sentello/src/linux-source-2.6.32'
make[2]: Entering directory `/home/sentello/src/linux-source-2.6.32'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
  CALL    scripts/checksyscalls.sh
make[2]: Leaving directory `/home/sentello/src/linux-source-2.6.32'
echo done > debian/stamp/conf/kernel-conf
make[1]: Leaving directory `/home/sentello/src/linux-source-2.6.32'
make -f debian/rules debian/stamp/conf/full-changelog
make[1]: Entering directory `/home/sentello/src/linux-source-2.6.32'
====== making target debian/stamp/conf/full-changelog [new prereqs: ]======
for file in ChangeLog  Control  Control.bin86 config templates.in rules; do            \
         cp -f  /usr/share/kernel-package/$file ./debian/;            \
    done
for dir  in Config docs examples ruleset scripts pkg po;    do                \
       cp -af /usr/share/kernel-package/$dir  ./debian/;                \
    done
install -p -m 755 /usr/share/kernel-package/rules debian/rules
sed         -e 's/=V/2.6.32.11+drm33.2-some-string-here/g'  \
                -e 's/=D/2.6.32.11+drm33.2-some-string-here-10.00.Custom/g'         -e 's/=A/i386/g'  \
        -e 's/=SA//g'  \
        -e 's/=I//g'                    \
        -e 's/=CV/2.6/g'                \
        -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                \
        -e 's/=ST/linux/g'      -e 's/=B/i386/g'    \
                  /usr/share/kernel-package/Control > debian/control
sed -e 's/=V/2.6.32.11+drm33.2-some-string-here/g' -e 's/=D/2.6.32.11+drm33.2-some-string-here-10.00.Custom/g'          \
        -e 's/=A/i386/g' -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g' \
        -e 's/=ST/linux/g'     -e 's/=B/i386/g'          \
        /usr/share/kernel-package/changelog > debian/changelog
chmod 0644 debian/control debian/changelog
make -f debian/rules debian/stamp/conf/kernel-conf
make[2]: Entering directory `/home/sentello/src/linux-source-2.6.32'
make[2]: `debian/stamp/conf/kernel-conf' is up to date.
make[2]: Leaving directory `/home/sentello/src/linux-source-2.6.32'
make[1]: Leaving directory `/home/sentello/src/linux-source-2.6.32'
echo done > debian/stamp/conf/minimal_debian
exec debian/rules  APPEND_TO_VERSION=-some-string-here  INITRD=YES  kernel-image kernel-headers 
====== making target debian/stamp/conf/vars [new prereqs: ]======

====== making target debian/stamp/build/kernel [new prereqs: vars]======
This is kernel package version 12.032.
restore_upstream_debianization
test ! -f scripts/package/builddeb.kpkg-dist ||    mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/Makefile.kpkg-dist ||    mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
/usr/bin/make  EXTRAVERSION=.11+drm33.2-some-string-here  ARCH=i386 \
                 bzImage
make[1]: Entering directory `/home/sentello/src/linux-source-2.6.32'
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/home/sentello/src/linux-source-2.6.32'
make[1]: Entering directory `/home/sentello/src/linux-source-2.6.32'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
  CALL    scripts/checksyscalls.sh
  CHK     include/linux/compile.h
  VDSOSYM arch/x86/vdso/vdso32-int80-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-sysenter-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-syms.lds
  LD      arch/x86/vdso/built-in.o
  LD      arch/x86/built-in.o
  CC      drivers/acpi/osl.o
In file included from drivers/acpi/osl.c:65:
/dsdt/dsdt.txt:18: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/dsdt/dsdt.txt:18: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/dsdt/dsdt.txt:18: error: expected declaration specifiers or &#8216;...&#8217; before numeric constant
/dsdt/dsdt.txt:18: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/dsdt/dsdt.txt:18: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/dsdt/dsdt.txt:18: error: expected declaration specifiers or &#8216;...&#8217; before numeric constant
/dsdt/dsdt.txt:19: warning: return type defaults to &#8216;int&#8217;
/dsdt/dsdt.txt:19: warning: function declaration isn&#8217;t a prototype
/dsdt/dsdt.txt: In function &#8216;DefinitionBlock&#8217;:
/dsdt/dsdt.txt:20: error: implicit declaration of function &#8216;Name&#8217;
/dsdt/dsdt.txt:20: error: &#8216;VERS&#8217; undeclared (first use in this function)
/dsdt/dsdt.txt:20: error: (Each undeclared identifier is reported only once
/dsdt/dsdt.txt:20: error: for each function it appears in.)
/dsdt/dsdt.txt:20: error: implicit declaration of function &#8216;Package&#8217;
/dsdt/dsdt.txt:21: error: expected &#8216;)&#8217; before &#8216;{&#8217; token
/dsdt/dsdt.txt:26: error: expected &#8216;;&#8217; before &#8216;OperationRegion&#8217;
/dsdt/dsdt.txt:60: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:61: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:65: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:70: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:79: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:83: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:84: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:89: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:94: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:250: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:251: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:256: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:257: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:262: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:263: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:341: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:342: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:385: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:394: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:405: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:414: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:421: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:440: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:444: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:445: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:446: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:447: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:448: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:451: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:452: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:452: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:463: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:464: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:465: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:468: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:480: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:497: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:498: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:499: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:500: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:503: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:506: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:526: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:531: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:533: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:536: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:537: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:538: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:539: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:541: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:541: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:544: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:549: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:550: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:551: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:554: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:555: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:570: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:578: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:579: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:580: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:581: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:584: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:586: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:591: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:602: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:623: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:627: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:644: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:664: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:670: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:711: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:712: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:713: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:719: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:745: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:746: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:748: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:755: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:757: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:791: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:804: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:872: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:878: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:884: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:997: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:998: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1031: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1039: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1047: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1055: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1063: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1071: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1079: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1087: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1095: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1103: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1111: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1119: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1127: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1135: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1143: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1151: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1159: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1167: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1175: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1183: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1191: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1199: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1207: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1215: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1223: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1231: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1239: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1247: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1471: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1471: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1474: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1486: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1487: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1490: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1522: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1523: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1529: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1530: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1534: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1535: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1613: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1640: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1667: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1692: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1720: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:1780: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2374: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2377: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2378: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2379: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2384: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2385: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2386: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2390: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2396: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2399: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2400: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2404: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2405: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2408: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2413: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2418: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2423: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2428: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2433: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2441: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2442: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2443: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2449: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2450: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2451: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2455: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2456: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2457: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2461: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2465: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2466: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2467: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2468: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2772: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2784: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2794: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2795: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2797: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2812: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2827: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2839: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2849: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2850: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2852: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2867: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2882: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2894: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2904: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2905: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2907: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2922: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2937: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2949: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2959: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2960: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2962: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2977: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:2992: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3004: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3014: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3015: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3017: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3032: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3047: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3059: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3069: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3070: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3072: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3087: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3102: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3114: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3124: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3125: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3127: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3142: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3157: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3169: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3179: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3180: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3182: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3197: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3240: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3267: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3290: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3291: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3293: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3331: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3332: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3338: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3369: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3372: error: stray &#8216;\&#8217; in program
/dsdt/dsdt.txt:3426: error: stray &#8216;\&#8217; in program
drivers/acpi/osl.c: In function &#8216;acpi_os_table_override&#8217;:
drivers/acpi/osl.c:366: error: &#8216;AmlCode&#8217; undeclared (first use in this function)
make[3]: *** [drivers/acpi/osl.o] Error 1
make[2]: *** [drivers/acpi] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/home/sentello/src/linux-source-2.6.32'
make: *** [debian/stamp/build/kernel] Error 2
sentello@ubuntu:~/src/linux-source-2.6.32$ ^C

```Any help for new UBUNTU 10:04? :confused:

---

### Post by morecore on 2010-04-30
ke[3]: *** [drivers/acpi/osl.o] Error 1
make[2]: *** [drivers/acpi] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.32'
make: *** [debian/stamp/build/kernel] Error 2


Same problem here

---

### Post by morecore on 2010-05-01
You must use the dsdt.hex file and must not use the dsdt.aml file!! Then it works for Lucid Lynx and the 2.6.32 Kernel.


Greetings,
   Daniel

---

### Post by Sentello on 2010-05-02
How I can make form dsdt.txt HEX file :confused:

---

### Post by morecore on 2010-05-02
If you follow the initial Tutorial. Then you will see that "isam -tc <modifyd-dsdt>" will generate some dsdt.xyz files, the former mentioned dsdt.aml and also a dsdt.hex file.

---

### Post by Sentello on 2010-05-02
Yes, I see this. But i have my own dsdt.txt file :(

---

### Post by naujokas on 2010-05-03
is the amd64 kernel compilation any different, cause i feel like total idiot tried 4 times with no luck, i receive error for headers installation and then stuck on boot

(Reading database ... 141227 files and directories currently installed.)
Preparing to replace linux-headers-2.6.31.12-dsdt 2.6.31.12-dsdt-10.00.Custom (using linux-headers-2.6.31.12-dsdt_2.6.31.12-dsdt-10.00.Custom_amd64.deb) ...
Unpacking replacement linux-headers-2.6.31.12-dsdt ...
Setting up linux-headers-2.6.31.12-dsdt (2.6.31.12-dsdt-10.00.Custom) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.

---

### Post by morecore on 2010-05-05
Just to get us on a common denominator:

1. Get your dsdt file
cat /proc/acpi/dsdt > dsdt.dat

2. Decompile the file from 1.
iasl -d dsdt.dat
which leads to dsdt.dsl

3.Now you can make your changes in dsdt.dsl

4. Reassemble the changed file
iasl -tc dsdt.dsl
which leads to two different files dsdt.aml and dsdt.hex

5. Now you can copy the /boot/config-2.6.32-21-generic to /src/linux-source-2.6.32/.config and make menuconfig (or something else) and alter the kernel parameters accordantly and save them.

6. Compile and install (check for the initrd eventually you have to create your own, see mkinitramfs)

7. Check your grub.cfg and make sure that you can boot your old kernel

8. Reboot

---

### Post by morecore on 2010-05-05
@naujoka: nope - i compiled also an amd64 kernel

Did you upgraded your system or why to you have a 2.6.31 kernel?

---

### Post by naujokas on 2010-05-05
i did upgraded but i think im going back to karmic, lucid as for now not in the best shape, do you get messed up desktop from time to time using firefox just went in some page on ubuntu community an boom :( never happened on karmic

do you have to do update-initramfs -u ???

---

### Post by Sentello on 2010-05-10
Any new solution for 10.04?

---

### Post by s.mulleady1122 on 2010-05-13
I compiled a new kernel for Gateway LT31 users based on the latest ubuntu source files using cyberey66's guide! 

[http://www.zshare.net/download/76287458e51a5c06/](http://www.zshare.net/download/76287458e51a5c06/)

I'm using 10.04 and all is well. Here are the files and some instructions

If using Ubuntu 10.04 then you have to copy these files as the script isn't automatically run anymore

```
sudo cp /usr/share/doc/kernel-package/examples/etc/kernel/postinst.d/initramfs /etc/kernel/postinst.d/initramfs
sudo cp /usr/share/doc/kernel-package/examples/etc/kernel/postrm.d/initramfs /etc/kernel/postrm.d/initramfs
```

(If you get an error, than make the directories)

Delete the nvidia-common file located in /etc/kernel/postinst.d

If using 9.10 start here

Go do the directory of the deb files and install
```
sudo dpkg -i linux-image-2.6.32.11_2.6.32.11-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.32.11_2.6.32.11-10.00.Custom_i386.deb
```

install Powernowd (The best daemon to use, sets it to on demand at the lowest freq and dynamically sets it up)

```
sudo apt-get install powernowd
```

Restart

Enjoy Frequency scaling on Ubuntu 10.04 and 9.10!

---

### Post by Sentello on 2010-05-19
How you do it? Whatever I'm doing everithing what is in tutorial and I fail :(

---

### Post by s.mulleady1122 on 2010-05-19
> **Sentello said:**
> How you do it? Whatever I'm doing everithing what is in tutorial and I fail :(

What error are you getting and when are you getting it

---

### Post by Sentello on 2010-05-24
I don't received any error during this process. :(

I recorded it
1. part
```
http://www.megaupload.com/?d=UXMQA97J
```2. part
After the successful kernel build, 
```
http://www.megaupload.com/?d=BZ164NUQ
```3. part
I restart notebook, and still nothing working correctly. Why ?:confused:

thx.

---

### Post by s.mulleady1122 on 2010-05-25
I can't see the first part to your video unfortunatly. But are you sure you're compiling the kernel pointing to the directory where your DSDT file is?

---

### Post by s.mulleady1122 on 2010-05-25
Ok I saw the first part, you pointed to the DSDT and compiled it.

What laptop do you have? Did you check if scaling worked with the kernel you compiled?

---

### Post by Sentello on 2010-05-26
I have Fujitsu Siemens Amilo L7310GW with Celeron M380

In Ubuntu 9.04 and Ubuntu 10.04:
> sentello@sentello-laptop:~$ sudo cpufreq-selector -g ondemand
[sudo] password for sentello: 
No cpufreq support
> sentello@sentello-laptop:~$ sudo cpufreq-selector -g performance
[sudo] password for sentello: 
Error calling SetGovernor: Error setting governor on cpu 0: No cpufreq support


---

### Post by s.mulleady1122 on 2010-05-26
try 

```
sudo modprobe p4-clockmod
```

See if the proper module for changing frequency is loaded.

Also some useful info:

> Speed Step

For using the speed step with the celeron M you must add the module p4-clockmod.
Kernel Options

When compiling the kernel choose the pentium-M processot type

---

### Post by Sentello on 2010-05-26
Ok i try it. It`s working

[IMG]http://img72.imageshack.us/img72/6183/screenshotbk.png[/IMG]

And now i must add module for changing CPU frq. ?
How ? :)
Where is this option?
```
http://img36.imageshack.us/i/screenshot1jgk.png/
```

thx. I am linux beginner

---

### Post by s.mulleady1122 on 2010-05-26
Ok so it works now, no need to recompile. Just install the Powernowd from Synaptic and set it to ondemand using that applet on the panel. (this is what I use, there are multiple ways to do it)



[IMG]http://img89.imageshack.us/img89/2739/screenjw.png[/IMG]

---

### Post by Sentello on 2010-05-26
Done, and now?

---

### Post by s.mulleady1122 on 2010-05-26
> **Sentello said:**
> Done, and now?

Well theres nothing more to it. The Frequency of the CPU will automatically go up and down depending on the load, saving power and making the laptop cooler.

---

### Post by Sentello on 2010-05-26
Okay, but still don't working USB, etc. How i fix problem with DSDT?
My DSDT working perfectly in Ubuntu 9.04, but in 10.04 i have some problems... :( [COLOR=#000000]Compiled kernel does not resolve anything[/COLOR]

---

### Post by cyberey66 on 2010-07-12
For those who want a permanent solutions see this post, 

[http://swiss.ubuntuforums.org/showpost.php?p=9464992&postcount=66](http://swiss.ubuntuforums.org/showpost.php?p=9464992&postcount=66)

If you have a patched DSDT and your computer has phoenix bios, you can simply just replace the buggy DSDT in your bios directly.

---

### Post by spaceballl on 2010-07-15
Can someone set me straight? I'm a bit confused...
- What is a DSDT file?
- With the powernow fix in the most recent version of the kernel, do I still need to do modifications to the BIOS / DSDT for the Gateway LT31? Why?
- I've seen so many solutions posted here - all a bit different. what is the best way?
- Any chance all of this will "just work" with the next version of Ubuntu?

---

### Post by cyberey66 on 2010-07-15
Can someone set me straight? I'm a bit confused...
- What is a DSDT file?
- With the powernow fix in the most recent version of the kernel, do I still need to do modifications to the BIOS / DSDT for the Gateway LT31? Why?

[http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)
[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

Basically the DSDT defines the computer hardware configuration including the power saving states of the CPU.  There are two compilers to create the DSDT, one from Intel and one from Microsoft.  The Microsoft does not comply with the ACPI specifications and is used by many manufacturers.


- I've seen so many solutions posted here - all a bit different. what is the best way?
You have two options; 1. compile each new kernel you use to override the bios with a corrected DSDT you provide, 2. modify your bios to include the correct DSDT and flash it.  I personally think the second option is best as it is a permanent and 'proper' fix.


- Any chance all of this will "just work" with the next version of Ubuntu?

Most likely never, the developers expect that the DSDT is written to comply with the standard, which some don't.  The developers have also been moving away from overriding the DSDT for ideological reasons.  So don't expect future versions to just work.  However, if you do modify your bios to include a corrected DSDT, all future versions will 'just work'.  I think this is the best path. 

 I would first, compile the kernel to override the bios with the new DSDT to make sure it works.  If it works well, I would then pursue modifying the bios.

---

