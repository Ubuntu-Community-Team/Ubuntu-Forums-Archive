---
title: "ATI Driver package building fails"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by a-user on 2010-02-03
Well, i'm new here and not sure if this is the right section for my thread.

I have a recently updated ubuntu 9.10 that worked with the ati 9.12 drivers. so i once  build the ubuntu/karmic packages without problems. now yesterday i tried upgrading to the new 10.1 drivers but the package building failed.

first i thought it is the quite common problem with the new drivers i read about (e.g. phoronix forum) but it is different. additionally i tried building the 9.12 packages too and this also failed.
 so actually i am not able to build any ati-driver packages.

the single error that gets repeated is the follwoing:
> dpkg-shlibdeps: error: no dependency information found for  /usr/share/ati/lib64/libQtCore.so.4 (used by  debian/xorg-driver-fglrx/usr/sbin/amdnotifyui). 

i hope somebody can help me and tell me what changed, why i cannot anymore build the packages. except for updateting the system i didn't changed anything.

here is the full output of the 10.1 building. the same output i get trying to build the older 9.12 drivers:

```

[FONT=-moz-fixed]sudo sh ../Downloads/ati-driver-installer-10-1-x86.x86_64.run --buildpkg  Ubuntu/karmic 
Created directory fglrx-install.4SQjaE 
Verifying archive integrity... All good. 
Uncompressing ATI Proprietary Linux Driver-8.69................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................ 
================================================== 
 ATI Technologies Linux Driver Installer/Packager 
================================================== 
Generating package: Ubuntu/karmic 
Resolving build dependencies... 
Continuing package build 
Package build failed! 
Package build utility output: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2 
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions 
dpkg-buildpackage: set FFLAGS to default value: -g -O2 
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2 
dpkg-buildpackage: source package fglrx-installer 
dpkg-buildpackage: source version 2:8.690-0ubuntu1 
dpkg-buildpackage: source changed by ATI Technologies Inc.  [<http://ati.amd.com/support/driver.html>]("http://ati.amd.com/support/driver.html") 
 debian/rules build 
dpkg-buildpackage: host architecture amd64 
test -x debian/rules 
mkdir -p "." 
#Create important strings 
for i in 10fglrx \ 
             dkms.conf \ 
             xorg-driver-fglrx.install \ 
             xorg-driver-fglrx-dev.install \ 
             fglrx-kernel-source.install \ 
             fglrx-amdcccle.install \ 
             libamdxvba1.install \ 
             overrides/fglrx-kernel-source; do \ 
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \ 
            -e "s|#XMODDIR32#||" \ 
            -e "s|#DRIDIR32#|usr/lib32|"   \ 
            -e "s|#LIBDIR#|lib64|"       \ 
            -e "s|#DRIDIR#|usr/lib|"       \ 
            -e "s|#CVERSION#|8.690|"   \ 
            -e "s|#XARCH#|x740_64a|"   \ 
            -e "s|#ARCH#|x86_64|"   \ 
            debian/$i.in > debian/$i;      \ 
    done 
# remove exec bit on everything 
find arch \ 
        etc \ 
        lib \ 
        module \ 
        usr \ 
        x740_64a     -type f | xargs chmod -x 
find: `module': No such file or directory 
# set executable on user apps 
find arch/x86_64/usr/sbin \ 
        arch/x86_64/usr/X11R6/bin \ 
        usr/sbin/ -type f | xargs chmod a+x 
# set exec bit on scripts 
find lib etc debian -name "*.sh" -type f | xargs chmod +x 
# Generate modaliases 
sh -e debian/modaliases/fglrx_supported \ 
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \ 
        debian/modaliases/fglrx-modules.alias.override 
 debian/rules binary 
test -x debian/rules 
dh_testroot 
dh_clean -k 
dh_installdirs -A 
mkdir -p "." 
#Create important strings 
for i in 10fglrx \ 
             dkms.conf \ 
             xorg-driver-fglrx.install \ 
             xorg-driver-fglrx-dev.install \ 
             fglrx-kernel-source.install \ 
             fglrx-amdcccle.install \ 
             libamdxvba1.install \ 
             overrides/fglrx-kernel-source; do \ 
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \ 
            -e "s|#XMODDIR32#||" \ 
            -e "s|#DRIDIR32#|usr/lib32|"   \ 
            -e "s|#LIBDIR#|lib64|"       \ 
            -e "s|#DRIDIR#|usr/lib|"       \ 
            -e "s|#CVERSION#|8.690|"   \ 
            -e "s|#XARCH#|x740_64a|"   \ 
            -e "s|#ARCH#|x86_64|"   \ 
            debian/$i.in > debian/$i;      \ 
    done 
# remove exec bit on everything 
find arch \ 
        etc \ 
        lib \ 
        module \ 
        usr \ 
        x740_64a     -type f | xargs chmod -x 
