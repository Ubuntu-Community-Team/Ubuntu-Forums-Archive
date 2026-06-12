---
title: "problem with kernel's compilation on Feisty"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by szymon_g on 2007-04-17
hi.
im using ubuntu feisty fawn. i've downloaded and installed kernel 2.6.20-15-generic, it works fine.
but i wanted to make a recompilation (for customise kernel for my processor and for other things).
i've downloaded (via apt-get) kernel 2.6.20 (NOT VANILLA, it's ubuntu's kernel), i've unpacked it into /usr/src/linux-source-2.6.20-2.6.20, i've symlink it to /usr/src/linux, i've copied a configure file of my current working kernel (the same number as this one compilated), i've made

make oldconfig

and next make menuconfig.
next was make-kpkg clean

and finally

make-kpkg --initrd --append-to-version=-mojkernel kernel_image kernel_headers

in short: i've followed this howto
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

and after 80minuts (about) I get this info:
INSTALL ubuntu/wireless/prism2/prism2_plx.ko
  INSTALL ubuntu/wireless/prism2/prism2_usb.ko
  INSTALL ubuntu/wireless/rt2x00-legacy/rt2400/rt2400.ko
  INSTALL ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko
  INSTALL ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko
  INSTALL ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
  INSTALL ubuntu/wireless/rt2x00/rt2400pci.ko
  INSTALL ubuntu/wireless/rt2x00/rt2500pci.ko
  INSTALL ubuntu/wireless/rt2x00/rt2500usb.ko
  INSTALL ubuntu/wireless/rt2x00/rt2x00lib.ko
  INSTALL ubuntu/wireless/rt2x00/rt61pci.ko
  INSTALL ubuntu/wireless/rt2x00/rt73usb.ko
  INSTALL ubuntu/wireless/rtl8187/rtl8187.ko
  INSTALL ubuntu/wireless/rtl818x/r818x.ko
  INSTALL ubuntu/wireless/zd1211rw/zd1211rw-mac80211.ko
if [ -r System.map -a -x /sbin/depmod ]; then /sbin/depmod -ae -F System.map -b /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel -r 2.6.20.3-ubuntu1-mojkernel; fi
make[1]: Leaving directory `/usr/src/linux-source-2.6.20-2.6.20'
test ! -e /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/lib/modules/2.6.20.3-ubuntu1-mojkernel/source ||                        \
	   mv /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/lib/modules/2.6.20.3-ubuntu1-mojkernel/source ./debian/source-link
test ! -e /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/lib/modules/2.6.20.3-ubuntu1-mojkernel/build ||                         \
	   mv /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/lib/modules/2.6.20.3-ubuntu1-mojkernel/build ./debian/build-link
/sbin/depmod -q -FSystem.map -b /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel 2.6.20.3-ubuntu1-mojkernel;
test ! -e ./debian/source-link ||                                              \
	   mv ./debian/source-link /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/lib/modules/2.6.20.3-ubuntu1-mojkernel/source
test ! -e  ./debian/build-link ||                                              \
	   mv  ./debian/build-link /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/lib/modules/2.6.20.3-ubuntu1-mojkernel/build
cp arch/i386/boot/bzImage /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel//boot/vmlinuz-2.6.20.3-ubuntu1-mojkernel
chmod 644 /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel//boot/vmlinuz-2.6.20.3-ubuntu1-mojkernel;
if test -d /usr/src/linux/debian/image.d ; then                        \
             TMPTOP=/usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel version=2.6.20.3-ubuntu1-mojkernel IMAGE_TOP=/usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel      \
                   run-parts --verbose /usr/src/linux/debian/image.d ;         \
         fi
if [ -x debian/post-install ]; then                               \
		TMPTOP=/usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel STEM=linux version=2.6.20.3-ubuntu1-mojkernel      \
		IMAGE_TOP=/usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel debian/post-install;                  \
	fi
test ! -s applied_patches || cp applied_patches                        \
                        /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel//boot/patches-2.6.20.3-ubuntu1-mojkernel
test ! -s applied_patches || chmod 644                                 \
                        /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel//boot/patches-2.6.20.3-ubuntu1-mojkernel
test ! -f System.map ||  cp System.map                         \
                        /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel//boot/System.map-2.6.20.3-ubuntu1-mojkernel;
test ! -f System.map ||  chmod 644                             \
                        /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel//boot/System.map-2.6.20.3-ubuntu1-mojkernel;
# For LKCD enabled kernels
test ! -f Kerntypes ||  cp Kerntypes                                   \
                        /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel//boot/Kerntypes-2.6.20.3-ubuntu1-mojkernel
test ! -f Kerntypes ||  chmod 644                                      \
                        /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel//boot/Kerntypes-2.6.20.3-ubuntu1-mojkernel
rm -f /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/lib/modules/2.6.20.3-ubuntu1-mojkernel/build
====== making target binary/linux-image-2.6.20.3-ubuntu1-mojkernel [new prereqs: ]======
This is kernel package version 10.065ubuntu5.
/usr/bin/make -f ./debian/rules debian/linux-image-2.6.20.3-ubuntu1-mojkernel
make[1]: Entering directory `/usr/src/linux-source-2.6.20-2.6.20'
====== making target debian/linux-image-2.6.20.3-ubuntu1-mojkernel [new prereqs: ]======
This is kernel package version 10.065ubuntu5.
install -p -d -m 755 /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN
sed -e 's/=V/2.6.20.3-ubuntu1-mojkernel/g'    -e 's/=IB//g'   \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'          \
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'        \
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \
            -e 's@=M@@g'    -e 's/=OF/YES/g'    \
            -e 's/=S//g'  -e 's@=B@i386@g'    \
         ./debian/pkg/image/postinst > /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/postinst
