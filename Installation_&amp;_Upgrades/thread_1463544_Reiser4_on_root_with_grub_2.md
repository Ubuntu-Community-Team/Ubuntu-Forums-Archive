---
title: "Reiser4 on root with grub 2"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by joshruehlig on 2010-04-27
I would like to create a 10.04 lucid install on a reiser4 partition, every guide I have seen either only puts a reiser4 directory, or uses grub legacy. These are what the steps I believe I would need to do to accomplish this... please read through them and direct me through my mistakes, thanks

* Partiton my drive with
/(to have ubuntu installed), /(to have ubuntu copied over)

* install kernel source, tools ect... to build a reiser4 enabled kernel

* change /(to have ubuntu copied over) into reiser4 partition

* Copy /(to have ubuntu installed) to reiser4 partition
(I am assuming from a live cd)

* Change fstab to use reiser4 partition as /root, change which partition boots. (Changing the boot flag has never seemed to make a difference with me when editing with parted...) **(This is where I get totally lost...)**

**(Do I need a seperate ext2 /boot partition? I found one guide that explains this with grub2)**

**I searched but haven't seen a guide to effectively boot a reiser4 partition with grub2.** I have seen a few that recommend creating a second ext2 partition as /boot with grub legacy.

Thank you for your time

---

### Post by joshruehlig on 2010-04-27
Not sure where I was supposed to put this thread, didn't see anything about filesystems...

I think I will try creating a seperate /boot,** does this mean Ill need to put it in the MBR **(I am gonna erase and start from a freshly alligned drive)? **How do I edit whats in the MBR?**(if I need to...)