find: `module': No such file or directory 
# set executable on user apps 
find arch/x86_64/usr/sbin \ 
        arch/x86_64/usr/X11R6/bin \ 
        usr/sbin/ -type f | xargs chmod a+x 
# set exec bit on scripts 
find lib etc debian -name "*.sh" -type f | xargs chmod +x 
# Generate modaliases 
sh -e debian/modaliases/fglrx_supported \ 
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \ 
        debian/modaliases/fglrx-modules.alias.override 
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx 
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx 
dh_installinfo -pxorg-driver-fglrx 
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx 
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx 
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx 
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx 
dh_link -pxorg-driver-fglrx 
dh_installmime -pxorg-driver-fglrx 
#driver package 
dh_install -XlibAMD -pxorg-driver-fglrx  "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32" 
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"      "usr/lib32" 
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                      "usr/lib32" 
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx" 
for i in \ 
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \ 
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \ 
            ; do execstack -q $i; execstack -c $i; done 
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so 
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2 
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude  ATI_LICENSE.TXT 
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start  --update-rcd-params="defaults 31" 
for i in \ 
            debian/xorg-driver-fglrx/usr/bin/atiode \ 
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \ 
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \ 
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \ 
            ; do execstack -q $i; execstack -c $i; done 
- debian/xorg-driver-fglrx/usr/bin/atiode 
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui 
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so 
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 
dh_installdocs -pxorg-driver-fglrx-dev 
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev 
dh_installinfo -pxorg-driver-fglrx-dev 
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev 
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev 
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev 
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev 
dh_link -pxorg-driver-fglrx-dev 
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source 
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source 
dh_installinfo -pfglrx-kernel-source 
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source 
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source 
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source 
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source 
dh_link -pfglrx-kernel-source 
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle 
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle 
dh_installinfo -pfglrx-amdcccle 
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle 
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle 
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle 
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle 
dh_link -pfglrx-amdcccle 
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/bin/amdcccle 
dh_installdocs -pfglrx-modaliases 
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases 
dh_installinfo -pfglrx-modaliases 
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases 
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases 
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases 
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases 
dh_link -pfglrx-modaliases 
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1 
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1 
dh_installinfo -plibamdxvba1 
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1 
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1 
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1 
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1 
dh_link -plibamdxvba1 
dh_installmime -plibamdxvba1 
dh_install -plibamdxvba1 "arch/x86/usr/X11R6/lib/libAMD*.so*"            "usr/lib32" 
dh_strip -pxorg-driver-fglrx 
dh_compress -pxorg-driver-fglrx 
dh_fixperms -pxorg-driver-fglrx 
dh_makeshlibs -pxorg-driver-fglrx 
dh_strip -pxorg-driver-fglrx-dev 
dh_compress -pxorg-driver-fglrx-dev 
dh_fixperms -pxorg-driver-fglrx-dev 
dh_makeshlibs -pxorg-driver-fglrx-dev 
dh_strip -pfglrx-kernel-source 
dh_compress -pfglrx-kernel-source 
dh_fixperms -pfglrx-kernel-source 
dh_makeshlibs -pfglrx-kernel-source 
dh_strip -pfglrx-amdcccle 
dh_compress -pfglrx-amdcccle 
dh_fixperms -pfglrx-amdcccle 
dh_makeshlibs -pfglrx-amdcccle 
dh_strip -pfglrx-modaliases 
dh_compress -pfglrx-modaliases 
dh_fixperms -pfglrx-modaliases 
dh_makeshlibs -pfglrx-modaliases 
dh_strip -plibamdxvba1 
dh_compress -plibamdxvba1 
dh_fixperms -plibamdxvba1 
dh_makeshlibs -plibamdxvba1 
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect 
 diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1.2 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect 
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa 
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd  contains an unresolvable reference to symbol XauFileName: it's probably  a plugin. 
dpkg-shlibdeps: warning: symbol XextCreateExtension used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol _XRead used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol XextAddDisplay used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol _XReply used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol _XFlush used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol XextFindDisplay used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: error: no dependency information found for  /usr/share/ati/lib64/libQtCore.so.4 (used by  debian/xorg-driver-fglrx/usr/sbin/amdnotifyui). 
dh_shlibdeps: dpkg-shlibdeps returned exit code 2 
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1 
dpkg-buildpackage: error: debian/rules binary gave error exit status 2 
dpkg-buildpackage: set CFLAGS to default value: -g -O2 
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions 
dpkg-buildpackage: set FFLAGS to default value: -g -O2 
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2 
dpkg-buildpackage: source package fglrx-installer 
dpkg-buildpackage: source version 2:8.690-0ubuntu1 
dpkg-buildpackage: source changed by ATI Technologies Inc.  [<http://ati.amd.com/support/driver.html>]("http://ati.amd.com/support/driver.html") 
 debian/rules build 
dpkg-buildpackage: host architecture amd64 
test -x debian/rules 
mkdir -p "." 
#Create important strings 
for i in 10fglrx \ 
             dkms.conf \ 
             xorg-driver-fglrx.install \ 
             xorg-driver-fglrx-dev.install \ 
             fglrx-kernel-source.install \ 
             fglrx-amdcccle.install \ 
             libamdxvba1.install \ 
             overrides/fglrx-kernel-source; do \ 
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \ 
            -e "s|#XMODDIR32#||" \ 
            -e "s|#DRIDIR32#|usr/lib32|"   \ 
            -e "s|#LIBDIR#|lib64|"       \ 
            -e "s|#DRIDIR#|usr/lib|"       \ 
            -e "s|#CVERSION#|8.690|"   \ 
            -e "s|#XARCH#|x740_64a|"   \ 
            -e "s|#ARCH#|x86_64|"   \ 
            debian/$i.in > debian/$i;      \ 
    done 
# remove exec bit on everything 
find arch \ 
        etc \ 
        lib \ 
        module \ 
        usr \ 
        x740_64a     -type f | xargs chmod -x 
find: `module': No such file or directory 
# set executable on user apps 
find arch/x86_64/usr/sbin \ 
        arch/x86_64/usr/X11R6/bin \ 
        usr/sbin/ -type f | xargs chmod a+x 
# set exec bit on scripts 
find lib etc debian -name "*.sh" -type f | xargs chmod +x 
# Generate modaliases 
sh -e debian/modaliases/fglrx_supported \ 
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \ 
        debian/modaliases/fglrx-modules.alias.override 
 debian/rules binary 
