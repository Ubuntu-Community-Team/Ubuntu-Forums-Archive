---
title: "Strange thing with Ubuntu Pro ESM-INFR - no updates when enabled"
date: 2023-10-12
forum: Installation &amp; Upgrades
---

### Post by novasolnix on 2023-10-12
Hi

I have a strange problem with ubuntu pro
[INDENT]```
0,15:45:22,root@XXX:/var/lib/dpkg$ pro disable esm-infra
Updating package lists
0,15:53:48,root@XXX:/var/lib/dpkg$ pro status
SERVICE          ENTITLED  STATUS    DESCRIPTION
cc-eal           yes       disabled  Common Criteria EAL2 Provisioning Packages
cis              yes       disabled  Security compliance and audit tools
esm-infra        yes       disabled  Expanded Security Maintenance for Infrastructure
fips             yes       disabled  NIST-certified core packages
fips-updates     yes       disabled  NIST-certified core packages with priority security updates
livepatch        yes       enabled   Canonical Livepatch service

For a list of all Ubuntu Pro services, run 'pro status --all'
Enable services with: pro enable <service>

                Account: XXXXXXXX
           Subscription: Ubuntu Pro (Infra-only)
            Valid until: Sun Oct 13 01:59:59 2024 CEST
Technical support level: essential

127,15:54:01,root@XXX:/var/lib/dpkg$ apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following security updates require Ubuntu Pro with 'esm-infra' enabled:
  screen libpython3.6-minimal libnghttp2-14 libisccfg160 libcups2
  intel-microcode linux-headers-generic vim-common libcurl4 libldap-2.4-2
  openssl libdw1 libsystemd0 linux-image-generic python2.7-minimal libpam-cap
  libpython3.6-stdlib libelf1 binutils libirs160 bind9-host
  libavahi-common-data open-iscsi dnsutils libavahi-common3 python2.7
  libpython3.6 python3.6 open-vm-tools openssh-sftp-server gawk libisc169 udev
  bind9utils amd64-microcode openjdk-11-jre-headless libx11-6 python3-requests
  linux-signed-generic libudev1 libapparmor1 linux-cloud-tools-common
  python3.6-minimal binutils-x86-64-linux-gnu libtiff5 libisc-export169
  busybox-static libcap2 systemd-sysv libcap2-bin openjdk-11-jre
  libldap-common liblwres160 vim-runtime vim libpam-systemd systemd xxd
  openssh-server libx11-data openssh-client libdns-export1100 libnss-systemd
  bind9 binutils-common libbinutils libpython2.7-minimal vim-tiny apparmor
  libisccc160 linux-tools-common libssl1.1 libbind9-160 accountsservice
  libdns1100 libpython2.7-stdlib libavahi-client3 curl linux-generic
  libcurl3-gnutls libx11-xcb1 libaccountsservice0 busybox-initramfs
Learn more about Ubuntu Pro for 18.04 at [https://ubuntu.com/18-04](https://ubuntu.com/18-04)
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
0,15:54:06,root@XXX:/var/lib/dpkg$
0,15:54:06,root@XXXXX:/var/lib/dpkg$ pro enable esm-infra
One moment, checking your subscription first
Updating package lists
Ubuntu Pro: ESM Infra enabled
0,15:55:11,root@cphxbitbucket01.nix.novasol.com:/var/lib/dpkg$ pro status
SERVICE          ENTITLED  STATUS    DESCRIPTION
cc-eal           yes       disabled  Common Criteria EAL2 Provisioning Packages
cis              yes       disabled  Security compliance and audit tools
esm-infra        yes       enabled   Expanded Security Maintenance for Infrastructure
fips             yes       disabled  NIST-certified core packages
fips-updates     yes       disabled  NIST-certified core packages with priority security updates
livepatch        yes       enabled   Canonical Livepatch service

For a list of all Ubuntu Pro services, run 'pro status --all'
Enable services with: pro enable <service>

                Account: XXXX
           Subscription: Ubuntu Pro (Infra-only)
            Valid until: Sun Oct 13 01:59:59 2024 CEST
Technical support level: essential
0,15:55:19,root@xxxxxx:/var/lib/dpkg$ apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/INDENT]
```