I think I found something that will be useful for the fstab step [http://ubuntuforums.org/showthread.php?t=416393](http://ubuntuforums.org/showthread.php?t=416393)

BTW - I am installing onto a 64GB Runcore Double Wide PATA SSD for Dell Mini 9's.

---

### Post by psusi on 2010-04-27
Why do you want to use reiser4?  It isn't included in the upstream kernel, isn't well tested, and isn't supported since the main author is in prison.  I don't think grub understands it, so yes, you will need to create a /boot partition using a filesystem that grub understands.  Assuming you build a custom kernel that understands reiser4, then that should be all you need to do.

---

### Post by joshruehlig on 2010-04-27
I just wanted to experiment with it, keeping both a reiser4 and ext4 partition on my ssd. I wanted to see if I see any real world performance difference, plus the extra compression would help.

---

### Post by joshruehlig on 2010-04-28
Well I made a rieser enabled kernel and it didn't boot... Heres my steps

downloaded (enable-reiser4patch) / .sign/ _(2.6.32.12 kernel) from kernel.orgto /usr/src_
**(was this already my first mistake? 2.6.32.12 was the only one I saw on their page)**

unpacked both, cd into the 2.6.32.12 directory

patched kernel

 cp /boot/config-$(uname -r)  /usr/src/linux-2.6.32.12/.config
 
make menuconfig (showed errors so I got packages)
{enabled reiser4}
[I]
make-kpkg (didn't work, finished too quickly with no errors, this is probably where I messed up)

so instead I ran 
[/I]make-kpkg clean
_make-kpkg -initrd --revision=ck12 kernel_image kernel_headers  modules_image_
(because I saw it on another post)

This created a package that I unpacked, then ran 
update-grub

Rebooted into kernel and nothing, just the cursor...
-----------------------------
I underlined anywhere I think I could have messed up...

Links
[http://linuxhelp.150m.com/installs/compile-kernel.htm](http://linuxhelp.150m.com/installs/compile-kernel.htm)
[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

Thanks, I'm not very good at this stuff..

---

### Post by joshruehlig on 2010-04-28
I redid everything with linux-2.6.32.21 instead, when I got to make-kpkg this is all I got, no package in /usr/src...

unlink debian/copyright
unlink debian/stamps/keep-dir
rmdir stamps
unlink debian/rules.d/0-common-vars.mk
unlink debian/rules.d/3-binary-indep.mk
unlink debian/rules.d/2-binary-arch.mk
unlink debian/rules.d/4-checks.mk
unlink debian/rules.d/5-udebs.mk
unlink debian/rules.d/1-maintainer.mk
rmdir rules.d
unlink debian/tests/check-aliases
unlink debian/tests/README
rmdir tests
unlink debian/control-scripts/headers-postinst
unlink debian/control-scripts/prerm
unlink debian/control-scripts/postrm
unlink debian/control-scripts/postinst
unlink debian/control-scripts/preinst
rmdir control-scripts
unlink debian/commit-templates/config-updates
unlink debian/commit-templates/bumpabi
unlink debian/commit-templates/sauce-patch
unlink debian/commit-templates/newrelease
unlink debian/commit-templates/external-driver
unlink debian/commit-templates/missing-modules
unlink debian/commit-templates/upstream-patch
rmdir commit-templates
unlink debian/control
unlink debian/tools/perf
rmdir tools
unlink debian/scripts/sub-flavour
unlink debian/scripts/abi-check
unlink debian/scripts/control-create
unlink debian/scripts/module-check
unlink debian/scripts/misc/retag
unlink debian/scripts/misc/insert-changes.pl
unlink debian/scripts/misc/insert-ubuntu-changes
unlink debian/scripts/misc/getabis
unlink debian/scripts/misc/splitconfig.pl
unlink debian/scripts/misc/git-ubuntu-log
unlink debian/scripts/misc/kernelconfig
rmdir misc
unlink debian/scripts/link-headers
unlink debian/scripts/config-check
rmdir scripts
unlink debian/debian.env
unlink debian/control.stub
unlink debian/compat
unlink debian/rules
unlink debian/config/enforce
rmdir config
unlink debian/changelog
rmdir debian
exec make kpkg_version=12.032 -f /usr/share/kernel-package/ruleset/minimal.mk debian
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
test -f debian/control || sed         -e 's/=V/2.6.32.11+drm33.2/g'  \
                -e 's/=D/2.6.32.11+drm33.2-10.00.Custom/g'         -e 's/=A/i386/g'  \
        -e 's/=SA//g'  \
        -e 's/=I//g'                    \
        -e 's/=CV/2.6/g'                \
        -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                \
        -e 's/=ST/linux/g'      -e 's/=B/i386/g'    \
                  /usr/share/kernel-package/Control > debian/control
test -f debian/changelog ||  sed -e 's/=V/2.6.32.11+drm33.2/g'       \
            -e 's/=D/2.6.32.11+drm33.2-10.00.Custom/g'        -e 's/=A/i386/g'       \
            -e 's/=ST/linux/g'     -e 's/=B/i386/g'         \
            -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                            \
             /usr/share/kernel-package/changelog > debian/changelog
chmod 0644 debian/control debian/changelog
test -d ./debian/stamp || mkdir debian/stamp 
make -f debian/rules debian/stamp/conf/kernel-conf
make[1]: Entering directory `/usr/src/linux-2.6.32'
====== making target debian/stamp/conf/kernel-conf [new prereqs: ]======
make    ARCH=i386 \
                    oldconfig;                                      
make[2]: Entering directory `/usr/src/linux-2.6.32'
scripts/kconfig/conf -o arch/x86/Kconfig
#
# configuration written to .config
#
make[2]: Leaving directory `/usr/src/linux-2.6.32'
make    ARCH=i386 prepare
make[2]: Entering directory `/usr/src/linux-2.6.32'
scripts/kconfig/conf -s arch/x86/Kconfig
make[2]: Leaving directory `/usr/src/linux-2.6.32'
make[2]: Entering directory `/usr/src/linux-2.6.32'
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
  CC      kernel/bounds.s
  GEN     include/linux/bounds.h
  CC      arch/x86/kernel/asm-offsets.s
  GEN     include/asm/asm-offsets.h
  CALL    scripts/checksyscalls.sh
make[2]: Leaving directory `/usr/src/linux-2.6.32'
echo done > debian/stamp/conf/kernel-conf
make[1]: Leaving directory `/usr/src/linux-2.6.32'
make -f debian/rules debian/stamp/conf/full-changelog
make[1]: Entering directory `/usr/src/linux-2.6.32'
====== making target debian/stamp/conf/full-changelog [new prereqs: ]======
for file in ChangeLog  Control  Control.bin86 config templates.in rules; do    \
         cp -f  /usr/share/kernel-package/$file ./debian/;            \
    done
for dir  in Config docs examples ruleset scripts pkg po;    do        \
       cp -af /usr/share/kernel-package/$dir  ./debian/;            \
    done
install -p -m 755 /usr/share/kernel-package/rules debian/rules
sed         -e 's/=V/2.6.32.11+drm33.2/g'  \
                -e 's/=D/2.6.32.11+drm33.2-10.00.Custom/g'         -e 's/=A/i386/g'  \
        -e 's/=SA//g'  \
        -e 's/=I//g'                    \
        -e 's/=CV/2.6/g'                \
        -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                \
        -e 's/=ST/linux/g'      -e 's/=B/i386/g'    \
                  /usr/share/kernel-package/Control > debian/control
sed -e 's/=V/2.6.32.11+drm33.2/g' -e 's/=D/2.6.32.11+drm33.2-10.00.Custom/g'          \
        -e 's/=A/i386/g' -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g' \
        -e 's/=ST/linux/g'     -e 's/=B/i386/g'          \
        /usr/share/kernel-package/changelog > debian/changelog
chmod 0644 debian/control debian/changelog
make -f debian/rules debian/stamp/conf/kernel-conf
make[2]: Entering directory `/usr/src/linux-2.6.32'
make[2]: `debian/stamp/conf/kernel-conf' is up to date.
make[2]: Leaving directory `/usr/src/linux-2.6.32'
make[1]: Leaving directory `/usr/src/linux-2.6.32'
echo done > debian/stamp/conf/minimal_debian
exec debian/rules  
nothing to be done.

---

### Post by psusi on 2010-04-28
Just make install and it should put the new kernel image in /boot, then update-initramfs should find it and build an initrd for it, then update-grub should add it to your grub menu.

---

### Post by joshruehlig on 2010-04-28
Thanks, that kernel created a 2.6.32.11 which booted but mouse didn't work, I think I should enable more modules when make menuconfig. 

Ill try this again from a clean slate and post later

---

### Post by davidogg on 2010-08-11
> **joshruehlig said:**
> Thanks, that kernel created a 2.6.32.11 which booted but mouse didn't work, I think I should enable more modules when make menuconfig. 

Ill try this again from a clean slate and post later

Any luck?

---