test -x debian/rules 
dh_testroot 
dh_clean -k 
dh_installdirs -A 
mkdir -p "." 
#Create important strings 
for i in 10fglrx \ 
             dkms.conf \ 
             xorg-driver-fglrx.install \ 
             xorg-driver-fglrx-dev.install \ 
             fglrx-kernel-source.install \ 
             fglrx-amdcccle.install \ 
             libamdxvba1.install \ 
             overrides/fglrx-kernel-source; do \ 
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \ 
            -e "s|#XMODDIR32#||" \ 
            -e "s|#DRIDIR32#|usr/lib32|"   \ 
            -e "s|#LIBDIR#|lib64|"       \ 
            -e "s|#DRIDIR#|usr/lib|"       \ 
            -e "s|#CVERSION#|8.690|"   \ 
            -e "s|#XARCH#|x740_64a|"   \ 
            -e "s|#ARCH#|x86_64|"   \ 
            debian/$i.in > debian/$i;      \ 
    done 
# remove exec bit on everything 
find arch \ 
        etc \ 
        lib \ 
        module \ 
        usr \ 
        x740_64a     -type f | xargs chmod -x 
find: `module': No such file or directory 
# set executable on user apps 
find arch/x86_64/usr/sbin \ 
        arch/x86_64/usr/X11R6/bin \ 
        usr/sbin/ -type f | xargs chmod a+x 
# set exec bit on scripts 
find lib etc debian -name "*.sh" -type f | xargs chmod +x 
# Generate modaliases 
sh -e debian/modaliases/fglrx_supported \ 
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \ 
        debian/modaliases/fglrx-modules.alias.override 
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx 
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx 
dh_installinfo -pxorg-driver-fglrx 
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx 
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx 
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx 
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx 
dh_link -pxorg-driver-fglrx 
dh_installmime -pxorg-driver-fglrx 
#driver package 
dh_install -XlibAMD -pxorg-driver-fglrx  "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32" 
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"      "usr/lib32" 
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                      "usr/lib32" 
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx" 
for i in \ 
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \ 
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \ 
            ; do execstack -q $i; execstack -c $i; done 
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so 
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2 
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude  ATI_LICENSE.TXT 
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start  --update-rcd-params="defaults 31" 
for i in \ 
            debian/xorg-driver-fglrx/usr/bin/atiode \ 
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \ 
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \ 
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \ 
            ; do execstack -q $i; execstack -c $i; done 
- debian/xorg-driver-fglrx/usr/bin/atiode 
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui 
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so 
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 
dh_installdocs -pxorg-driver-fglrx-dev 
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev 
dh_installinfo -pxorg-driver-fglrx-dev 
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev 
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev 
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev 
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev 
dh_link -pxorg-driver-fglrx-dev 
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source 
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source 
dh_installinfo -pfglrx-kernel-source 
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source 
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source 
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source 
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source 
dh_link -pfglrx-kernel-source 
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle 
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle 
dh_installinfo -pfglrx-amdcccle 
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle 
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle 
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle 
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle 
dh_link -pfglrx-amdcccle 
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/bin/amdcccle 
dh_installdocs -pfglrx-modaliases 
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases 
dh_installinfo -pfglrx-modaliases 
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases 
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases 
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases 
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases 
dh_link -pfglrx-modaliases 
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1 
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1 
dh_installinfo -plibamdxvba1 
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1 
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1 
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1 
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1 
dh_link -plibamdxvba1 
dh_installmime -plibamdxvba1 
dh_install -plibamdxvba1 "arch/x86/usr/X11R6/lib/libAMD*.so*"            "usr/lib32" 
dh_strip -pxorg-driver-fglrx 
dh_compress -pxorg-driver-fglrx 
dh_fixperms -pxorg-driver-fglrx 
dh_makeshlibs -pxorg-driver-fglrx 
dh_strip -pxorg-driver-fglrx-dev 
dh_compress -pxorg-driver-fglrx-dev 
dh_fixperms -pxorg-driver-fglrx-dev 
dh_makeshlibs -pxorg-driver-fglrx-dev 
dh_strip -pfglrx-kernel-source 
dh_compress -pfglrx-kernel-source 
dh_fixperms -pfglrx-kernel-source 
dh_makeshlibs -pfglrx-kernel-source 
dh_strip -pfglrx-amdcccle 
dh_compress -pfglrx-amdcccle 
dh_fixperms -pfglrx-amdcccle 
dh_makeshlibs -pfglrx-amdcccle 
dh_strip -pfglrx-modaliases 
dh_compress -pfglrx-modaliases 
dh_fixperms -pfglrx-modaliases 
dh_makeshlibs -pfglrx-modaliases 
dh_strip -plibamdxvba1 
dh_compress -plibamdxvba1 
dh_fixperms -plibamdxvba1 
dh_makeshlibs -plibamdxvba1 
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect 
 diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1.2 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect 
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa 
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd  contains an unresolvable reference to symbol XauFileName: it's probably  a plugin. 
dpkg-shlibdeps: warning: symbol XextCreateExtension used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol _XRead used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol XextAddDisplay used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol _XReply used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol _XFlush used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol XextFindDisplay used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: error: no dependency information found for  /usr/share/ati/lib64/libQtCore.so.4 (used by  debian/xorg-driver-fglrx/usr/sbin/amdnotifyui). 
dh_shlibdeps: dpkg-shlibdeps returned exit code 2 
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1 
dpkg-buildpackage: error: debian/rules binary gave error exit status 2 
dpkg-buildpackage: set CFLAGS to default value: -g -O2 
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions 
dpkg-buildpackage: set FFLAGS to default value: -g -O2 
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2 
dpkg-buildpackage: source package fglrx-installer 
dpkg-buildpackage: source version 2:8.690-0ubuntu1 
dpkg-buildpackage: source changed by ATI Technologies Inc.  [<http://ati.amd.com/support/driver.html>]("http://ati.amd.com/support/driver.html") 
 debian/rules build 
dpkg-buildpackage: host architecture amd64 
test -x debian/rules 
mkdir -p "." 
#Create important strings 
for i in 10fglrx \ 
             dkms.conf \ 
             xorg-driver-fglrx.install \ 
             xorg-driver-fglrx-dev.install \ 
             fglrx-kernel-source.install \ 
             fglrx-amdcccle.install \ 
             libamdxvba1.install \ 
             overrides/fglrx-kernel-source; do \ 
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \ 
            -e "s|#XMODDIR32#||" \ 
            -e "s|#DRIDIR32#|usr/lib32|"   \ 
            -e "s|#LIBDIR#|lib64|"       \ 
            -e "s|#DRIDIR#|usr/lib|"       \ 
            -e "s|#CVERSION#|8.690|"   \ 
            -e "s|#XARCH#|x740_64a|"   \ 
            -e "s|#ARCH#|x86_64|"   \ 
            debian/$i.in > debian/$i;      \ 
    done 
# remove exec bit on everything 
find arch \ 
        etc \ 
        lib \ 
        module \ 
        usr \ 
        x740_64a     -type f | xargs chmod -x 
find: `module': No such file or directory 
# set executable on user apps 
find arch/x86_64/usr/sbin \ 
        arch/x86_64/usr/X11R6/bin \ 
        usr/sbin/ -type f | xargs chmod a+x 
