---
title: "HELP - ATI driver install issue/error"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by JonnyRock on 2010-10-12
I am using Linux Mint 9.

I have an ATI HD4830 graphics card and i am trying to install the latest ATI drivers (ati-driver-installer-10-9-x86.x86_64.run) but get this error. Can anyone help please?

i was following the following this [how to guide]("http://brainacle.com/2010/9/9/install-ati-10-8-drivers-on-ubuntu-lucid-linux-mint")

sudo ./ati-driver-installer-10-9-x86.x86_64.run --buildpkg Ubuntu/lucid
[sudo] password for media-pc: 
Created directory fglrx-install.68AEJl
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.771.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/lucid
Package build failed!
Package build utility output:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.771-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-amdcccle.install \
             overrides/fglrx; do \
        sed -e "s|#XMODDIR#|usr/lib/fglrx/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32/fglrx|"   \
            -e "s|#LIBDIR#|lib|"       \
            -e "s|#DRIDIR#|usr/lib/fglrx|"       \
            -e "s|#CVERSION#|8.771|"   \
            -e "s|#XARCH#|x750|"   \
            -e "s|#ARCH#|x86|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x750     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
        arch/x86/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 debian/rules binary
#Steps that we can't easily represent in debhelper files or .in files yet
dh_installdirs -pfglrx
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
Duplicate specification "O=s" for option "O"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
dh_install -pfglrx
for i in \
            debian/fglrx/usr/lib/fglrx/bin/atiode \
            debian/fglrx/usr/lib/fglrx/bin/amdnotifyui \
            debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib/fglrx/bin/atiode
- debian/fglrx/usr/lib/fglrx/bin/amdnotifyui
- debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.A3riWO/debian/fglrx/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.A3riWO/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary-arch
   dh_testroot -a -Nfglrx -Nfglrx-amdcccle
   dh_prep -a -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -a -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a
   dh_installexamples -a
   dh_installman -a
   dh_installcatalogs -a
   dh_installcron -a
   dh_installdebconf -a
   dh_installemacsen -a
   dh_installifupdown -a
   dh_installinfo -a
   dh_pysupport -a
   dh_installinit -a -Nfglrx
Duplicate specification "O=s" for option "O"
   dh_installmenu -a
   dh_installmime -a
   dh_installmodules -a
   dh_installlogcheck -a
   dh_installlogrotate -a
   dh_installpam -a
   dh_installppp -a
   dh_installudev -a
   dh_installwm -a
   dh_installxfonts -a
   dh_bugfiles -a
   dh_lintian -a
   dh_gconf -a
   dh_icons -a
   dh_perl -a
   dh_usrlocal -a
   dh_link -a
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.A3riWO'
dh_shlibdeps -l/tmp/fglrx.A3riWO/debian/fglrx/usr/lib/fglrx
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XOpenDisplay: it's probably a plugin.
dpkg-shlibdeps: warning: 29 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 contains an unresolvable reference to symbol XextCreateExtension: it's probably a plugin.
dpkg-shlibdeps: warning: 5 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib/libQtGui.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/fglrx_xgamma debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 9
make[1]: Leaving directory `/tmp/fglrx.A3riWO'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.68AEJl

---

### Post by searchfgold6789 on 2010-10-12
Try the ```
sudo ./ati-driver-installer-[version]-[CPU architecture].run –listpkg
```

---

### Post by JonnyRock on 2010-10-12
> **searchfgold6789 said:**
> Try the ```
sudo ./ati-driver-installer-[version]-[CPU architecture].run –listpkg
```

indeed....and this is why i used "--buildpkg Ubuntu/lucid" as i know that is my distro...

---

