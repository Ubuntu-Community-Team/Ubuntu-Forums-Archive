---
title: "another failed upgrade"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by BcRich on 2011-12-04
Hi 
I was in the process of installing important security upgrades and recommended upgrades
through update manager, which managed to get partially through the upgrade. as there were a lot of files to download i let it run while i went off and did something else. when i got back to my computer update manager was displaying an error stating that several packages failed to update however everything did manage to download.
so i closed update manager and ran
sudo apt-get install -f
because i had broken packages. the command ran without any errors. so i rebooted ubuntu as update manager said i needed to reboot ubuntu in order for the update process to complete.
however when i rebooted ubuntu started up as usual it took me to the command prompt to enter my user name and password (not @the ubuntu login screen yet). then i try 
sudo gdm
and nothing happens
usually at that point i would get taken to the ubuntu gdm login screen but my computer just hangs at that point.
ubuntu 10.10

---

### Post by dabl on 2011-12-04
```
sudo service gdm stop
```

```
sudo service gdm start
```

:confused:

---

### Post by Rubi1200 on 2011-12-04
Hi,
you upgraded from what to what?

Please post the specifications, especially RAM and graphics card.

Thanks.

---

### Post by BcRich on 2011-12-05
> **Rubi1200 said:**
> Hi,
you upgraded from what to what?

Please post the specifications, especially RAM and graphics card.

Thanks.
hi Rubi1200
sorry for lack of info,
i wasn't upgrading the entire ubuntu version for example I use 10.10 and upgrade manager recomends I upgrade to 11.04. That's not what I was doing. Upgrade manager also has a section that allows you to stay on the current version of ubuntu that you r using (in my case 10.10) but to update the security fixes and installed recommended updates (i guess for the purposes of creating a more stable system), that is what I was doing. The problem started when I tried to install an app from kxstudio called klaudia, which messed up my sound configuration. So i thought that maybe the fact that some of the stuff I was using was out of date. Which is why I did the whole update manager thing. I hope that makes more sense? i use ubuntu studio x64 10.10, with 8bg ram, amd 1075t cpu, amd 6850 gpu, with two WD hdd's one which is for ubuntu 10.10 the other which is for ubuntu 9.04 (but that installation doesn't have a woring internet connection any more). what i'd like is just to get my old version 10.10 x64 working back to the way that it was before it broke? i have a live cd which i can use to start my computer up and hopefully provide u with any more information u may need. thanks a billion

---