# set exec bit on scripts 
find lib etc debian -name "*.sh" -type f | xargs chmod +x 
# Generate modaliases 
sh -e debian/modaliases/fglrx_supported \ 
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \ 
        debian/modaliases/fglrx-modules.alias.override 
 debian/rules binary 
test -x debian/rules 
dh_testroot 
dh_clean -k 
dh_installdirs -A 
mkdir -p "." 
#Create important strings 
for i in 10fglrx \ 
             dkms.conf \ 
             xorg-driver-fglrx.install \ 
             xorg-driver-fglrx-dev.install \ 
             fglrx-kernel-source.install \ 
             fglrx-amdcccle.install \ 
             libamdxvba1.install \ 
             overrides/fglrx-kernel-source; do \ 
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \ 
            -e "s|#XMODDIR32#||" \ 
            -e "s|#DRIDIR32#|usr/lib32|"   \ 
            -e "s|#LIBDIR#|lib64|"       \ 
            -e "s|#DRIDIR#|usr/lib|"       \ 
            -e "s|#CVERSION#|8.690|"   \ 
            -e "s|#XARCH#|x740_64a|"   \ 
            -e "s|#ARCH#|x86_64|"   \ 
            debian/$i.in > debian/$i;      \ 
    done 
# remove exec bit on everything 
find arch \ 
        etc \ 
        lib \ 
        module \ 
        usr \ 
        x740_64a     -type f | xargs chmod -x 
find: `module': No such file or directory 
# set executable on user apps 
find arch/x86_64/usr/sbin \ 
        arch/x86_64/usr/X11R6/bin \ 
        usr/sbin/ -type f | xargs chmod a+x 
# set exec bit on scripts 
find lib etc debian -name "*.sh" -type f | xargs chmod +x 
# Generate modaliases 
sh -e debian/modaliases/fglrx_supported \ 
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \ 
        debian/modaliases/fglrx-modules.alias.override 
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx 
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx 
dh_installinfo -pxorg-driver-fglrx 
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx 
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx 
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx 
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx 
dh_link -pxorg-driver-fglrx 
dh_installmime -pxorg-driver-fglrx 
#driver package 
dh_install -XlibAMD -pxorg-driver-fglrx  "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32" 
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"      "usr/lib32" 
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                      "usr/lib32" 
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx" 
for i in \ 
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \ 
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \ 
            ; do execstack -q $i; execstack -c $i; done 
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so 
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2 
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude  ATI_LICENSE.TXT 
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start  --update-rcd-params="defaults 31" 
for i in \ 
            debian/xorg-driver-fglrx/usr/bin/atiode \ 
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \ 
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \ 
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \ 
            ; do execstack -q $i; execstack -c $i; done 
- debian/xorg-driver-fglrx/usr/bin/atiode 
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui 
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so 
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 
dh_installdocs -pxorg-driver-fglrx-dev 
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev 
dh_installinfo -pxorg-driver-fglrx-dev 
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev 
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev 
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev 
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev 
dh_link -pxorg-driver-fglrx-dev 
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source 
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source 
dh_installinfo -pfglrx-kernel-source 
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source 
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source 
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source 
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source 
dh_link -pfglrx-kernel-source 
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle 
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle 
dh_installinfo -pfglrx-amdcccle 
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle 
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle 
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle 
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle 
dh_link -pfglrx-amdcccle 
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/bin/amdcccle 
dh_installdocs -pfglrx-modaliases 
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases 
dh_installinfo -pfglrx-modaliases 
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases 
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases 
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases 
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases 
dh_link -pfglrx-modaliases 
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1 
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1 
dh_installinfo -plibamdxvba1 
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1 
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1 
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1 
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1 
dh_link -plibamdxvba1 
dh_installmime -plibamdxvba1 
dh_install -plibamdxvba1 "arch/x86/usr/X11R6/lib/libAMD*.so*"            "usr/lib32" 
dh_strip -pxorg-driver-fglrx 
dh_compress -pxorg-driver-fglrx 
dh_fixperms -pxorg-driver-fglrx 
dh_makeshlibs -pxorg-driver-fglrx 
dh_strip -pxorg-driver-fglrx-dev 
dh_compress -pxorg-driver-fglrx-dev 
dh_fixperms -pxorg-driver-fglrx-dev 
dh_makeshlibs -pxorg-driver-fglrx-dev 
dh_strip -pfglrx-kernel-source 
dh_compress -pfglrx-kernel-source 
dh_fixperms -pfglrx-kernel-source 
dh_makeshlibs -pfglrx-kernel-source 
dh_strip -pfglrx-amdcccle 
dh_compress -pfglrx-amdcccle 
dh_fixperms -pfglrx-amdcccle 
dh_makeshlibs -pfglrx-amdcccle 
dh_strip -pfglrx-modaliases 
dh_compress -pfglrx-modaliases 
dh_fixperms -pfglrx-modaliases 
dh_makeshlibs -pfglrx-modaliases 
dh_strip -plibamdxvba1 
dh_compress -plibamdxvba1 
dh_fixperms -plibamdxvba1 
dh_makeshlibs -plibamdxvba1 
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect 
 diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1.2 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect 
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa 
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd  contains an unresolvable reference to symbol XauFileName: it's probably  a plugin. 
dpkg-shlibdeps: warning: symbol XextCreateExtension used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol _XRead used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol XextAddDisplay used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol _XReply used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol _XFlush used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: warning: symbol XextFindDisplay used by  debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the  libraries. 
dpkg-shlibdeps: error: no dependency information found for  /usr/share/ati/lib64/libQtCore.so.4 (used by  debian/xorg-driver-fglrx/usr/sbin/amdnotifyui). 
dh_shlibdeps: dpkg-shlibdeps returned exit code 2 
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1 
dpkg-buildpackage: error: debian/rules binary gave error exit status 2 
Removing temporary directory: fglrx-install.4SQjaE 

[/FONT]

```