chmod 755 /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/postinst
sed -e 's/=V/2.6.20.3-ubuntu1-mojkernel/g'    -e 's/=IB//g'    \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'          \
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'        \
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \
            -e 's@=M@@g'    -e 's/=OF/YES/g'    \
            -e 's/=S//g'  -e 's@=B@i386@g'    \
         ./debian/pkg/image/config > /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/config
chmod 755 /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/config
sed -e 's/=V/2.6.20.3-ubuntu1-mojkernel/g'    -e 's/=IB//g'    \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'          \
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'        \
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \
            -e 's@=M@@g'    -e 's/=OF/YES/g'    \
            -e 's/=S//g' -e 's@=B@i386@g'     \
         ./debian/pkg/image/postrm > /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/postrm
chmod 755 /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/postrm
sed -e 's/=V/2.6.20.3-ubuntu1-mojkernel/g'    -e 's/=IB//g'    \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'          \
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'        \
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \
            -e 's@=M@@g'    -e 's/=OF/YES/g'    \
            -e 's/=S//g' -e 's@=B@i386@g'     \
         ./debian/pkg/image/preinst > /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/preinst
chmod 755 /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/preinst
sed -e 's/=V/2.6.20.3-ubuntu1-mojkernel/g'    -e 's/=IB//g'    \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'          \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'        \
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                \
            -e 's@=M@@g'    -e 's/=OF/YES/g'    \
            -e 's/=S//g' -e 's@=B@i386@g'     \
         ./debian/pkg/image/prerm > /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/prerm
chmod 755 /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/prerm
sed -e 's/=V/2.6.20.3-ubuntu1-mojkernel/g'    -e 's/=IB//g'    \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'          \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'        \
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                \
            -e 's@=M@@g'    -e 's/=OF/YES/g'    \
            -e 's/=S//g' -e 's@=B@i386@g'     \
          ./debian/templates.in   > ./debian/templates.master
echo using old template
using old template
install -p    -m 644 ./debian/templates.master /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/DEBIAN/templates
dpkg-gencontrol -DArchitecture=i386 -isp         \
                        -plinux-image-2.6.20.3-ubuntu1-mojkernel -P/usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1-mojkernel/
dpkg-gencontrol: error: package linux-image-2.6.20.3-ubuntu1-mojkernel not in control info
make[1]: *** [debian/linux-image-2.6.20.3-ubuntu1-mojkernel] Error 255
make[1]: Leaving directory `/usr/src/linux-source-2.6.20-2.6.20'
make: *** [binary/linux-image-2.6.20.3-ubuntu1-mojkernel] Error 2
root@linugrat:/usr/src/linux# 

i've tried to compile this kernel 3 times, and 3 times (in a raw :-/) it's failed :-/

is anyone who had/have similar problem?

simon


//edit///
and i used the following options :

make-kpkg -initrd --revision=2.6.20-15.27 kernel_image kernel_headers modules_image 

and the results were the same :-/

---

### Post by luopio on 2007-04-20
I have a similar problem with feisty linux-source: 

/usr/src/linux-source-2.6.20$ sudo make all
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  CHK     include/linux/compile.h
  MODPOST vmlinux
Kernel: arch/i386/boot/bzImage is ready  (#1)
  Building modules, stage 2.
  MODPOST 8 modules
WARNING: "wireless_send_event" [ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko] undefined!
make[1]: *** [__modpost] Error 1
make: *** [modules] Error 2

---

