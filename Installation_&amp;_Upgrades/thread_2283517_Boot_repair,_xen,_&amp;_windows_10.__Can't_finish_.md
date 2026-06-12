---
title: "Boot repair, xen, &amp; windows 10.  Can't finish grub boot repair!"
date: 2015-06-22
forum: Installation &amp; Upgrades
---

### Post by Peter_Dupler on 2015-06-22
Okay, not sure if this is in the right place but this is where it threw me so, here's hoping....
I have a HD with Windows 7, windows 10 preview, PeppermintOS (Ubuntu varient, tried something different), Android X86, & Puppy linux.  Windows 10 upgraded to 10130 something and it took over my boot menu and crashed, so now it boots into windows, but it doesn't go anywhere, it just freezes and/or reboots.  No problem, just run boot repair, get my Grub back and manually add Windows 7 back in, plus no problems using ubuntu of course so I'm all set.  I recently added a program called Xen which is supposed to be a virtual computer thing but I haven't actually tried it yet, though I DID notice it put an entry into my Grub listing.  

So I started up Boot-Repair and got to the first screen where I need to enter stuff  into a terminal:
sudo chroot "/mnt/boot-sav/sda7" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda7" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda7" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*

My memory isn't what it used to be, but it gives an error something like Warning, Grub changed to Xen by default and then it proceeds to re-install a version of Grub, or it tries to.  Boot-Repair gives an error when I try to click forward saying: GRUB is still present. Please try again.  I try the commands again, doesn't help.  I try shutting down, stopping midway, no matter what I do, I seem to be stuck & unable to purge or re-install Grub the right way.  Well, grub MAY be installed the right way, but since Boot-Repair isn't allowed to finish it never changes the boot sector so it still boots into Windows, which is now Windows 10 which freezes & reboots.
Here is what is left of the terminal:
```
Unpacking os-prober (1.63ubuntu1) ...
Selecting previously unselected package grub-efi-amd64-bin.
Preparing to unpack .../grub-efi-amd64-bin_2.02~beta2-22ubuntu1_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.02~beta2-22ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up gettext-base (0.19.2-2ubuntu1) ...
Setting up grub-common (2.02~beta2-22ubuntu1) ...
Setting up os-prober (1.63ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up grub2-common (2.02~beta2-22ubuntu1) ...
Setting up grub-efi-amd64-bin (2.02~beta2-22ubuntu1) ...
Setting up grub-efi-amd64 (2.02~beta2-22ubuntu1) ...
Including Xen overrides from /etc/default/grub.d/xen.cfg
WARNING: GRUB_DEFAULT changed to boot into Xen by default!
         Edit /etc/default/grub.d/xen.cfg to avoid this warning.

Creating config file /etc/default/grub with new version
Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.PackageKit was not provided by any .service files
lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda7" apt-get purge -y --force-yes xen* shim-signed linux-signed*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libannotation-indexer-java-doc' for regex 'xen*'
Note, selecting 'libc6-xen' for regex 'xen*'
Note, selecting 'libsdl2-mixer-dbg' for regex 'xen*'
Note, selecting 'libaudio-mixer-perl' for regex 'xen*'
Note, selecting 'libparse-fixedlength-perl' for regex 'xen*'
Note, selecting 'ipxe-qemu' for regex 'xen*'
Note, selecting 'libexempi-dev' for regex 'xen*'
Note, selecting 'libqtexengine-dev' for regex 'xen*'
Note, selecting 'amixer' for regex 'xen*'
Note, selecting 'xevil' for regex 'xen*'
Note, selecting 'libsdl2-mixer-dev' for regex 'xen*'
Note, selecting 'xen-hypervisor-4.1-amd64' for regex 'xen*'
Note, selecting 'libghc-sdl-mixer-dev' for regex 'xen*'
Note, selecting 'libxfixes3' for regex 'xen*'
Note, selecting 'qasmixer' for regex 'xen*'
Note, selecting 'libannotation-indexer-java' for regex 'xen*'
Note, selecting 'ltsp-cluster-pxeconfig' for regex 'xen*'
Note, selecting 'xenomai' for regex 'xen*'
Note, selecting 'event-execflow-perl' for regex 'xen*'
Note, selecting 'ffado-mixer-qt4' for regex 'xen*'
Note, selecting 'libxcb-xevie0-dbg' for regex 'xen*'
Note, selecting 'chef-indexer' for regex 'xen*'
Note, selecting 'libxext6' for regex 'xen*'
Note, selecting 'ncurses-hexedit' for regex 'xen*'
Note, selecting 'libxerces-c3-doc' for regex 'xen*'
Note, selecting 'nova-compute-xen' for regex 'xen*'
Note, selecting 'xenomai-docs' for regex 'xen*'
Note, selecting 'xenwatch' for regex 'xen*'
Note, selecting 'axe' for regex 'xen*'
Note, selecting 'hexedit' for regex 'xen*'
Note, selecting 'xen-hypervisor-amd64' for regex 'xen*'
Note, selecting 'libstreamindexer-dev' for regex 'xen*'
Note, selecting 'libghc-haskell-lexer-dev' for regex 'xen*'
Note, selecting 'libxerces25-dev' for regex 'xen*'
Note, selecting 'libtext-affixes-perl' for regex 'xen*'
Note, selecting 'libevent-execflow-perl' for regex 'xen*'
Note, selecting 'libxcb-xevie0-dev' for regex 'xen*'
Note, selecting 'libxen-4.4' for regex 'xen*'
Note, selecting 'libxen-4.5' for regex 'xen*'
Note, selecting 'xemacs21-gnome-mule' for regex 'xen*'
Note, selecting 'xen-hypervisor-4.4' for regex 'xen*'
Note, selecting 'kobodeluxe' for regex 'xen*'
Note, selecting 'pxe' for regex 'xen*'
Note, selecting 'pexec' for regex 'xen*'
Note, selecting 'xemacs21-supportel' for regex 'xen*'
Note, selecting 'grub-xen-dbg' for regex 'xen*'
Note, selecting 'camlidl-xepi2' for regex 'xen*'
Note, selecting 'kexec-tools' for regex 'xen*'
Note, selecting 'axel-dbg' for regex 'xen*'
Note, selecting 'libghc-sdl-mixer-doc' for regex 'xen*'
Note, selecting 'xen' for regex 'xen*'
Note, selecting 'pixelmed-apps' for regex 'xen*'
Note, selecting 'xemacs21-gnome-mule-canna-wnn' for regex 'xen*'
Note, selecting 'libghc-executable-path-prof-0.0.3-68e0e' for regex 'xen*'
Note, selecting 'libpixelmed-java-doc' for regex 'xen*'
Note, selecting 'pixelmed-java' for regex 'xen*'
Note, selecting 'libxenstore3.0' for regex 'xen*'
Note, selecting 'libsdl-mixer1.2' for regex 'xen*'
Note, selecting 'xen-hypervisor-4.3-amd64' for regex 'xen*'
Note, selecting 'libstreamindexer0' for regex 'xen*'
Note, selecting 'libxerces-c3.1' for regex 'xen*'
Note, selecting 'libghc-executable-path-dev' for regex 'xen*'
Note, selecting 'libjaxe-java-doc' for regex 'xen*'
Note, selecting 'xemacs21-mule' for regex 'xen*'
Note, selecting 'hexen-wad' for regex 'xen*'
Note, selecting 'python-pyxenstore' for regex 'xen*'
Note, selecting 'libproc-syncexec-perl' for regex 'xen*'
Note, selecting 'libptexenc-dev' for regex 'xen*'
Note, selecting 'libexene-smlnj' for regex 'xen*'
Note, selecting 'xemacs21-support' for regex 'xen*'
Note, selecting 'xfce4-mixer-oss' for regex 'xen*'
Note, selecting 'jack-mixer' for regex 'xen*'
Note, selecting 'dtc-xen' for regex 'xen*'
Note, selecting 'libsdl-mixer1.2-dbg' for regex 'xen*'
Note, selecting 'xemacs21-bin' for regex 'xen*'
Note, selecting 'alsamixergui' for regex 'xen*'
Note, selecting 'libghc-haskell-lexer-dev-1.0-4cd87' for regex 'xen*'
Note, selecting 'xemacs21-mule-canna-wnn' for regex 'xen*'
Note, selecting 'libxerces26-dev' for regex 'xen*'
Note, selecting 'exempi' for regex 'xen*'
Note, selecting 'xeyes' for regex 'xen*'
Note, selecting 'python3-zope.fixers' for regex 'xen*'
Note, selecting 'mixer.app' for regex 'xen*'
Note, selecting 'libghc-haskell-lexer-doc' for regex 'xen*'
Note, selecting 'libxerces-c-samples' for regex 'xen*'
Note, selecting 'xen-hypervisor-4.4-amd64' for regex 'xen*'
Note, selecting 'libxen-ocaml' for regex 'xen*'
Note, selecting 'xenstore-utils' for regex 'xen*'
Note, selecting 'libxerces-c-dev' for regex 'xen*'
Note, selecting 'librdf-prefixes-perl' for regex 'xen*'
Note, selecting 'libsdl-mixer1.2-dev' for regex 'xen*'
Note, selecting 'pixelmed-webstart-apps' for regex 'xen*'
Note, selecting 'xfce4-mixer' for regex 'xen*'
Note, selecting 'gnome-exe-thumbnailer' for regex 'xen*'
Note, selecting 'ruby-execjs' for regex 'xen*'
Note, selecting 'libpixelmed-java' for regex 'xen*'
Note, selecting 'gnome-boxes' for regex 'xen*'
Note, selecting 'libmoosex-attributeindexes-perl' for regex 'xen*'
Note, selecting 'libjaxe-java' for regex 'xen*'
Note, selecting 'axel-kapt' for regex 'xen*'
Note, selecting 'libghc-executable-path-doc' for regex 'xen*'
Note, selecting 'linux-patch-xenomai' for regex 'xen*'
Note, selecting 'hexen-engine' for regex 'xen*'
Note, selecting 'ruby-subexec' for regex 'xen*'
Note, selecting 'jenkins-executable-war' for regex 'xen*'
Note, selecting 'libxen-ocaml-dev' for regex 'xen*'
Note, selecting 'jenkins-executable-war-doc' for regex 'xen*'
Note, selecting 'hexen2-data' for regex 'xen*'
Note, selecting 'libexempi3-dbg' for regex 'xen*'
Note, selecting 'libxerces27-dev' for regex 'xen*'
Note, selecting 'xemacs21' for regex 'xen*'
Note, selecting 'xemacs21-basesupport' for regex 'xen*'
Note, selecting 'xemacs21-mulesupport-el' for regex 'xen*'
Note, selecting 'kvm-pxe' for regex 'xen*'
Note, selecting 'xemacs' for regex 'xen*'
Note, selecting 'audio-mixer' for regex 'xen*'
Note, selecting 'python2.7-execnet' for regex 'xen*'
Note, selecting 'xen-utils' for regex 'xen*'
Note, selecting 'libexempi3' for regex 'xen*'
Note, selecting 'libxerces2-java' for regex 'xen*'
Note, selecting 'xen-utils-common' for regex 'xen*'
Note, selecting 'dtc-xen-firewall' for regex 'xen*'
Note, selecting 'x11proto-fixes-dev' for regex 'xen*'
Note, selecting 'pxe-kexec' for regex 'xen*'
Note, selecting 'cl-lexer' for regex 'xen*'
Note, selecting 'execstack' for regex 'xen*'
Note, selecting 'libxerces-c-doc' for regex 'xen*'
Note, selecting 'elyxer' for regex 'xen*'
Note, selecting 'pxelinux' for regex 'xen*'
Note, selecting 'apache2-suexec-custom' for regex 'xen*'
Note, selecting 'libjmxetric-java' for regex 'xen*'
Note, selecting 'hexen2-engine' for regex 'xen*'
Note, selecting 'libxen-ocaml-k1q31' for regex 'xen*'
Note, selecting 'xserver-xephyr' for regex 'xen*'
Note, selecting 'libxcb-xevie0' for regex 'xen*'
Note, selecting 'libxfixes-dev' for regex 'xen*'
Note, selecting 'libghc-executable-path-prof' for regex 'xen*'
Note, selecting 'xenomai-doc' for regex 'xen*'
Note, selecting 'libjaxen-java' for regex 'xen*'
Note, selecting 'libxerces2-java-doc' for regex 'xen*'
Note, selecting 'metapixel' for regex 'xen*'
Note, selecting 'aide-xen' for regex 'xen*'
Note, selecting 'xemacs21-gnome-nomule' for regex 'xen*'
Note, selecting 'apache2-suexec' for regex 'xen*'
Note, selecting 'kvm-ipxe' for regex 'xen*'
Note, selecting 'wmmixer' for regex 'xen*'
Note, selecting 'libghc-sdl-mixer-prof' for regex 'xen*'
Note, selecting 'libxext6-dbg' for regex 'xen*'
Note, selecting 'boxes' for regex 'xen*'
Note, selecting 'xen-system' for regex 'xen*'
Note, selecting 'jaxe' for regex 'xen*'
Note, selecting 'divxenc' for regex 'xen*'
Note, selecting 'libxext-dev' for regex 'xen*'
Note, selecting 'libxerces28-dev' for regex 'xen*'
Note, selecting 'gexec' for regex 'xen*'
Note, selecting 'xemacs21-nomule' for regex 'xen*'
Note, selecting 'xen-linux-system-686-pae' for regex 'xen*'
Note, selecting 'x11proto-xext-dev' for regex 'xen*'
Note, selecting 'xfce4-mixer-alsa' for regex 'xen*'
Note, selecting 'lcmaps-plugins-basic-posixenf' for regex 'xen*'
Note, selecting 'libxerces-c28' for regex 'xen*'
Note, selecting 'uhexen2' for regex 'xen*'
Note, selecting 'xen-hypervisor' for regex 'xen*'
Note, selecting 'gstreamer0.10-videomixer2' for regex 'xen*'
Note, selecting 'kvm-ipxe-precise' for regex 'xen*'
Note, selecting 'pixelize' for regex 'xen*'
Note, selecting 'xen-linux-system-amd64' for regex 'xen*'
Note, selecting 'asmixer' for regex 'xen*'
Note, selecting 'xemacs21-basesupport-el' for regex 'xen*'
Note, selecting 'libxenomai-dev' for regex 'xen*'
Note, selecting 'xen-utils-4.0' for regex 'xen*'
Note, selecting 'xen-utils-4.1' for regex 'xen*'
Note, selecting 'xen-utils-4.3' for regex 'xen*'
Note, selecting 'xen-utils-4.4' for regex 'xen*'
Note, selecting 'libsdl2-mixer-2.0-0' for regex 'xen*'
Note, selecting 'grub-xen-bin' for regex 'xen*'
Note, selecting 'libmaven-exec-plugin-java' for regex 'xen*'
Note, selecting 'blixem' for regex 'xen*'
Note, selecting 'xemacs-support' for regex 'xen*'
Note, selecting 'uhexen2-common' for regex 'xen*'
Note, selecting 'libcommons-exec-java' for regex 'xen*'
Note, selecting 'autopkgtest-xenlvm' for regex 'xen*'
Note, selecting 'dh-exec' for regex 'xen*'
Note, selecting 'libxcb-xfixes0' for regex 'xen*'
Note, selecting 'x-audio-mixer' for regex 'xen*'
Note, selecting 'libxerces-c2-dev' for regex 'xen*'
Note, selecting 'xen-tools' for regex 'xen*'
Note, selecting 'pixelmed-www' for regex 'xen*'
Note, selecting 'libxen-dev' for regex 'xen*'
Note, selecting 'libxerces28' for regex 'xen*'
Note, selecting 'libsdl-mixer-gst' for regex 'xen*'
Note, selecting 'libqtexengine1' for regex 'xen*'
Note, selecting 'axel' for regex 'xen*'
Note, selecting 'libxerces2-java-gcj' for regex 'xen*'
Note, selecting 'python-xe' for regex 'xen*'
Note, selecting 'libgetopt-mixed-perl' for regex 'xen*'
Note, selecting 'ipxe' for regex 'xen*'
Note, selecting 'libpixels-java' for regex 'xen*'
Note, selecting 'xephem' for regex 'xen*'
Note, selecting 'grub-ipxe' for regex 'xen*'
Note, selecting 'libxfixes3-dbg' for regex 'xen*'
Note, selecting 'libghc-executable-path-dev-0.0.3-68e0e' for regex 'xen*'
Note, selecting 'xen-hypervisor-i386' for regex 'xen*'
Note, selecting 'hexec' for regex 'xen*'
Note, selecting 'hexer' for regex 'xen*'
Note, selecting 'libxext-doc' for regex 'xen*'
Note, selecting 'libxerces28-doc' for regex 'xen*'
Note, selecting 'python-execnet' for regex 'xen*'
Note, selecting 'xen-system-amd64' for regex 'xen*'
Note, selecting 'openxenmanager' for regex 'xen*'
Note, selecting 'libmaven-indexer-java' for regex 'xen*'
Note, selecting 'libghc-haskell-lexer-prof' for regex 'xen*'
Note, selecting 'libxenomai1' for regex 'xen*'
Note, selecting 'libxerces-c3-samples' for regex 'xen*'
Note, selecting 'kobodeluxe-data' for regex 'xen*'
Note, selecting 'libxcb-xfixes0-dbg' for regex 'xen*'
Note, selecting 'survex-svxedit' for regex 'xen*'
Note, selecting 'non-mixer' for regex 'xen*'
Note, selecting 'xemacs21-mulesupport' for regex 'xen*'
Note, selecting 'libghc-haskell-lexer-prof-1.0-4cd87' for regex 'xen*'
Note, selecting 'grub-xen' for regex 'xen*'
Note, selecting 'xen-system-i386' for regex 'xen*'
Note, selecting 'xserver-xephyr-lts-utopic' for regex 'xen*'
Note, selecting 'libptexenc1' for regex 'xen*'
Note, selecting 'haxe' for regex 'xen*'
Note, selecting 'xemacs-widget' for regex 'xen*'
Note, selecting 'regexxer' for regex 'xen*'
Note, selecting 'libjaxen-java-doc' for regex 'xen*'
Note, selecting 'apache2-suexec-pristine' for regex 'xen*'
Note, selecting 'gridengine-exec' for regex 'xen*'
Note, selecting 'libxen-ocaml-dev-k1q31' for regex 'xen*'
Note, selecting 'libxerces-c3-dev' for regex 'xen*'
Note, selecting 'libxcb-xfixes0-dev' for regex 'xen*'
Note, selecting 'gnome-alsamixer' for regex 'xen*'
Note, selecting 'texlive-xetex' for regex 'xen*'
Note, selecting 'xen-hypervisor-i386-pae' for regex 'xen*'
Note, selecting 'fonttools-eexecop' for regex 'xen*'
Note, selecting 'xenomai-runtime' for regex 'xen*'
Note, selecting 'libxerces-c2-doc' for regex 'xen*'
Note, selecting 'wxhexeditor' for regex 'xen*'
Package 'libmoosex-attributeindexes-perl' is not installed, so not removed
Package 'libstreamindexer-dev' is not installed, so not removed
Package 'libstreamindexer0' is not installed, so not removed
Package 'xen-utils-4.1' is not installed, so not removed
Package 'xen-utils-4.3' is not installed, so not removed
Package 'xen' is not installed, so not removed
Note, selecting 'libxen-ocaml' instead of 'libxen-ocaml-k1q31'
Note, selecting 'libxen-ocaml-dev' instead of 'libxen-ocaml-dev-k1q31'
Package 'xeyes' is not installed, so not removed
Note, selecting 'camlidl' instead of 'camlidl-xepi2'
Package 'chef-indexer' is not installed, so not removed
Package 'xen-linux-system-amd64' is not installed, so not removed
Package 'xen-linux-system-686-pae' is not installed, so not removed
Package 'xemacs' is not installed, so not removed
Package 'gstreamer0.10-videomixer2' is not installed, so not removed
Package 'event-execflow-perl' is not installed, so not removed
Note, selecting 'libghc-executable-path-dev' instead of 'libghc-executable-path-dev-0.0.3-68e0e'
Note, selecting 'libghc-executable-path-prof' instead of 'libghc-executable-path-prof-0.0.3-68e0e'
Note, selecting 'libghc-haskell-lexer-dev' instead of 'libghc-haskell-lexer-dev-1.0-4cd87'
Note, selecting 'libghc-haskell-lexer-prof' instead of 'libghc-haskell-lexer-prof-1.0-4cd87'
Package 'pixelmed-java' is not installed, so not removed
Package 'xenomai' is not installed, so not removed
Package 'libxerces25-dev' is not installed, so not removed
Package 'libxerces26-dev' is not installed, so not removed
Package 'libxerces27-dev' is not installed, so not removed
Package 'libxerces28-dev' is not installed, so not removed
Note, selecting 'libxerces-c-dev' instead of 'libxerces-c3-dev'
Note, selecting 'libxerces-c-doc' instead of 'libxerces-c3-doc'
Note, selecting 'libxerces-c-samples' instead of 'libxerces-c3-samples'
Package 'libxerces28-doc' is not installed, so not removed
Package 'libxerces28' is not installed, so not removed
Package 'amixer' is not installed, so not removed
Package 'blixem' is not installed, so not removed
Package 'non-mixer' is not installed, so not removed
Package 'xen-system-i386' is not installed, so not removed
Package 'xen-utils-4.0' is not installed, so not removed
Note, selecting 'python-execnet' instead of 'python2.7-execnet'
Package 'xephem' is not installed, so not removed
Package 'kvm-pxe' is not installed, so not removed
Package 'xemacs-widget' is not installed, so not removed
Package 'xemacs-support' is not installed, so not removed
Note, selecting 'xen-hypervisor-4.4-amd64' instead of 'xen-hypervisor'
Note, selecting 'xen-hypervisor-4.4-amd64' instead of 'xen-hypervisor-4.4'
Note, selecting 'xen-hypervisor-4.4-amd64' instead of 'xen-hypervisor-amd64'
Note, selecting 'xen-system-amd64' instead of 'xen-system'
Package 'xen-hypervisor-i386' is not installed, so not removed
Package 'xen-hypervisor-i386-pae' is not installed, so not removed
Note, selecting 'xen-utils-4.4' instead of 'xen-utils'
Package 'xenomai-docs' is not installed, so not removed
Package 'xfce4-mixer-alsa' is not installed, so not removed
Package 'xfce4-mixer-oss' is not installed, so not removed
Package 'hexen-wad' is not installed, so not removed
Note, selecting 'chocolate-doom' instead of 'hexen-engine'
Package 'hexen2-data' is not installed, so not removed
Note, selecting 'uhexen2' instead of 'hexen2-engine'
Package 'libc6-xen' is not installed, so not removed
Note, selecting 'linux-signed-image-3.13.0-44-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-utopic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-24-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-33-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-53-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-raring-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-33-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-31-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-51-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-40-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-40-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-trusty' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-raring' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-saucy-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-29-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-49-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-15-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-saucy' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-29-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-38-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-saucy' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-27-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-36-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-36-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-25-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-45-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-quantal' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-34-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-54-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-quantal' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-20-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-34-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-utopic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-43-generic' for regex 'linux-signed*'
Note, selecting 'efilinux-signed' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-52-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-32-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-41-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-18-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-41-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-30-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-trusty' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-30-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-39-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-raring' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-vivid' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-39-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-vivid' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-quantal-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-28-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-48-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-37-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-37-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-26-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-46-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-55-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-21-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-35-generic' for regex 'linux-signed*'
Package 'libjaxen-java' is not installed, so not removed
Package 'libjaxen-java-doc' is not installed, so not removed
Package 'libxcb-xevie0' is not installed, so not removed
Package 'libxcb-xevie0-dbg' is not installed, so not removed
Package 'libxcb-xevie0-dev' is not installed, so not removed
Package 'libxcb-xfixes0-dbg' is not installed, so not removed
Package 'libxcb-xfixes0-dev' is not installed, so not removed
Package 'libxerces2-java' is not installed, so not removed
Package 'libxerces2-java-doc' is not installed, so not removed
Package 'libxerces2-java-gcj' is not installed, so not removed
Package 'x11proto-fixes-dev' is not installed, so not removed
Package 'x11proto-xext-dev' is not installed, so not removed
Package 'alsamixergui' is not installed, so not removed
Package 'asmixer' is not installed, so not removed
Package 'autopkgtest-xenlvm' is not installed, so not removed
Package 'axel' is not installed, so not removed
Package 'axel-dbg' is not installed, so not removed
Package 'axel-kapt' is not installed, so not removed
Package 'boxes' is not installed, so not removed
Package 'cl-lexer' is not installed, so not removed
Package 'dtc-xen' is not installed, so not removed
Package 'dtc-xen-firewall' is not installed, so not removed
Package 'efilinux-signed' is not installed, so not removed
Package 'elyxer' is not installed, so not removed
Package 'exempi' is not installed, so not removed
Package 'ffado-mixer-qt4' is not installed, so not removed
Package 'fonttools-eexecop' is not installed, so not removed
Package 'gexec' is not installed, so not removed
Package 'gnome-alsamixer' is not installed, so not removed
Package 'gnome-boxes' is not installed, so not removed
Package 'gridengine-exec' is not installed, so not removed
Package 'haxe' is not installed, so not removed
Package 'hexec' is not installed, so not removed
Package 'hexedit' is not installed, so not removed
Package 'hexer' is not installed, so not removed
Package 'jack-mixer' is not installed, so not removed
Package 'jaxe' is not installed, so not removed
Package 'jenkins-executable-war' is not installed, so not removed
Package 'jenkins-executable-war-doc' is not installed, so not removed
Package 'kobodeluxe' is not installed, so not removed
Package 'kobodeluxe-data' is not installed, so not removed
Package 'lcmaps-plugins-basic-posixenf' is not installed, so not removed
Package 'libannotation-indexer-java' is not installed, so not removed
Package 'libannotation-indexer-java-doc' is not installed, so not removed
Package 'libaudio-mixer-perl' is not installed, so not removed
Package 'libcommons-exec-java' is not installed, so not removed
Package 'libexene-smlnj' is not installed, so not removed
Package 'libgetopt-mixed-perl' is not installed, so not removed
Package 'libghc-executable-path-dev' is not installed, so not removed
Package 'libghc-executable-path-doc' is not installed, so not removed
Package 'libghc-executable-path-prof' is not installed, so not removed
Package 'libghc-haskell-lexer-dev' is not installed, so not removed
Package 'libghc-haskell-lexer-doc' is not installed, so not removed
Package 'libghc-haskell-lexer-prof' is not installed, so not removed
Package 'libghc-sdl-mixer-dev' is not installed, so not removed
Package 'libghc-sdl-mixer-doc' is not installed, so not removed
Package 'libghc-sdl-mixer-prof' is not installed, so not removed
Package 'libjaxe-java' is not installed, so not removed
Package 'libjaxe-java-doc' is not installed, so not removed
Package 'libjmxetric-java' is not installed, so not removed
Package 'libmaven-exec-plugin-java' is not installed, so not removed
Package 'libmaven-indexer-java' is not installed, so not removed
Package 'libparse-fixedlength-perl' is not installed, so not removed
Package 'libpixelmed-java' is not installed, so not removed
Package 'libpixelmed-java-doc' is not installed, so not removed
Package 'libpixels-java' is not installed, so not removed
Package 'libproc-syncexec-perl' is not installed, so not removed
Package 'libqtexengine-dev' is not installed, so not removed
Package 'libqtexengine1' is not installed, so not removed
Package 'librdf-prefixes-perl' is not installed, so not removed
Package 'libsdl-mixer-gst' is not installed, so not removed
Package 'libsdl-mixer1.2-dbg' is not installed, so not removed
Package 'libsdl-mixer1.2-dev' is not installed, so not removed
Package 'libsdl2-mixer-2.0-0' is not installed, so not removed
Package 'libsdl2-mixer-dbg' is not installed, so not removed
Package 'libsdl2-mixer-dev' is not installed, so not removed
Package 'libtext-affixes-perl' is not installed, so not removed
Package 'libxenomai-dev' is not installed, so not removed
Package 'libxenomai1' is not installed, so not removed
Package 'libxerces-c2-dev' is not installed, so not removed
Package 'libxerces-c2-doc' is not installed, so not removed
Package 'libxerces-c28' is not installed, so not removed
Package 'linux-patch-xenomai' is not installed, so not removed
Package 'ltsp-cluster-pxeconfig' is not installed, so not removed
Package 'metapixel' is not installed, so not removed
Package 'mixer.app' is not installed, so not removed
Package 'ncurses-hexedit' is not installed, so not removed
Package 'openxenmanager' is not installed, so not removed
Package 'pexec' is not installed, so not removed
Package 'pixelize' is not installed, so not removed
Package 'pixelmed-apps' is not installed, so not removed
Package 'pixelmed-webstart-apps' is not installed, so not removed
Package 'pixelmed-www' is not installed, so not removed
Package 'pxe' is not installed, so not removed
Package 'pxe-kexec' is not installed, so not removed
Package 'python-execnet' is not installed, so not removed
Package 'python-pyxenstore' is not installed, so not removed
Package 'python-xe' is not installed, so not removed
Package 'python3-zope.fixers' is not installed, so not removed
Package 'qasmixer' is not installed, so not removed
Package 'regexxer' is not installed, so not removed
Package 'ruby-execjs' is not installed, so not removed
Package 'ruby-subexec' is not installed, so not removed
Package 'survex-svxedit' is not installed, so not removed
Package 'texlive-xetex' is not installed, so not removed
Package 'wmmixer' is not installed, so not removed
Package 'wxhexeditor' is not installed, so not removed
Package 'xemacs21' is not installed, so not removed
Package 'xemacs21-basesupport' is not installed, so not removed
Package 'xemacs21-basesupport-el' is not installed, so not removed
Package 'xemacs21-bin' is not installed, so not removed
Package 'xemacs21-gnome-mule' is not installed, so not removed
Package 'xemacs21-gnome-mule-canna-wnn' is not installed, so not removed
Package 'xemacs21-gnome-nomule' is not installed, so not removed
Package 'xemacs21-mule' is not installed, so not removed
Package 'xemacs21-mule-canna-wnn' is not installed, so not removed
Package 'xemacs21-mulesupport' is not installed, so not removed
Package 'xemacs21-mulesupport-el' is not installed, so not removed
Package 'xemacs21-nomule' is not installed, so not removed
Package 'xemacs21-support' is not installed, so not removed
Package 'xemacs21-supportel' is not installed, so not removed
Package 'xen-tools' is not installed, so not removed
Package 'xenomai-doc' is not installed, so not removed
Package 'xenomai-runtime' is not installed, so not removed
Package 'xenwatch' is not installed, so not removed
Package 'xevil' is not installed, so not removed
Package 'xfce4-mixer' is not installed, so not removed
Package 'axe' is not installed, so not removed
Package 'divxenc' is not installed, so not removed
Package 'uhexen2' is not installed, so not removed
Package 'uhexen2-common' is not installed, so not removed
Package 'libxen-ocaml' is not installed, so not removed
Package 'libxen-ocaml-dev' is not installed, so not removed
Package 'linux-signed-generic-lts-quantal' is not installed, so not removed
Package 'linux-signed-generic-lts-quantal-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-raring' is not installed, so not removed
Package 'linux-signed-generic-lts-raring-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-saucy' is not installed, so not removed
Package 'linux-signed-generic-lts-saucy-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-trusty' is not installed, so not removed
Package 'linux-signed-generic-lts-utopic' is not installed, so not removed
Package 'linux-signed-generic-lts-vivid' is not installed, so not removed
Package 'linux-signed-image-3.13.0-24-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-27-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-29-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-30-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-32-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-33-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-34-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-35-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-36-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-37-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-39-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-40-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-41-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-43-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-44-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-45-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-46-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-48-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-49-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-51-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-52-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-53-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-54-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-55-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-25-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-26-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-28-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-29-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-30-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-31-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-33-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-34-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-36-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-37-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-38-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-39-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-40-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-41-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-18-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-20-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-21-generic' is not installed, so not removed
Package 'linux-signed-image-generic-lts-quantal' is not installed, so not removed
Package 'linux-signed-image-generic-lts-raring' is not installed, so not removed
Package 'linux-signed-image-generic-lts-saucy' is not installed, so not removed
Package 'linux-signed-image-generic-lts-trusty' is not installed, so not removed
Package 'linux-signed-image-generic-lts-utopic' is not installed, so not removed
Package 'linux-signed-image-generic-lts-vivid' is not installed, so not removed
Package 'aide-xen' is not installed, so not removed
Package 'apache2-suexec' is not installed, so not removed
Package 'apache2-suexec-custom' is not installed, so not removed
Package 'apache2-suexec-pristine' is not installed, so not removed
Package 'kvm-ipxe' is not installed, so not removed
Package 'kvm-ipxe-precise' is not installed, so not removed
Package 'libxerces-c-dev' is not installed, so not removed
Package 'libxerces-c-doc' is not installed, so not removed
Package 'libxerces-c-samples' is not installed, so not removed
Package 'libxerces-c3.1' is not installed, so not removed
Package 'nova-compute-xen' is not installed, so not removed
Package 'xen-hypervisor-4.1-amd64' is not installed, so not removed
Package 'xen-hypervisor-4.3-amd64' is not installed, so not removed
Package 'xserver-xephyr' is not installed, so not removed
Package 'xserver-xephyr-lts-utopic' is not installed, so not removed
Package 'dh-exec' is not installed, so not removed
Package 'execstack' is not installed, so not removed
Package 'grub-ipxe' is not installed, so not removed
Package 'grub-xen' is not installed, so not removed
Package 'grub-xen-bin' is not installed, so not removed
Package 'grub-xen-dbg' is not installed, so not removed
Package 'ipxe' is not installed, so not removed
Package 'kexec-tools' is not installed, so not removed
Package 'libexempi-dev' is not installed, so not removed
Package 'libexempi3' is not installed, so not removed
Package 'libexempi3-dbg' is not installed, so not removed
Package 'libptexenc-dev' is not installed, so not removed
Package 'libptexenc1' is not installed, so not removed
Package 'libxen-4.5' is not installed, so not removed
Package 'libxen-dev' is not installed, so not removed
Package 'libxext-dev' is not installed, so not removed
Package 'libxext-doc' is not installed, so not removed
Package 'libxext6-dbg' is not installed, so not removed
Package 'libxfixes-dev' is not installed, so not removed
Package 'libxfixes3-dbg' is not installed, so not removed
Package 'linux-signed-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-15-generic' is not installed, so not removed
Package 'linux-signed-image-generic' is not installed, so not removed
Package 'pxelinux' is not installed, so not removed
Package 'shim-signed' is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lsb-base : Breaks: upstart (< 1.12.1-0ubuntu8)
            Breaks: upstart:i386 (< 1.12.1-0ubuntu8)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda7" apt-get purge -y --force-yes 





```



 ```
grub*-common shim-signed linux-signed*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'grub-common' for regex 'grub*-common'
Note, selecting 'linux-signed-image-3.13.0-44-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-utopic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-24-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-33-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-53-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-raring-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-33-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-31-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-51-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-40-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-40-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-trusty' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-raring' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-saucy-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-29-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-49-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-15-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-saucy' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-29-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-38-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-saucy' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-27-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-36-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-36-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-25-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-45-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-quantal' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-34-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-54-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-quantal' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-20-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-34-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-utopic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-43-generic' for regex 'linux-signed*'
Note, selecting 'efilinux-signed' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-52-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-32-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-41-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-18-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-41-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-30-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-trusty' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-30-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-39-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-raring' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-vivid' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-39-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-vivid' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-quantal-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-28-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-48-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-37-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-37-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-26-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-46-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-55-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-21-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-35-generic' for regex 'linux-signed*'
Package 'efilinux-signed' is not installed, so not removed
Package 'linux-signed-generic-lts-quantal' is not installed, so not removed
Package 'linux-signed-generic-lts-quantal-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-raring' is not installed, so not removed
Package 'linux-signed-generic-lts-raring-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-saucy' is not installed, so not removed
Package 'linux-signed-generic-lts-saucy-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-trusty' is not installed, so not removed
Package 'linux-signed-generic-lts-utopic' is not installed, so not removed
Package 'linux-signed-generic-lts-vivid' is not installed, so not removed
Package 'linux-signed-image-3.13.0-24-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-27-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-29-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-30-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-32-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-33-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-34-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-35-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-36-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-37-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-39-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-40-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-41-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-43-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-44-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-45-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-46-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-48-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-49-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-51-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-52-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-53-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-54-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-55-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-25-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-26-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-28-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-29-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-30-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-31-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-33-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-34-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-36-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-37-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-38-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-39-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-40-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-41-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-18-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-20-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-21-generic' is not installed, so not removed
Package 'linux-signed-image-generic-lts-quantal' is not installed, so not removed
Package 'linux-signed-image-generic-lts-raring' is not installed, so not removed
Package 'linux-signed-image-generic-lts-saucy' is not installed, so not removed
Package 'linux-signed-image-generic-lts-trusty' is not installed, so not removed
Package 'linux-signed-image-generic-lts-utopic' is not installed, so not removed
Package 'linux-signed-image-generic-lts-vivid' is not installed, so not removed
Package 'grub-common' is not installed, so not removed. Did you mean 'grub-common:i386'?
Package 'linux-signed-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-15-generic' is not installed, so not removed
Package 'linux-signed-image-generic' is not installed, so not removed
Package 'shim-signed' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  debugedit dh-apparmor gambas3-dev gambas3-examples gambas3-gb-cairo
  gambas3-gb-chart gambas3-gb-compress gambas3-gb-compress-bzlib2
  gambas3-gb-compress-zlib gambas3-gb-crypt gambas3-gb-db gambas3-gb-db-form
  gambas3-gb-db-mysql gambas3-gb-db-odbc gambas3-gb-db-postgresql
  gambas3-gb-db-sqlite3 gambas3-gb-dbus gambas3-gb-desktop
  gambas3-gb-eval-highlight gambas3-gb-form gambas3-gb-form-dialog
  gambas3-gb-form-mdi gambas3-gb-form-stock gambas3-gb-gtk gambas3-gb-gui
  gambas3-gb-image gambas3-gb-image-effect gambas3-gb-image-imlib
  gambas3-gb-image-io gambas3-gb-mysql gambas3-gb-net gambas3-gb-net-curl
  gambas3-gb-net-smtp gambas3-gb-opengl gambas3-gb-opengl-glsl
  gambas3-gb-opengl-glu gambas3-gb-option gambas3-gb-pcre gambas3-gb-pdf
  gambas3-gb-qt4 gambas3-gb-qt4-ext gambas3-gb-qt4-opengl
  gambas3-gb-qt4-webkit gambas3-gb-report gambas3-gb-sdl gambas3-gb-sdl-sound
  gambas3-gb-settings gambas3-gb-v4l gambas3-gb-vb gambas3-gb-web
  gambas3-gb-xml gambas3-gb-xml-rpc gambas3-gb-xml-xslt gambas3-runtime
  glade2script libasprintf-dev libasprintf0c2:i386 libgettextpo-dev
  libgettextpo0 libmail-sendmail-perl libpq5 librpmbuild3 librpmsign1
  libsys-hostname-long-perl linux-headers-3.13.0-48
  linux-headers-3.13.0-48-generic linux-image-3.13.0-48-generic
  linux-image-extra-3.13.0-48-generic pastebinit rpm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1325 not upgraded.
lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda7" dpkg --configure -alubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda7" apt-get install -fyReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  debugedit dh-apparmor gambas3-dev gambas3-examples gambas3-gb-cairo
  gambas3-gb-chart gambas3-gb-compress gambas3-gb-compress-bzlib2
  gambas3-gb-compress-zlib gambas3-gb-crypt gambas3-gb-db gambas3-gb-db-form
  gambas3-gb-db-mysql gambas3-gb-db-odbc gambas3-gb-db-postgresql
  gambas3-gb-db-sqlite3 gambas3-gb-dbus gambas3-gb-desktop
  gambas3-gb-eval-highlight gambas3-gb-form gambas3-gb-form-dialog
  gambas3-gb-form-mdi gambas3-gb-form-stock gambas3-gb-gtk gambas3-gb-gui
  gambas3-gb-image gambas3-gb-image-effect gambas3-gb-image-imlib
  gambas3-gb-image-io gambas3-gb-mysql gambas3-gb-net gambas3-gb-net-curl
  gambas3-gb-net-smtp gambas3-gb-opengl gambas3-gb-opengl-glsl
  gambas3-gb-opengl-glu gambas3-gb-option gambas3-gb-pcre gambas3-gb-pdf
  gambas3-gb-qt4 gambas3-gb-qt4-ext gambas3-gb-qt4-opengl
  gambas3-gb-qt4-webkit gambas3-gb-report gambas3-gb-sdl gambas3-gb-sdl-sound
  gambas3-gb-settings gambas3-gb-v4l gambas3-gb-vb gambas3-gb-web
  gambas3-gb-xml gambas3-gb-xml-rpc gambas3-gb-xml-xslt gambas3-runtime
  glade2script libasprintf-dev libasprintf0c2:i386 libgettextpo-dev
  libgettextpo0 libmail-sendmail-perl libpq5 librpmbuild3 librpmsign1
  libsys-hostname-long-perl linux-headers-3.13.0-48
  linux-headers-3.13.0-48-generic linux-image-3.13.0-48-generic
  linux-image-extra-3.13.0-48-generic pastebinit rpm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1325 not upgraded.
lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda7" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'grub-common' for regex 'grub*-common'
Note, selecting 'linux-signed-image-3.13.0-44-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-utopic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-24-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-33-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-53-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-raring-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-33-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-31-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-51-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-40-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-40-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-trusty' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-raring' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-saucy-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-29-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-49-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-15-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-saucy' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-29-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-38-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-saucy' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-27-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-36-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-36-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-25-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-45-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-quantal' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-34-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-54-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-quantal' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-20-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-34-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-utopic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-43-generic' for regex 'linux-signed*'
Note, selecting 'efilinux-signed' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-52-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-32-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-41-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-18-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-41-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-30-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-trusty' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-30-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-39-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-raring' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-vivid' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-39-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-vivid' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-quantal-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-28-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-48-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-37-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-37-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.16.0-26-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-46-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-55-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.19.0-21-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.13.0-35-generic' for regex 'linux-signed*'
Package 'efilinux-signed' is not installed, so not removed
Package 'linux-signed-generic-lts-quantal' is not installed, so not removed
Package 'linux-signed-generic-lts-quantal-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-raring' is not installed, so not removed
Package 'linux-signed-generic-lts-raring-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-saucy' is not installed, so not removed
Package 'linux-signed-generic-lts-saucy-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-trusty' is not installed, so not removed
Package 'linux-signed-generic-lts-utopic' is not installed, so not removed
Package 'linux-signed-generic-lts-vivid' is not installed, so not removed
Package 'linux-signed-image-3.13.0-24-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-27-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-29-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-30-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-32-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-33-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-34-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-35-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-36-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-37-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-39-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-40-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-41-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-43-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-44-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-45-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-46-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-48-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-49-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-51-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-52-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-53-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-54-generic' is not installed, so not removed
Package 'linux-signed-image-3.13.0-55-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-25-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-26-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-28-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-29-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-30-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-31-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-33-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-34-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-36-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-37-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-38-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-39-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-40-generic' is not installed, so not removed
Package 'linux-signed-image-3.16.0-41-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-18-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-20-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-21-generic' is not installed, so not removed
Package 'linux-signed-image-generic-lts-quantal' is not installed, so not removed
Package 'linux-signed-image-generic-lts-raring' is not installed, so not removed
Package 'linux-signed-image-generic-lts-saucy' is not installed, so not removed
Package 'linux-signed-image-generic-lts-trusty' is not installed, so not removed
Package 'linux-signed-image-generic-lts-utopic' is not installed, so not removed
Package 'linux-signed-image-generic-lts-vivid' is not installed, so not removed
Package 'grub-common' is not installed, so not removed. Did you mean 'grub-common:i386'?
Package 'linux-signed-generic' is not installed, so not removed
Package 'linux-signed-image-3.19.0-15-generic' is not installed, so not removed
Package 'linux-signed-image-generic' is not installed, so not removed
Package 'shim-signed' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  debugedit dh-apparmor gambas3-dev gambas3-examples gambas3-gb-cairo
  gambas3-gb-chart gambas3-gb-compress gambas3-gb-compress-bzlib2
  gambas3-gb-compress-zlib gambas3-gb-crypt gambas3-gb-db gambas3-gb-db-form
  gambas3-gb-db-mysql gambas3-gb-db-odbc gambas3-gb-db-postgresql
  gambas3-gb-db-sqlite3 gambas3-gb-dbus gambas3-gb-desktop
  gambas3-gb-eval-highlight gambas3-gb-form gambas3-gb-form-dialog
  gambas3-gb-form-mdi gambas3-gb-form-stock gambas3-gb-gtk gambas3-gb-gui
  gambas3-gb-image gambas3-gb-image-effect gambas3-gb-image-imlib
  gambas3-gb-image-io gambas3-gb-mysql gambas3-gb-net gambas3-gb-net-curl
  gambas3-gb-net-smtp gambas3-gb-opengl gambas3-gb-opengl-glsl
  gambas3-gb-opengl-glu gambas3-gb-option gambas3-gb-pcre gambas3-gb-pdf
  gambas3-gb-qt4 gambas3-gb-qt4-ext gambas3-gb-qt4-opengl
  gambas3-gb-qt4-webkit gambas3-gb-report gambas3-gb-sdl gambas3-gb-sdl-sound
  gambas3-gb-settings gambas3-gb-v4l gambas3-gb-vb gambas3-gb-web
  gambas3-gb-xml gambas3-gb-xml-rpc gambas3-gb-xml-xslt gambas3-runtime
  glade2script libasprintf-dev libasprintf0c2:i386 libgettextpo-dev
  libgettextpo0 libmail-sendmail-perl libpq5 librpmbuild3 librpmsign1
  libsys-hostname-long-perl linux-headers-3.13.0-48
  linux-headers-3.13.0-48-generic linux-image-3.13.0-48-generic
  linux-image-extra-3.13.0-48-generic pastebinit rpm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1325 not upgraded.
lubuntu@lubuntu:~$ 

```