---

### Post by ptrxyz on 2010-02-04
Got the same problem...does anyone know whats that about and how to solve it?
Thanks in advance...

---

### Post by a-user on 2010-02-04
i could solve it by deleting (moving) the directory /usr/share/ati/lib64

after that i could build the packages again. note, there is still a bug in the current 10.1 release. within the packages there is a missing link (look on phoronix forum) that you must manually add to be able to compile them.

---

### Post by elect on 2010-02-13
> **a-user said:**
> i could solve it by deleting (moving) the directory /usr/share/ati/lib64


I love u :p

---

### Post by Ain Soph on 2010-05-08
the automatic instalation non generate deb package, and we want generate the deb package

anybody know how solve this problem?

---

### Post by kagy on 2010-05-08
> **Ain Soph said:**
> the automatic instalation non generate deb package, and we want generate the deb package

anybody know how solve this problem?

sudo sh ./ati-driver-installer-10-3-x86.x86_64.run --buildpkg Ubuntu/lucid

---

### Post by Ain Soph on 2010-05-08
Think kagy, but occur same problem, "dpkg-buildpackage: error: debian/rules binary gave error exit status 2"
the full log

```

Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.723....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
[31m ATI Technologies Linux Driver Installer/Packager [0m
==================================================
Generating package: Ubuntu/lucid
Package build failed!
Package build utility output:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.702-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.702|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
        debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.702|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
        debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#driver package
dh_install -XlibAMD -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                     "usr/lib32"
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx"
for i in \
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
            debian/xorg-driver-fglrx/usr/bin/atiode \
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/bin/amdcccle
dh_installdocs -pfglrx-modaliases   
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases  
dh_installinfo -pfglrx-modaliases  
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases   
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases   
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases   
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases  
dh_link -pfglrx-modaliases  
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1   
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1  
dh_installinfo -plibamdxvba1  
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1   
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1   
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1   
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1  
dh_link -plibamdxvba1  
dh_installmime -plibamdxvba1 
dh_install -plibamdxvba1 "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32"
dh_strip -pxorg-driver-fglrx  
dh_compress -pxorg-driver-fglrx  
dh_fixperms -pxorg-driver-fglrx  
dh_makeshlibs -pxorg-driver-fglrx  
dh_strip -pxorg-driver-fglrx-dev  
dh_compress -pxorg-driver-fglrx-dev  
dh_fixperms -pxorg-driver-fglrx-dev  
dh_makeshlibs -pxorg-driver-fglrx-dev  
dh_strip -pfglrx-kernel-source  
dh_compress -pfglrx-kernel-source  
dh_fixperms -pfglrx-kernel-source  
dh_makeshlibs -pfglrx-kernel-source  
dh_strip -pfglrx-amdcccle  
dh_compress -pfglrx-amdcccle  
dh_fixperms -pfglrx-amdcccle  
dh_makeshlibs -pfglrx-amdcccle  
dh_strip -pfglrx-modaliases  
dh_compress -pfglrx-modaliases  
dh_fixperms -pfglrx-modaliases  
dh_makeshlibs -pfglrx-modaliases  
dh_strip -plibamdxvba1  
dh_compress -plibamdxvba1  
dh_fixperms -plibamdxvba1  
dh_makeshlibs -plibamdxvba1  
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#driver package
dh_install -XlibAMD -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                     "usr/lib32"
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx"
for i in \
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
            debian/xorg-driver-fglrx/usr/bin/atiode \
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.702-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.702|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
        debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.702|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
        debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#driver package
dh_install -XlibAMD -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                     "usr/lib32"
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx"
for i in \
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
            debian/xorg-driver-fglrx/usr/bin/atiode \
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/bin/amdcccle
dh_installdocs -pfglrx-modaliases   
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases  
dh_installinfo -pfglrx-modaliases  
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases   
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases   
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases   
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases  
dh_link -pfglrx-modaliases  
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1   
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1  
dh_installinfo -plibamdxvba1  
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1   
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1   
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1   
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1  
dh_link -plibamdxvba1  
dh_installmime -plibamdxvba1 
dh_install -plibamdxvba1 "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32"
dh_strip -pxorg-driver-fglrx  
dh_compress -pxorg-driver-fglrx  
dh_fixperms -pxorg-driver-fglrx  
dh_makeshlibs -pxorg-driver-fglrx  
dh_strip -pxorg-driver-fglrx-dev  
dh_compress -pxorg-driver-fglrx-dev  
dh_fixperms -pxorg-driver-fglrx-dev  
dh_makeshlibs -pxorg-driver-fglrx-dev  
dh_strip -pfglrx-kernel-source  
dh_compress -pfglrx-kernel-source  
dh_fixperms -pfglrx-kernel-source  
dh_makeshlibs -pfglrx-kernel-source  
dh_strip -pfglrx-amdcccle  
dh_compress -pfglrx-amdcccle  
dh_fixperms -pfglrx-amdcccle  
dh_makeshlibs -pfglrx-amdcccle  
dh_strip -pfglrx-modaliases  
dh_compress -pfglrx-modaliases  
dh_fixperms -pfglrx-modaliases  
dh_makeshlibs -pfglrx-modaliases  
dh_strip -plibamdxvba1  
dh_compress -plibamdxvba1  
dh_fixperms -plibamdxvba1  
dh_makeshlibs -plibamdxvba1  
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#driver package
dh_install -XlibAMD -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                     "usr/lib32"
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx"
for i in \
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
            debian/xorg-driver-fglrx/usr/bin/atiode \
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
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
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib/fglrx|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x750_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x750_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
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
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*"                     "usr/lib32/fglrx"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
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
- debian/fglrx/usr/lib/fglrx/libGL.so.1
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.hvKuMY/debian/fglrx/usr/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.hvKuMY/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.hvKuMY/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary
   dh_testroot -Nfglrx -Nfglrx-amdcccle
   dh_prep -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -Nfglrx -Nfglrx-amdcccle
   dh_install -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -Nfglrx
   dh_installchangelogs
   dh_installexamples
   dh_installman
   dh_installcatalogs
   dh_installcron
   dh_installdebconf
   dh_installcatalogs
   dh_installemacsen
   dh_installifupdown
   dh_installinfo
   dh_installinit -Nfglrx
   dh_installmenu
   dh_installmime
   dh_installmodules
   dh_installlogcheck
   dh_installlogrotate
   dh_installpam
   dh_installppp
   dh_installudev
   dh_installwm
   dh_installxfonts
   dh_bugfiles
   dh_lintian
   dh_gconf
   dh_icons
   dh_perl
   dh_pysupport
   dh_usrlocal
   dh_link -Nfglrx
   dh_compress
   dh_fixperms
   dh_strip
   dh_makeshlibs
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.hvKuMY'
dh_shlibdeps -l/tmp/fglrx.hvKuMY/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.hvKuMY/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XGetGeometry: it's probably a plugin.
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 contains an unresolvable reference to symbol XextCreateExtension: it's probably a plugin.
dpkg-shlibdeps: warning: 5 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 1
make[1]: Leaving directory `/tmp/fglrx.hvKuMY'
make: *** [binary] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
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
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib/fglrx|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x750_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x750_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
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
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*"                     "usr/lib32/fglrx"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
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
- debian/fglrx/usr/lib/fglrx/libGL.so.1
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.oybJFM/debian/fglrx/usr/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.oybJFM/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.oybJFM/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary
   dh_testroot -Nfglrx -Nfglrx-amdcccle
   dh_prep -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -Nfglrx -Nfglrx-amdcccle
   dh_install -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -Nfglrx
   dh_installchangelogs
   dh_installexamples
   dh_installman
   dh_installcatalogs
   dh_installcron
   dh_installdebconf
   dh_installcatalogs
   dh_installemacsen
   dh_installifupdown
   dh_installinfo
   dh_installinit -Nfglrx
   dh_installmenu
   dh_installmime
   dh_installmodules
   dh_installlogcheck
   dh_installlogrotate
   dh_installpam
   dh_installppp
   dh_installudev
   dh_installwm
   dh_installxfonts
   dh_bugfiles
   dh_lintian
   dh_gconf
   dh_icons
   dh_perl
   dh_pysupport
   dh_usrlocal
   dh_link -Nfglrx
   dh_compress
   dh_fixperms
   dh_strip
   dh_makeshlibs
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.oybJFM'
dh_shlibdeps -l/tmp/fglrx.oybJFM/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.oybJFM/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XGetGeometry: it's probably a plugin.
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 contains an unresolvable reference to symbol XextCreateExtension: it's probably a plugin.
dpkg-shlibdeps: warning: 5 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 1
make[1]: Leaving directory `/tmp/fglrx.oybJFM'
make: *** [binary] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
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
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib/fglrx|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x750_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x750_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
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
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*"                     "usr/lib32/fglrx"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
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
- debian/fglrx/usr/lib/fglrx/libGL.so.1
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.qbOhCG/debian/fglrx/usr/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.qbOhCG/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.qbOhCG/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary
   dh_testroot -Nfglrx -Nfglrx-amdcccle
   dh_prep -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -Nfglrx -Nfglrx-amdcccle
   dh_install -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -Nfglrx
   dh_installchangelogs
   dh_installexamples
   dh_installman
   dh_installcatalogs
   dh_installcron
   dh_installdebconf
   dh_installcatalogs
   dh_installemacsen
   dh_installifupdown
   dh_installinfo
   dh_installinit -Nfglrx
   dh_installmenu
   dh_installmime
   dh_installmodules
   dh_installlogcheck
   dh_installlogrotate
   dh_installpam
   dh_installppp
   dh_installudev
   dh_installwm
   dh_installxfonts
   dh_bugfiles
   dh_lintian
   dh_gconf
   dh_icons
   dh_perl
   dh_pysupport
   dh_usrlocal
   dh_link -Nfglrx
   dh_compress
   dh_fixperms
   dh_strip
   dh_makeshlibs
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.qbOhCG'
dh_shlibdeps -l/tmp/fglrx.qbOhCG/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.qbOhCG/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XGetGeometry: it's probably a plugin.
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 contains an unresolvable reference to symbol XextCreateExtension: it's probably a plugin.
dpkg-shlibdeps: warning: 5 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 1
make[1]: Leaving directory `/tmp/fglrx.qbOhCG'
make: *** [binary] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.juMSxu