So when Ubuntu pro esm-infra is disabled, it tells me there is lots of updates, but when I do enable the pro, it tells me there are none

Any thoughts?

/m

---

### Post by grahammechanical on 2023-10-12
My guess would be that you a seeing a list of all the packaged that would be upgraded (if necessary) if esm-infra w as enabled. But with esm-infra disabled these are the packages that will not be upgraded by the Ubuntu Pro arrangement.

Regards

---

### Post by MAFoElffen on 2023-10-12
Here is "my" laptop
```

mafoelffen@Mikes-ThinkPad-T520:~$ pro status
SERVICE          ENTITLED  STATUS    DESCRIPTION
anbox-cloud      yes       disabled  Scalable Android in the cloud
esm-apps         yes       enabled   Expanded Security Maintenance for Applications
esm-infra        yes       enabled   Expanded Security Maintenance for Infrastructure
livepatch        yes       enabled   Canonical Livepatch service
realtime-kernel  yes       disabled  Ubuntu kernel with PREEMPT_RT patches integrated

For a list of all Ubuntu Pro services, run 'pro status --all'
Enable services with: pro enable <service>

     Account: [ Retracked ]
Subscription: Ubuntu Pro - free personal subscription

```
In the following command, any that are in the list that are in bold, are packages that have aan avaiable update that is not applied yet...
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo ua security-status --esm-apps
[sudo] password for mafoelffen: 
2699 packages installed:
     545 packages from Ubuntu Universe/Multiverse repository

Universe/Multiverse packages are receiving security updates from
Ubuntu Pro with 'esm-apps' enabled until 2032. You have received 20 security
updates.

Run 'pro help esm-apps' to learn more

Installed packages with an esm-apps update applied:
gsasl-common imagemagick imagemagick-6-common imagemagick-6.q16 libavcodec58
libavdevice58 libavfilter7 libavformat58 libavutil56 libgsasl7
libimage-magick-perl libimage-magick-q16-perl libmagick++-6.q16-8
libmagickcore-6.q16-6 libmagickcore-6.q16-6-extra libmagickwand-6.q16-6
libopenexr25 libpostproc55 libswresample3 libswscale5