Lots of info, hopefully somebody can make sense of it & point me in the right direction.  Thanks!!!

---

### Post by oldfred on 2015-06-22
Please use code tags which are easy to add with Advanced Editor and # icon.

Do not know Xen.

Please run the Summary report in Boot-Repair and post the link it provides.

---

### Post by MAFoElffen on 2015-06-22
Explanation: Xen is a micro-kernel design for hypervisor management. It is applied directly to the Linux kernel of its host, so that memory management and CPU scheduling are prioritized to the virtual machines running under that hypervisor. Xen runs in a more privileged CPU state than any other software on that host. It runs in Dom0.

Xen could be (and has been) applied to any distro of Linux. 

EDITS-- Treat it just as any other Linux kernel. Grub does have considerations concerning Xen. It has it's own set of scripts concerning Xen.  I went through the OP's output in his post and am looking into it.  I've done Xen, but not on a UFI machine and not with recent Linux kernels. Xen used to have certain issues were the Xen part of the Grub scripts, would not place the Xen kernel as the first boot option... but those scripts have since been updated for recent versions of Grub.

To the OP-- I gave up on using Xen >> and went with Ubuntu Server with KMS. What are you looking for in your hypersvisor? And why go with a Hypervisor server as part of a multi-boot system? 

My next queston is on the Windows 10 side. For that part, just select the Wndows Recovery that grubs finds. That is the instance of Win10. << But on that, you know that it is not really going to be completely free right? (meaning that it's going to want to see a previous M$ license to verify that something was previously paid for... for the final version to be authenticated, for the free "upgrade").

If your answer is that you want to use it as a test bench to run test virtuals, then I understand your efforts. That is what 3 of my 14 here servers are dedicated to (testing problems and code on virtuals). If you are rather having your virtuals do something business-wise or fulltime, then you are on the causing yourself extra work. (<-- If interested, ask me what is a lot less work and makes more sense resource-wise...)

I heard Windows 10, Ubuntu, Xen... but did not hear a specific mention of "Ubuntu Server." What edition of Ubuntu is this on? Did you know that running a graphics version on a Xen server confuses it's process scheduling right? If running and testing virtuals were your priority, I would have heard Ubuntu server and the Windows Server (2016) tech-preview.

I'm following this thread and will try to jump in when I can.

---