```

anyone have another idea?

---

### Post by progre55_icky on 2010-05-31
> **Ain Soph said:**
> Think kagy, but occur same problem, "dpkg-buildpackage: error: debian/rules binary gave error exit status 2"
the full log

```

Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.723....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
[31m ATI Technologies Linux Driver Installer/Packager [0m
==================================================
Generating package: Ubuntu/lucid
Package build failed!
Package build utility output:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.702-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.702|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
        debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.702|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
        debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#driver package
dh_install -XlibAMD -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                     "usr/lib32"
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx"
for i in \
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
            debian/xorg-driver-fglrx/usr/bin/atiode \
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/bin/amdcccle
dh_installdocs -pfglrx-modaliases   
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases  
dh_installinfo -pfglrx-modaliases  
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases   
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases   
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases   
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases  
dh_link -pfglrx-modaliases  
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1   
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1  
dh_installinfo -plibamdxvba1  
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1   
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1   
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1   
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1  
dh_link -plibamdxvba1  
dh_installmime -plibamdxvba1 
dh_install -plibamdxvba1 "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32"
dh_strip -pxorg-driver-fglrx  
dh_compress -pxorg-driver-fglrx  
dh_fixperms -pxorg-driver-fglrx  
dh_makeshlibs -pxorg-driver-fglrx  
dh_strip -pxorg-driver-fglrx-dev  
dh_compress -pxorg-driver-fglrx-dev  
dh_fixperms -pxorg-driver-fglrx-dev  
dh_makeshlibs -pxorg-driver-fglrx-dev  
dh_strip -pfglrx-kernel-source  
dh_compress -pfglrx-kernel-source  
dh_fixperms -pfglrx-kernel-source  
dh_makeshlibs -pfglrx-kernel-source  
dh_strip -pfglrx-amdcccle  
dh_compress -pfglrx-amdcccle  
dh_fixperms -pfglrx-amdcccle  
dh_makeshlibs -pfglrx-amdcccle  
dh_strip -pfglrx-modaliases  
dh_compress -pfglrx-modaliases  
dh_fixperms -pfglrx-modaliases  
dh_makeshlibs -pfglrx-modaliases  
dh_strip -plibamdxvba1  
dh_compress -plibamdxvba1  
dh_fixperms -plibamdxvba1  
dh_makeshlibs -plibamdxvba1  
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#driver package
dh_install -XlibAMD -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                     "usr/lib32"
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx"
for i in \
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
            debian/xorg-driver-fglrx/usr/bin/atiode \
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.702-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.702|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
        debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.702|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
        debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#driver package
dh_install -XlibAMD -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                     "usr/lib32"
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx"
for i in \
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
            debian/xorg-driver-fglrx/usr/bin/atiode \
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/bin/amdcccle
dh_installdocs -pfglrx-modaliases   
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases  
dh_installinfo -pfglrx-modaliases  
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases   
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases   
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases   
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases  
dh_link -pfglrx-modaliases  
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1   
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1  
dh_installinfo -plibamdxvba1  
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1   
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1   
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1   
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1  
dh_link -plibamdxvba1  
dh_installmime -plibamdxvba1 
dh_install -plibamdxvba1 "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32"
dh_strip -pxorg-driver-fglrx  
dh_compress -pxorg-driver-fglrx  
dh_fixperms -pxorg-driver-fglrx  
dh_makeshlibs -pxorg-driver-fglrx  
dh_strip -pxorg-driver-fglrx-dev  
dh_compress -pxorg-driver-fglrx-dev  
dh_fixperms -pxorg-driver-fglrx-dev  
dh_makeshlibs -pxorg-driver-fglrx-dev  
dh_strip -pfglrx-kernel-source  
dh_compress -pfglrx-kernel-source  
dh_fixperms -pfglrx-kernel-source  
dh_makeshlibs -pfglrx-kernel-source  
dh_strip -pfglrx-amdcccle  
dh_compress -pfglrx-amdcccle  
dh_fixperms -pfglrx-amdcccle  
dh_makeshlibs -pfglrx-amdcccle  
dh_strip -pfglrx-modaliases  
dh_compress -pfglrx-modaliases  
dh_fixperms -pfglrx-modaliases  
dh_makeshlibs -pfglrx-modaliases  
dh_strip -plibamdxvba1  
dh_compress -plibamdxvba1  
dh_fixperms -plibamdxvba1  
dh_makeshlibs -plibamdxvba1  
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
             dkms.conf \
             xorg-driver-fglrx.install \
             xorg-driver-fglrx-dev.install \
             fglrx-kernel-source.install \
             fglrx-amdcccle.install \
             libamdxvba1.install \
             overrides/fglrx-kernel-source; do \
        sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#driver package
dh_install -XlibAMD -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                     "usr/lib32"
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx"
for i in \
            debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
            debian/xorg-driver-fglrx/usr/bin/atiode \
            debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
            debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
            debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
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
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib/fglrx|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x750_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x750_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
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
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*"                     "usr/lib32/fglrx"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
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
- debian/fglrx/usr/lib/fglrx/libGL.so.1
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.hvKuMY/debian/fglrx/usr/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.hvKuMY/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.hvKuMY/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary
   dh_testroot -Nfglrx -Nfglrx-amdcccle
   dh_prep -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -Nfglrx -Nfglrx-amdcccle
   dh_install -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -Nfglrx
   dh_installchangelogs
   dh_installexamples
   dh_installman
   dh_installcatalogs
   dh_installcron
   dh_installdebconf
   dh_installcatalogs
   dh_installemacsen
   dh_installifupdown
   dh_installinfo
   dh_installinit -Nfglrx
   dh_installmenu
   dh_installmime
   dh_installmodules
   dh_installlogcheck
   dh_installlogrotate
   dh_installpam
   dh_installppp
   dh_installudev
   dh_installwm
   dh_installxfonts
   dh_bugfiles
   dh_lintian
   dh_gconf
   dh_icons
   dh_perl
   dh_pysupport
   dh_usrlocal
   dh_link -Nfglrx
   dh_compress
   dh_fixperms
   dh_strip
   dh_makeshlibs
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.hvKuMY'
dh_shlibdeps -l/tmp/fglrx.hvKuMY/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.hvKuMY/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XGetGeometry: it's probably a plugin.
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 contains an unresolvable reference to symbol XextCreateExtension: it's probably a plugin.
dpkg-shlibdeps: warning: 5 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 1
make[1]: Leaving directory `/tmp/fglrx.hvKuMY'
make: *** [binary] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
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
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib/fglrx|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x750_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x750_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
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
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*"                     "usr/lib32/fglrx"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
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
- debian/fglrx/usr/lib/fglrx/libGL.so.1
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.oybJFM/debian/fglrx/usr/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.oybJFM/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.oybJFM/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary
   dh_testroot -Nfglrx -Nfglrx-amdcccle
   dh_prep -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -Nfglrx -Nfglrx-amdcccle
   dh_install -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -Nfglrx
   dh_installchangelogs
   dh_installexamples
   dh_installman
   dh_installcatalogs
   dh_installcron
   dh_installdebconf
   dh_installcatalogs
   dh_installemacsen
   dh_installifupdown
   dh_installinfo
   dh_installinit -Nfglrx
   dh_installmenu
   dh_installmime
   dh_installmodules
   dh_installlogcheck
   dh_installlogrotate
   dh_installpam
   dh_installppp
   dh_installudev
   dh_installwm
   dh_installxfonts
   dh_bugfiles
   dh_lintian
   dh_gconf
   dh_icons
   dh_perl
   dh_pysupport
   dh_usrlocal
   dh_link -Nfglrx
   dh_compress
   dh_fixperms
   dh_strip
   dh_makeshlibs
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.oybJFM'
dh_shlibdeps -l/tmp/fglrx.oybJFM/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.oybJFM/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XGetGeometry: it's probably a plugin.
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 contains an unresolvable reference to symbol XextCreateExtension: it's probably a plugin.
dpkg-shlibdeps: warning: 5 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 1
make[1]: Leaving directory `/tmp/fglrx.oybJFM'
make: *** [binary] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
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
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib/fglrx|"       \
            -e "s|#CVERSION#|8.723|"   \
            -e "s|#XARCH#|x750_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x750_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
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
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*"                     "usr/lib32/fglrx"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
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
- debian/fglrx/usr/lib/fglrx/libGL.so.1
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.qbOhCG/debian/fglrx/usr/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.qbOhCG/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.qbOhCG/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary
   dh_testroot -Nfglrx -Nfglrx-amdcccle
   dh_prep -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -Nfglrx -Nfglrx-amdcccle
   dh_install -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -Nfglrx
   dh_installchangelogs
   dh_installexamples
   dh_installman
   dh_installcatalogs
   dh_installcron
   dh_installdebconf
   dh_installcatalogs
   dh_installemacsen
   dh_installifupdown
   dh_installinfo
   dh_installinit -Nfglrx
   dh_installmenu
   dh_installmime
   dh_installmodules
   dh_installlogcheck
   dh_installlogrotate
   dh_installpam
   dh_installppp
   dh_installudev
   dh_installwm
   dh_installxfonts
   dh_bugfiles
   dh_lintian
   dh_gconf
   dh_icons
   dh_perl
   dh_pysupport
   dh_usrlocal
   dh_link -Nfglrx
   dh_compress
   dh_fixperms
   dh_strip
   dh_makeshlibs
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.qbOhCG'
dh_shlibdeps -l/tmp/fglrx.qbOhCG/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.qbOhCG/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XGetGeometry: it's probably a plugin.
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 contains an unresolvable reference to symbol XextCreateExtension: it's probably a plugin.
dpkg-shlibdeps: warning: 5 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 1
make[1]: Leaving directory `/tmp/fglrx.qbOhCG'
make: *** [binary] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.juMSxu

```anyone have another idea?
 
as it was said by a-user, just moving /usr/share/ati/lib64 into some other location (or deleting) helped me. I was getting the very same  error.

---

### Post by surrealillusions on 2010-06-14
Hi,

Sorry to drag this topic from the depths of 2 weeks ago...but this is giving me problems.

I ran the command line after installing the ATI drivers from the website. Same error as that bunch of error code stuff.

Theres a lib folder under ati, but not a lib64. And that lib folder I cant move, rename or delete, despite trying to change the permissions via sudo chmod commands.

Any advice on what to do?

---

### Post by Ain Soph on 2010-06-26
> **surrealillusions said:**
> Hi,

Sorry to drag this topic from the depths of 2 weeks ago...but this is giving me problems.

I ran the command line after installing the ATI drivers from the website. Same error as that bunch of error code stuff.

Theres a lib folder under ati, but not a lib64. And that lib folder I cant move, rename or delete, despite trying to change the permissions via sudo chmod commands.

Any advice on what to do?

I no have idea...

---

### Post by a-user on 2010-06-28
how did you tried to remove this directory?
did you used root rights by using e.g. "sudo rm -rf [directoryname]" ? (replace [directoryname] with the path of the directory to delete)

---