Further installed packages covered by esm-apps:
accountsservice-ubuntu-schemas acpi acpitool activity-log-manager adb
adwaita-icon-theme-full alien android-libadb android-libbase
android-libboringssl android-libcrypto-utils android-libcutils android-liblog
android-sdk-platform-tools-common aspell-es at augeas-lenses bamfdaemon brasero
brasero-cdrkit brasero-common bsdmainutils ca-certificates-mono cdrdao
checkpolicy chrome-gnome-shell cli-common clinfo cockpit cockpit-bridge
cockpit-machines cockpit-networkmanager cockpit-packagekit cockpit-storaged
cockpit-system cockpit-ws cpp-9 dclock dconf-editor debian-keyring driverctl
dvdauthor edid-decode exfatprogs extlinux f2fs-tools fig2dev freerdp2-x11 g++-9
g++-9-multilib gcc-9 gcc-9-base gcc-9-doc gcc-9-locales gcc-9-multilib
gir1.2-appindicator3-0.1 gir1.2-gtk-vnc-2.0 gir1.2-libosinfo-1.0
gir1.2-libvirt-glib-1.0 gir1.2-spiceclientglib-2.0 gir1.2-spiceclientgtk-3.0
gmtp gnome-icon-theme gnome-screensaver gnome-session
gnome-shell-extension-prefs gnome-shell-extensions gnome-tweaks growisofs
grub-emu gsfonts gstreamer1.0-libav gstreamer1.0-plugins-ugly guestfish
guestfs-tools guestmount guile-3.0-libs hfsprogs hwinfo i965-va-driver icoutils
indicator-applet indicator-application indicator-appmenu indicator-bluetooth
indicator-common indicator-datetime indicator-keyboard indicator-messages
indicator-power indicator-printers indicator-session indicator-sound inkscape
intel-media-va-driver inxi jayatana kded5 keditbookmarks kio kpackagelauncherqml
kpackagetool5 krdc kwayland-data kwayland-integration ldmtool lib2geom1.1.0
lib32asan5 lib32gcc-9-dev lib32stdc++-9-dev liba52-0.7.4 libaacs0
libaccounts-glib0 libafflib0v5 libaom3 libasan5 libass9 libaugeas0 libbamf3-2
libbdplus0 libbfio1 libblockdev-mdraid2 libbluray2 libbrasero-media3-1 libbs2b0
libburn4 libbytesize-common libbytesize1 libcanberra-gtk0 libchromaprint1
libcodec2-1.0 libconfig9 libdav1d5 libdbusmenu-qt5-2 libdc1394-25 libde265-0
libdouble-conversion3 libdvdread8 libegl1-mesa libept1.6.0 libewf2 libexecs0
libfcitx-config4 libfcitx-gclient1 libfcitx-utils0 libffi7 libflite1
libfsverity0 libfuse2 libgcc-9-dev libgdiplus libgdk-pixbuf2.0-0
libgeonames-common libgeonames0 libgl1-mesa-glx libglib2.0-cil libgme0
libgnome-panel0 libgovirt-common libgovirt2 libgsl27 libgslcblas0 libgsm1
libgtk-vnc-2.0-0 libgtk2.0-cil libguestfs-hfsplus libguestfs-perl
libguestfs-reiserfs libguestfs-tools libguestfs-xfs libguestfs0 libgvnc-1.0-0
libhd21 libheif1 libhivex0 libid3tag0 libido3-0.1-0 libigdgmm12 libilmbase25
libindicator3-7 libisoburn1 libisofs6 libjpeg62 libjte2 libjxr-tools libjxr0
libkf5archive5 libkf5auth-data libkf5auth5 libkf5authcore5 libkf5bookmarks-data
libkf5bookmarks5 libkf5codecs-data libkf5codecs5 libkf5completion-data
libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5
libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5
libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin
libkf5dbusaddons-data libkf5dbusaddons5 libkf5declarative-data
libkf5declarative5 libkf5dnssd-data libkf5dnssd5 libkf5doctools5
libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5
libkf5globalaccelprivate5 libkf5guiaddons-bin libkf5guiaddons-data
libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin
libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data
libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5 libkf5kcmutils-data
libkf5kcmutils5 libkf5kiocore5 libkf5kiogui5 libkf5kiontlm5 libkf5kiowidgets5
libkf5notifications-data libkf5notifications5 libkf5notifyconfig-data
libkf5notifyconfig5 libkf5package-data libkf5package5 libkf5parts-data
libkf5parts-plugins libkf5parts5 libkf5quickaddons5 libkf5service-bin
libkf5service-data libkf5service5 libkf5solid5 libkf5solid5-data
libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data
libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5
libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5
libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin libkf5xmlgui-data
libkf5xmlgui5 libkwalletbackend5-5 libldm-1.0-0 liblightdm-gobject-1-0
liblilv-0-0 liblinear4 liblqr-1-0 liblxc-common liblxc1 libmailutils8 libmd4c0
libmfx1 libmono-addins-gui0.2-cil libmono-addins0.2-cil
libmono-btls-interface4.0-cil libmono-cairo4.0-cil libmono-corlib4.5-cil
libmono-corlib4.5-dll libmono-i18n-west4.0-cil libmono-i18n4.0-cil
libmono-posix4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil
libmono-system-configuration4.0-cil libmono-system-core4.0-cil
libmono-system-drawing4.0-cil libmono-system-numerics4.0-cil
libmono-system-security4.0-cil libmono-system-xml4.0-cil libmono-system4.0-cil
libmpeg2-4 libmysofa1 libncurses5 libnetpbm10 libnorm1 libntlm0 libopenal-data
libopenal1 libopencore-amrnb0 libopencore-amrwb0 libopenmpt0 libosinfo-1.0-0
libpam-cgfs libpgm-5.3-0 libphodav-2.0-0 libphodav-2.0-common libpocketsphinx3
libpolkit-qt5-1-1 libpotrace0 libpwquality-tools libqt5core5a libqt5dbus5
libqt5gui5 libqt5network5 libqt5printsupport5 libqt5qml5 libqt5qmlmodels5
libqt5qmlworkerscript5 libqt5quick5 libqt5quickcontrols2-5
libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5svg5 libqt5texttospeech5
libqt5waylandclient5 libqt5waylandcompositor5 libqt5widgets5 libqt5x11extras5
libqt5xml5 librpm9 librpmbuild9 librpmio9 librpmsign9 librubberband2
libsdl1.2debian libserd-0-0 libshine3 libsidplay1v5 libsndio7.0 libsord-0-0
libsox-fmt-alsa libsox-fmt-base libsox3 libsphinxbase3
libspice-client-glib-2.0-8 libspice-client-gtk-3.0-5 libsratom-0-0
libsrt1.4-gnutls libstdc++-9-dev libstdc++-9-doc libsys-virt-perl libtinfo5
libtsk19 libudfread0 libunity-control-center1 libunity-gtk2-parser0
libunity-gtk3-parser0 libunity-settings-daemon1 libva-drm2 libva-wayland2
libva-x11-2 libva2 libvde0 libvdeplug2 libvhdi1 libvidstab1.1
libvirt-daemon-driver-lxc libvirt-daemon-driver-storage-rbd
libvirt-daemon-driver-storage-zfs libvirt-dbus libvirt-glib-1.0-0
libvirt-glib-1.0-data libvmdk1 libwim15 libwin-hivex-perl libwmf-bin
libwxbase3.0-0v5 libwxgtk3.0-gtk3-0v5 libx264-163 libx265-199 libx32asan5
libx32gcc-9-dev libx32stdc++-9-dev libx86-1 libx86emu3 libxapian30
libxml-xpath-perl libxvidcore4 libyara8 libzeitgeist-2.0-0 libzimg2 libzmq5
libzvbi-common libzvbi0 lightdm lm-sensors lsb lsb-core lsb-printing
lsb-security lua-lpeg lxc-utils lxcfs lynx lynx-common mailutils
mailutils-common mbuffer menu mesa-utils mesa-utils-bin mesa-va-drivers
mono-4.0-gac mono-gac mono-runtime mono-runtime-common mono-runtime-sgen mutter
nautilus-extension-brasero ncal netpbm nmap nmap-common nvtop ocl-icd-libopencl1
openjdk-8-jre openjdk-8-jre-headless osinfo-db p7zip p7zip-full pavucontrol
pinta pocketsphinx-en-us policycoreutils policycoreutils-dev
policycoreutils-python-utils policykit-1-gnome python3-audit python3-libxml2
python3-pip python3-pip-whl python3-scour python3-selinux python3-semanage
python3-sepolgen python3-sepolicy python3-setools python3-setuptools-whl
python3-venv python3-wheel python3.10-venv qemu qemu-efi
qml-module-qtgraphicaleffects qml-module-qtquick-controls2
qml-module-qtquick-layouts qml-module-qtquick-templates2
qml-module-qtquick-window2 qml-module-qtquick2 qt5-gtk-platformtheme
qtspeech5-speechd-plugin qttranslations5-l10n qtwayland5 read-edid rpi-imager
rpm rpm-common rpm2cpio scrcpy scrcpy-server scrub selinux-policy-dev
selinux-utils semodule-utils setools sharutils sleuthkit sonnet-plugins sox
speedtest-cli spice-client-glib-usb-acl-helper supermin synaptic syslinux
systemd-bootchart traceroute tree ubuntu-touch-sounds ubuntu-wallpapers-focal
uidmap uml-utilities unity-control-center unity-greeter unity-gtk-module-common
unity-gtk2-module unity-gtk3-module unity-settings-daemon
unity-settings-daemon-schemas va-driver-all vainfo vde-switch vde-wirefilter
vde2 vdeplug vinagre virt-manager virt-p2v virt-viewer virtinst vorbis-tools
wimtools wodim xkeycaps xorgxrdp xorriso xrdp yad zeitgeist-core zfs-dkms

For example, run:
    apt-cache show libgsasl7
to learn more about that package.

```

---

