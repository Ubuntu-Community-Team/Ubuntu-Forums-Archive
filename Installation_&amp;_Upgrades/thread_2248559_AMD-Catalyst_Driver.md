---
title: "AMD-Catalyst Driver"
date: 2014-10-15
forum: Installation &amp; Upgrades
---

### Post by sing0512 on 2014-10-15
I am trying to install AMD catalyst 14.9 (downloaded from AMD official website) on my Kubuntu 14.04 64-bit machine. However, it always throws an error message while installing. Below is the installaion log.

```
NOTE: If your system has logged the missing packages required for installation, install them in the order as per the log file to resolve package-dependency issues.
Package build failed!
Package build utility output:
Cleaning in directory .
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
# remove any file generated from a template
for file in *.in; do \
        # strip only the last .in from the name \
        filename=`echo $file | sed -e "s|.in||"` \
        rm -f ; \
    done
rm -f debian/fglrx.substvars
dh clean
   dh_testdir
   dh_auto_clean
   dh_clean
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:14.301-0ubuntu1
dpkg-buildpackage: source distribution trusty
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.E4ZnFV
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-dev.links \
             fglrx-amdcccle.install \
             fglrx.grub-gfxpayload \
             fglrx.dirs \
             fglrx.links \
             fglrx.postinst \
             fglrx.postrm \
             fglrx.preinst \
             fglrx.prerm \
             overrides/fglrx; do \
        sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#LIBDIR#|usr/lib|g" \
            -e "s|#LIBDIR32#|usr/lib32|g" \
            -e "s|#BINDIR#|usr/bin|g" \
            -e "s|#SYSCONFDIR#|etc|g" \
            -e "s|#MANDIR#|usr/share/man/man1|g" \
            -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
            -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
            -e "s|#ALTPRIORITY#|1000|g" \
            -e "s|#PXALTPRIORITY#|900|g" \
            -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
            -e "s|#DATADIR#|usr/share|g" \
            -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
            -e "s|#PKGDATADIR#|usr/share/fglrx|g" \
            -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
            -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
            -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \
            -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
            -e "s|#DRIVERNAME#|fglrx|g" \
            -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
            -e "s|#DRIVERSRCNAME#||g" \
            -e "s|#INCLUDEDIR#|usr/include|g" \
            -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
            -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
            -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#PXDIR#|usr/lib/pxpress|g" \
            -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
            -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
            -e "s|#PXDIRNAME#|pxpress|g" \
            -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
            -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
            -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
            -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
            -e "s|#CVERSION#|14.301|g" \
            -e "s|#SRCXARCH#|xpic_64a|g" \
            -e "s|#SRCARCH#|x86_64|g" \
            -e "s|#SRCOTHERARCH#|x86|g" \
            -e "s|#SRCLIBDIR#|lib64|g" \
            -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
            -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
dh build
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
# Generate the xserver ABI dependencies
cat debian/substvars >> debian/fglrx.substvars
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib64" "usr/share/ati"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/*libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/fglrx-libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdirs -pfglrx-dev
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude LICENSE.TXT
dh_installdocs -pfglrx debian/AUTHORS
dh_installdocs -pfglrx debian/copyright
dh_installinit -pfglrx -n --name="atieventsd" --no-start --update-rcd-params="defaults 31"
Use of uninitialized value $filename in concatenation (.) or string at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 410.
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
dh_install -pfglrx
for i in \
            debian/fglrx/usr/lib/fglrx/bin/clinfo \
            debian/fglrx/usr/lib/fglrx/bin/atiode \
            debian/fglrx/usr/lib/fglrx/bin/amdnotifyui \
            debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib/fglrx/*libGL.so.*.* \
            debian/fglrx/usr/lib/fglrx/*libOpenCL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib/fglrx/bin/clinfo
- debian/fglrx/usr/lib/fglrx/bin/atiode
- debian/fglrx/usr/lib/fglrx/bin/amdnotifyui
- debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib/fglrx/fglrx-libGL.so.1.2
- debian/fglrx/usr/lib/fglrx/libOpenCL.so.1
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Make sure that every binary in bin is executable
find debian/fglrx/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Rename libraries which are supposed to have fglrx-libGL as a prefix
for lib in `find debian/fglrx/ -name 'fglrx-libGL*'`; \
        do \
            file_name=`echo $lib | awk -F/ '{print $NF}'`; \
            path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
            # Remove fglrx prefix \
            new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
            full_path=`echo "$path$new_name"`; \
            mv -f $lib $full_path; \
    done
# Rename libraries which are supposed to have fglrx-libglx as a prefix
for lib in `find debian/fglrx/ -name 'fglrx-libglx*'`; \
        do \
            file_name=`echo $lib | awk -F/ '{print $NF}'`; \
            path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
            new_path=`echo $path | sed -e 's/fglrx\/$//'`; \
            # Remove fglrx prefix \
            new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
            full_path=`echo "$new_path$new_name"`; \
            mv -f $lib $full_path; \
    done
# Create links for PowerXpress X modules (except for extensions)
for i in \
        debian/fglrx/usr/lib/fglrx/xorg/modules/* \
        ; do \
            orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
            if [ `echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules/||"` != "extensions" ]; then \
                link_name=$orig_name ; \
                link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules|usr/lib/pxpress/xorg/modules|"`; \
                dh_link -pfglrx $orig_name $link_name ; \
            fi \
        done
# Create links for PowerXpress libs (except for libGL)
for i in \
        debian/fglrx/usr/lib/fglrx/* \
        ; do \
            orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
            # Copy each file except for libGL* \
            if [ -f $i ]; then \
                if [ ! `echo $orig_name  | grep libGL` ]; then \
                    link_name=$orig_name ; \
                    link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx|usr/lib/pxpress/lib|"`; \
                    dh_link -pfglrx $orig_name $link_name ; \
                fi \
            else \
                # Here we only accept the dri directory \
                dir_name=`echo $orig_name | awk -F/ '{print $NF}'`; \
                if [ "$dir_name" = "dri" ]; then \
                    link_name=$orig_name ; \
                    link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx|usr/lib/pxpress/lib|"`; \
                    dh_link -pfglrx $orig_name $link_name ; \
                fi \
            fi \
        done