### Post by BcRich on 2011-12-05
Hi 
so after check out this post [http://ubuntuforums.org/showthread.php?t=1890056](http://ubuntuforums.org/showthread.php?t=1890056) i was able to confirm that it is an issue with my graphics card driver similar to the mentioned post. I'm using (or rather was using) catalyst 11.7 which used to work fine but obviously something went wrong with during the update manager problem. I was able to boot into failsafex mode and everything on my computer seems to be perfectly fine except that my video drivers are not working. 
however i can't uninstall my previous drivers and as a result cannot reinstall the current drivers (11.7) or install the new catalyst drivers 11.11
i keep getting told that i need to uninstall my old drivers first, so I go through the removal steps here [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)
and they seem to work but then i run 
```
sudo sh ./ati-driver-installer-11-11-x86.x86_64.run --buildpkg Ubuntu/maverick
```

i get this error. NB the guide is for oneric so i had to change the previous command to end with maverick, which is what i'm using

```
Created directory fglrx-install.jzxkn3
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.911...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/maverick
Resolving build dependencies...
Continuing package build
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 396: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.872-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.kTM7gp
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 fglrx.install \
			 fglrx-dev.install \
			 fglrx-amdcccle.install \
			 overrides/fglrx; do \
		sed -e "s|#XMODDIR#|usr/lib/fglrx/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#PXPRESSXMODDIR#|usr/lib/pxpress/xorg/modules|" \
			-e "s|#DRIDIR32#|usr/lib32/fglrx|"   \
			-e "s|#LIBDIR#|lib64|"       \
			-e "s|#DRIDIR#|usr/lib/fglrx|"       \
			-e "s|#PXPRESSDIR#|usr/lib/pxpress|" \
			-e "s|#PXPRESSLIBDIR#|usr/lib/pxpress/lib|" \
			-e "s|#PXPRESSLIBDIR32#|usr/lib32/pxpress/lib|" \
			-e "s|#CVERSION#|8.872|"   \
			-e "s|#XARCH#|xpic_64a|"   \
			-e "s|#ARCH#|x86_64|"   \
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
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 debian/rules binary
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
for i in \
			debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
			debian/fglrx/usr/lib32/fglrx/*libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
/bin/sh: execstack: not found
/bin/sh: execstack: not found
/bin/sh: execstack: not found
/bin/sh: execstack: not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
./packages/Ubuntu/ati-packager.sh: 399: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.911-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.okBrYb
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
			-e "s|#XORGEXTRA#|usr/lib/xorg/extra-modules|g" \
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
			-e "s|#CVERSION#|8.911|g" \
			-e "s|#SRCXARCH#|xpic_64a|g" \
			-e "s|#SRCARCH#|x86_64|g" \
			-e "s|#SRCLIBDIR#|lib64|g" \
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
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h fglrx fglrx > \
		debian/modaliases/fglrx-modules.alias.override
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
for i in \
			debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
			debian/fglrx/usr/lib32/fglrx/*libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/fglrx-libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude LICENSE.TXT
dh_installdocs -pfglrx debian/AUTHORS
dh_installdocs -pfglrx debian/copyright
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
Duplicate specification "O=s" for option "O"
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
printf "blacklist radeon\n" > /tmp/fglrx.okBrYb/debian/fglrx/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >	"/tmp/fglrx.okBrYb/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>	"/tmp/fglrx.okBrYb/debian/fglrx/usr/lib/fglrx/ld.so.conf"
# ld.so.conf for PowerXpress
echo "/usr/lib/mesa" >		"/tmp/fglrx.okBrYb/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib/pxpress/lib" >>	"/tmp/fglrx.okBrYb/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib32/mesa" >>	"/tmp/fglrx.okBrYb/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib32/pxpress/lib" >>	"/tmp/fglrx.okBrYb/debian/fglrx/usr/lib/pxpress/ld.so.conf"
#Run the normal stuff
dh binary-arch
   dh_testroot -a -Nfglrx -Nfglrx-amdcccle
   dh_prep -a -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -a -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a -Nfglrx
   dh_installexamples -a -Nfglrx
   dh_installman -a -Nfglrx
   dh_installcatalogs -a -Nfglrx
   dh_installcron -a -Nfglrx
   dh_installdebconf -a -Nfglrx
   dh_installemacsen -a -Nfglrx
   dh_installifupdown -a -Nfglrx
   dh_installinfo -a -Nfglrx
   dh_pysupport -a -Nfglrx
   dh_installinit -a -Nfglrx
Duplicate specification "O=s" for option "O"
   dh_installmenu -a -Nfglrx
   dh_installmime -a -Nfglrx
   dh_installmodules -a -Nfglrx
   dh_installlogcheck -a -Nfglrx
   dh_installlogrotate -a -Nfglrx
   dh_installpam -a -Nfglrx
   dh_installppp -a -Nfglrx
   dh_installudev -a -Nfglrx
   dh_installwm -a -Nfglrx
   dh_installxfonts -a -Nfglrx
   dh_bugfiles -a -Nfglrx
   dh_lintian -a -Nfglrx
   dh_gconf -a -Nfglrx
   dh_icons -a -Nfglrx
   dh_perl -a -Nfglrx
   dh_usrlocal -a -Nfglrx
   dh_link -a -Nfglrx
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.okBrYb'
dh_shlibdeps -l/tmp/fglrx.okBrYb/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.okBrYb/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 23 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XOpenDisplay: it's probably a plugin.
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/libOpenCL.so.1 debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libamdocl64.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 9
make[1]: Leaving directory `/tmp/fglrx.okBrYb'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.jzxkn3

```

---

### Post by BcRich on 2011-12-05
Solved I think, well everything seems to be working thus far......
I had to force uninstallation of the old ati drivers with
```
sudo /usr/share/ati/amd-uninstall.sh --force
```
then install new drivers
running 
```
fglrxinfo
```
```
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6800 Series  
OpenGL version string: 4.1.11251 Compatibility Profile Context
```
and everything seems to be fine. only strange thing is that I installed ver 11.11 but catalyst says i'm using 11.5
but until i actually see this turning into an actual problem i'm just going to ignore it

---