# Create links for PowerXpress 32bit libs (except for libGL)
for i in \
        debian/fglrx/usr/lib32/fglrx/* \
        ; do \
            orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
            # Copy each file except for libGL* \
            if [ -f $i ]; then \
                if [ ! `echo $orig_name  | grep libGL` ]; then \
                    link_name=$orig_name ; \
                    link_name=`echo $orig_name  | sed -e "s|usr/lib32/fglrx|usr/lib32/pxpress/lib|"`; \
                    dh_link -pfglrx $orig_name $link_name ; \
                fi \
            else \
                # Here we only accept the dri directory \
                dir_name=`echo $orig_name | awk -F/ '{print $NF}'`; \
                if [ "$dir_name" = "dri" ]; then \
                    link_name=$orig_name ; \
                    link_name=`echo $orig_name  | sed -e "s|usr/lib32/fglrx|usr/lib32/pxpress/lib|"`; \
                    dh_link -pfglrx $orig_name $link_name ; \
                fi \
            fi \
        done
# Blacklist any other driver that udev may want to load instead of fglrx
# and create an alias for the module so that it can be used as fglrx
printf '# This file was installed by fglrx\n# Do not edit this file manually\n\nblacklist radeon\nalias fglrx fglrx\nalias radeon off\nalias lbm-radeon off' > /tmp/fglrx.E4ZnFV/debian/fglrx/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/fglrx/ld.so.conf"
# ld.so.conf for PowerXpress
echo "/usr/lib/x86_64-linux-gnu/mesa" >        "/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib/pxpress/lib" >>    "/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib/i386-linux-gnu/mesa" >>    "/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib32/pxpress/lib" >>    "/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/pxpress/ld.so.conf"
# empty ld.so.conf for the fake multi-arch alternative
echo "" > "/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/fglrx/alt_ld.so.conf"
# empty ld.so.conf for the fake multi-arch alternative for PXpress
echo "" > "/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/pxpress/alt_ld.so.conf"
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h fglrx fglrx > \
        debian/fglrx.modaliases
dh_modaliases
rm debian/fglrx.modaliases
#Run the normal stuff
dh binary-arch
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a -Nfglrx
   dh_pysupport -a -Nfglrx
dh_pysupport: This program is deprecated, you should use dh_python2 instead. Migration guide: http://deb.li/dhs2p
   dh_perl -a -Nfglrx
   dh_link -a -Nfglrx
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/fglrx/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/pxpress/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.E4ZnFV'
dh_shlibdeps -l/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/fglrx/bin:/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/fglrx/sbin:/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin
dpkg-shlibdeps: error: no dependency information found for /usr/lib/x86_64-linux-gnu/libgcc_s.so.1 (used by debian/fglrx/usr/lib/fglrx/libatiadlxx.so)
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars -l/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/fglrx -l/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/fglrx/bin -l/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib/fglrx/sbin -l/tmp/fglrx.E4ZnFV/debian/fglrx/usr/lib32/fglrx debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/libamdocl64.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/
fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/clinfo debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/libamdhsasc64.so debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libOpenCL.so.1 debian/fglrx/usr/share/ati/lib64/libQtGui.so.4 debian/fglrx/usr/share/ati/lib64/libQtCore.so.4 returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 2
make[1]: Leaving directory `/tmp/fglrx.E4ZnFV'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Cleaning in directory .
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
# remove any file generated from a template
for file in *.in; do \
        # strip only the last .in from the name \
        filename=`echo $file | sed -e "s|.in||"` \
        rm -f ; \
    done
rm -f debian/fglrx.substvars
dh clean
   dh_testdir
   dh_auto_clean
   dh_clean
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:14.301-0ubuntu1
dpkg-buildpackage: source distribution trusty
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.o5HipX
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-dev.links \
             fglrx-amdcccle.install \
             fglrx.grub-gfxpayload \
             fglrx.dirs \
             fglrx.links \
             fglrx.postinst \
             fglrx.postrm \
             fglrx.preinst \
             fglrx.prerm \
             overrides/fglrx; do \
        sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#LIBDIR#|usr/lib|g" \
            -e "s|#LIBDIR32#|usr/lib32|g" \
            -e "s|#BINDIR#|usr/bin|g" \
            -e "s|#SYSCONFDIR#|etc|g" \
            -e "s|#MANDIR#|usr/share/man/man1|g" \
            -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
            -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
            -e "s|#ALTPRIORITY#|1000|g" \
            -e "s|#PXALTPRIORITY#|900|g" \
            -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
            -e "s|#DATADIR#|usr/share|g" \
            -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
            -e "s|#PKGDATADIR#|usr/share/fglrx|g" \
            -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
            -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
            -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \
            -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
            -e "s|#DRIVERNAME#|fglrx|g" \
            -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
            -e "s|#DRIVERSRCNAME#||g" \
            -e "s|#INCLUDEDIR#|usr/include|g" \
            -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
            -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
            -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#PXDIR#|usr/lib/pxpress|g" \
            -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
            -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
            -e "s|#PXDIRNAME#|pxpress|g" \
            -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
            -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
            -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
            -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
            -e "s|#CVERSION#|14.301|g" \
            -e "s|#SRCXARCH#|xpic_64a|g" \
            -e "s|#SRCARCH#|x86_64|g" \
            -e "s|#SRCOTHERARCH#|x86|g" \
            -e "s|#SRCLIBDIR#|lib64|g" \
            -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
            -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
dh build
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
# Generate the xserver ABI dependencies
cat debian/substvars >> debian/fglrx.substvars
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib64" "usr/share/ati"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/*libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/fglrx-libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdirs -pfglrx-dev
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude LICENSE.TXT
dh_installdocs -pfglrx debian/AUTHORS
dh_installdocs -pfglrx debian/copyright
dh_installinit -pfglrx -n --name="atieventsd" --no-start --update-rcd-params="defaults 31"
Use of uninitialized value $filename in concatenation (.) or string at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 410.
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
dh_install -pfglrx
for i in \
            debian/fglrx/usr/lib/fglrx/bin/clinfo \
            debian/fglrx/usr/lib/fglrx/bin/atiode \
            debian/fglrx/usr/lib/fglrx/bin/amdnotifyui \
            debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib/fglrx/*libGL.so.*.* \
            debian/fglrx/usr/lib/fglrx/*libOpenCL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib/fglrx/bin/clinfo
- debian/fglrx/usr/lib/fglrx/bin/atiode
- debian/fglrx/usr/lib/fglrx/bin/amdnotifyui
- debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib/fglrx/fglrx-libGL.so.1.2
- debian/fglrx/usr/lib/fglrx/libOpenCL.so.1
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Make sure that every binary in bin is executable
find debian/fglrx/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Rename libraries which are supposed to have fglrx-libGL as a prefix
for lib in `find debian/fglrx/ -name 'fglrx-libGL*'`; \
        do \
            file_name=`echo $lib | awk -F/ '{print $NF}'`; \
            path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
            # Remove fglrx prefix \
            new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
            full_path=`echo "$path$new_name"`; \
            mv -f $lib $full_path; \
    done
# Rename libraries which are supposed to have fglrx-libglx as a prefix
for lib in `find debian/fglrx/ -name 'fglrx-libglx*'`; \
        do \
            file_name=`echo $lib | awk -F/ '{print $NF}'`; \
            path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
            new_path=`echo $path | sed -e 's/fglrx\/$//'`; \
            # Remove fglrx prefix \
            new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
            full_path=`echo "$new_path$new_name"`; \
            mv -f $lib $full_path; \
    done
# Create links for PowerXpress X modules (except for extensions)
for i in \
        debian/fglrx/usr/lib/fglrx/xorg/modules/* \
        ; do \
            orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
            if [ `echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules/||"` != "extensions" ]; then \
                link_name=$orig_name ; \
                link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules|usr/lib/pxpress/xorg/modules|"`; \
                dh_link -pfglrx $orig_name $link_name ; \
            fi \
        done
# Create links for PowerXpress libs (except for libGL)
for i in \
        debian/fglrx/usr/lib/fglrx/* \
        ; do \
            orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
            # Copy each file except for libGL* \
            if [ -f $i ]; then \
                if [ ! `echo $orig_name  | grep libGL` ]; then \
                    link_name=$orig_name ; \
                    link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx|usr/lib/pxpress/lib|"`; \
                    dh_link -pfglrx $orig_name $link_name ; \
                fi \
            else \
                # Here we only accept the dri directory \
                dir_name=`echo $orig_name | awk -F/ '{print $NF}'`; \
                if [ "$dir_name" = "dri" ]; then \
                    link_name=$orig_name ; \
                    link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx|usr/lib/pxpress/lib|"`; \
                    dh_link -pfglrx $orig_name $link_name ; \
                fi \
            fi \
        done
# Create links for PowerXpress 32bit libs (except for libGL)
for i in \
        debian/fglrx/usr/lib32/fglrx/* \
        ; do \
            orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
            # Copy each file except for libGL* \
            if [ -f $i ]; then \
                if [ ! `echo $orig_name  | grep libGL` ]; then \
                    link_name=$orig_name ; \
                    link_name=`echo $orig_name  | sed -e "s|usr/lib32/fglrx|usr/lib32/pxpress/lib|"`; \
                    dh_link -pfglrx $orig_name $link_name ; \
                fi \
            else \
                # Here we only accept the dri directory \
                dir_name=`echo $orig_name | awk -F/ '{print $NF}'`; \
                if [ "$dir_name" = "dri" ]; then \
                    link_name=$orig_name ; \
                    link_name=`echo $orig_name  | sed -e "s|usr/lib32/fglrx|usr/lib32/pxpress/lib|"`; \
                    dh_link -pfglrx $orig_name $link_name ; \
                fi \
            fi \
        done
# Blacklist any other driver that udev may want to load instead of fglrx
# and create an alias for the module so that it can be used as fglrx
printf '# This file was installed by fglrx\n# Do not edit this file manually\n\nblacklist radeon\nalias fglrx fglrx\nalias radeon off\nalias lbm-radeon off' > /tmp/fglrx.o5HipX/debian/fglrx/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/fglrx/ld.so.conf"
# ld.so.conf for PowerXpress
echo "/usr/lib/x86_64-linux-gnu/mesa" >        "/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib/pxpress/lib" >>    "/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib/i386-linux-gnu/mesa" >>    "/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib32/pxpress/lib" >>    "/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/pxpress/ld.so.conf"
# empty ld.so.conf for the fake multi-arch alternative
echo "" > "/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/fglrx/alt_ld.so.conf"
# empty ld.so.conf for the fake multi-arch alternative for PXpress
echo "" > "/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/pxpress/alt_ld.so.conf"
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h fglrx fglrx > \
        debian/fglrx.modaliases
dh_modaliases
rm debian/fglrx.modaliases
#Run the normal stuff
dh binary-arch
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a -Nfglrx
   dh_pysupport -a -Nfglrx
dh_pysupport: This program is deprecated, you should use dh_python2 instead. Migration guide: http://deb.li/dhs2p
   dh_perl -a -Nfglrx
   dh_link -a -Nfglrx
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/fglrx/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/pxpress/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.o5HipX'
dh_shlibdeps -l/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/fglrx/bin:/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/fglrx/sbin:/tmp/fglrx.o5HipX/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: error: no dependency information found for /usr/lib/x86_64-linux-gnu/libgcc_s.so.1 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui)
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars -l/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/fglrx -l/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/fglrx/bin -l/tmp/fglrx.o5HipX/debian/fglrx/usr/lib/fglrx/sbin -l/tmp/fglrx.o5HipX/debian/fglrx/usr/lib32/fglrx debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/libamdocl64.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/
fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/clinfo debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/libamdhsasc64.so debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libOpenCL.so.1 debian/fglrx/usr/share/ati/lib64/libQtGui.so.4 debian/fglrx/usr/share/ati/lib64/libQtCore.so.4 returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 2
make[1]: Leaving directory `/tmp/fglrx.o5HipX'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
[Error] Generate Package - error generating package : Ubuntu/trusty

```

This is my AMD device information queried by lspci.
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos XT [Radeon HD 7470/8470 / R5 235 OEM]
```

Does anyone have ideas to resolve this problem?

Thanks,

---

### Post by J0nDaFr3aK on 2014-12-03
Same problem here, with similar log file... 
I have Lubuntu..

---

