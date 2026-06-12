---
title: "Help gnome can't stay loaded?"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by Opeth115 on 2007-04-01
Ok well i really didn't know where to put this so move it please if it's in the wrong spot.

well i finally got ubuntu installed and everything to my liking but now when i load inti gnome it gives me this error message:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "matt"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/matt-desktop:/tmp/.ICE-unix/6296
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/matt/.themes/SnowIsh-Theme.tar.gz_FILES/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Starting gdesklets-daemon...

Connecting to daemon [###          ]exec: 2: /usr/share/system-config-printer/applet.py: not found
*** glibc detected *** /usr/bin/gnome-session: free(): invalid pointer: 0x082fa980 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75f87cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb75fbe30]
/usr/lib/libICE.so.6(_IceFreeConnection+0xde)[0xb7e7b08e]
/usr/lib/libICE.so.6(IceCloseConnection+0xb9)[0xb7e7b1a9]
/usr/lib/libgnomeui-2.so.0[0xb7ecc698]
/usr/lib/libglib-2.0.so.0[0xb773240d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7708df2]
/usr/lib/libglib-2.0.so.0[0xb770bdcf]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb770c335]
/usr/bin/gnome-session[0x8055789]
/usr/lib/libglib-2.0.so.0[0xb773240d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7708df2]
/usr/lib/libglib-2.0.so.0[0xb770bdcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb770c179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c3a044]
/usr/bin/gnome-session(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75a6ebc]
/usr/bin/gnome-session[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:01 41469311   /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:01 41469311   /usr/bin/gnome-session
08069000-08319000 rw-p 08069000 00:00 0          [heap]
b3000000-b3021000 rw-p b3000000 00:00 0 
b3021000-b3100000 ---p b3021000 00:00 0 
b3155000-b3160000 r-xp 00000000 08:01 12648521   /lib/libgcc_s.so.1
b3160000-b3161000 rw-p 0000a000 08:01 12648521   /lib/libgcc_s.so.1
b317a000-b317b000 ---p b317a000 00:00 0 
b317b000-b397b000 rw-p b317b000 00:00 0 
b397b000-b39f8000 r--p 00000000 08:01 41683237   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b39f8000-b39fa000 r-xp 00000000 08:01 41599865   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b39fa000-b39fb000 rw-p 00001000 08:01 41599865   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b39fb000-b3a01000 r--s 00000000 08:01 31245281   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b3a01000-b3a02000 r--s 00000000 08:01 31245978   /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b3a02000-b3a05000 r--s 00000000 08:01 31245977   /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b3a05000-b3a06000 r--s 00000000 08:01 31245976   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b3a06000-b3a07000 r--s 00000000 08:01 31245975   /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b3a07000-b3a0b000 r--s 00000000 08:01 31245276   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b3a0b000-b3a0e000 r--s 00000000 08:01 31244670   /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
b3a0e000-b3a0f000 r--s 00000000 08:01 31245973   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b3a0f000-b3a11000 r--s 00000000 08:01 31245972   /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b3a11000-b3a13000 r--s 00000000 08:01 31245971   /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b3a13000-b3a14000 r--s 00000000 08:01 31245970   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b3a14000-b3a16000 r--s 00000000 08:01 31245969   /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b3a16000-b3a1c000 r--s 00000000 08:01 31245968   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b3a1c000-b3a1e000 r--s 00000000 08:01 31245967   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b3a1e000-b3a20000 r--s 00000000 08:01 31245966   /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b3a20000-b3a28000 r--s 00000000 08:01 31245965   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b3a28000-b3a2e000 r--s 00000000 08:01 31245964   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b3a2e000-b3a2f000 r--s 00000000 08:01 31245963   /var/cache/fontconfig/9451a55048e8dbe8633e64d34165fdf2-x86.cache-2
b3a2f000-b3a30000 r--s 00000000 08:01 31245962   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b3a30000-b3a47000 r--s 00000000 08:01 31245961   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b3a47000-b3a49000 r--s 00000000 08:01 31245960   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b3a49000-b3a4f000 r--s 00000000 08:01 31245959   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b3a4f000-b3a53000 r--s 00000000 08:01 31245958   /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b3a53000-b3a56000 r--s 00000000 08:01 31245957   /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b3a56000-b3a5a000 r--s 00000000 08:01 31245333   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b3a5a000-b3a5c000 r--s 00000000 08:01 31244694   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b3a5c000-b3a5d000 r--s 00000000 08:01 31245818   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b3a5d000-b3a5e000 r--s 00000000 08:01 31246006   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b3a5e000-b3a5f000 r--s 00000000 08:01 31244975   /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b3a5f000-b3a60000 r--s 00000000 08:01 31246004   /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b3a60000-b3a61000 r--s 00000000 08:01 31246003   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b3a61000-b3a64000 r--s 00000000 08:01 31246002   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b3a64000-b3a67000 r--s 00000000 08:01 31246001   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b3a67000-b3a70000 r--s 00000000 08:01 31246000   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b3a70000-b3a72000 r--s 00000000 08:01 31245999   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b3a72000-b3a73000 r--s 00000000 08:01 31245998   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b3a73000-b3a75000 r--s 00000000 08:01 31245997   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b3a75000-b3a76000 r--s 00000000 08:01 31245996   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b3a76000-b3a7b000 r--s 00000000 08:01 31245995   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b3a7b000-b3a7f000 r--s 00000000 08:01 31245994   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b3a7f000-b3a84000 r--s 00000000 08:01 31244388   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b3a84000-b3a87000 r--s 00000000 08:01 31245992   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b3a87000-b3a88000 r--s 00000000 08:01 31245991   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b3a88000-b3a89000 r--s 00000000 08:01 31245990   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b3a89000-b3a8b000 r--s 00000000 08:01 31245989   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b3a8b000-b3a91000 r--s 00000000 08:01 31245988   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b3a91000-b3a9b000 r--s 00000000 08:01 31245985   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b3a9b000-b4952000 r--p 00000000 08:01 41779740   /usr/share/icons/hicolor/icon-theme.cache
b4952000-b659b000 r--p 00000000 08:01 42009404   /usr/share/icons/crystalsvg/icon-theme.cache
b659b000-b6c44000 r--p 00000000 08:01 41779748   /usr/share/icons/gnome/icon-theme.cache
b6c44000-b6c5f000 r-xp 00000000 08:01 41517122   /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6c5f000-b6c60000 rw-p 0001b000 08:01 41517122   /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6c60000-b6cc0000 rw-s 00000000 00:08 25165828   /SYSV00000000 (deleted)
b6cc0000-b6d5a000 rw-p b6cc0000 00:00 0 
b6d5a000-b6d61000 r-xp 00000000 08:01 41469373   /usr/lib/libfam.so.0.0.0
b6d61000-b6d62000 rw-p 00006000 08:01 41469373   /usr/lib/libfam.so.0.0.0
b6d62000-b6d68000 r-xp 00000000 08:01 12648475   /lib/libacl.so.1.1.0
b6d68000-b6d69000 rw-p 00005000 08:01 12648475   /lib/libacl.so.1.1.0
b6d69000-b6d6f000 r--s 00000000 08:01 31245987   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b6d6f000-b6d74000 r--s 00000000 08:01 31245984   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6d74000-b6d78000 r--s 00000000 08:01 31245983   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6d78000-b6d7d000 r--s 00000000 08:01 31245812   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6d7d000-b6d81000 r-xp 00000000 08:01 41517421   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6d81000-b6d82000 rw-p 00003000 08:01 41517421   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6d82000-b6d8e000 r-xp 00000000 08:01 41517425   /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6d8e000-b6d8f000 rw-p 0000b000 08:01 41517425   /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6d8f000-b6d90000 r-xp 00000000 08:01 41485486   /usr/lib/gconv/ISO8859-1.so
b6d90000-b6d92000 rw-p 00000000 08:01 41485486   /usr/lib/gconv/ISO8859-1.so
b6d92000-b6dcd000 r--p 00000000 08:01 41518401   /usr/lib/locale/en_US.utf8/LC_CTYPE
b6dcd000-b6ea4000 r--p 00000000 08:01 41518400   /usr/lib/locale/en_US.utf8/LC_COLLATE
b6ea4000-b6ead000 r-xp 00000000 08:01 12682212   /lib/tls/i686/cmov/libnss_files-2.5.so
b6ead000-b6eaf000 rw-p 00008000 08:01 12682212   /lib/tls/i686/cmov/libnss_files-2.5.so
b6eaf000-b6eb7000 r-xp 00000000 08:01 12682214   /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eb7000-b6eb9000 rw-p 00007000 08:01 12682214   /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eb9000-b6ec0000 r-xp 00000000 08:01 12682210   /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ec0000-b6ec2000 rw-p 00006000 08:01 12682210   /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ec2000-b6ec6000 rw-p b6ec2000 00:00 0 
b6ec6000-b6efc000 r-xp 00000000 08:01 12648523   /lib/libsepol.so.1
b6efc000-b6efd000 rw-p 00035000 08:01 12648523   /lib/libsepol.so.1
b6efd000-b6f07000 rw-p b6efd000 00:00 0 
b6f07000-b6f0a000 r-xp 00000000 08:01 41469073   /usr/lib/libgpg-error.so.0.3.0
b6f0a000-b6f0b000 rw-p 00002000 08:01 41469073   /usr/lib/libgpg-error.so.0.3.0
b6f0b000-b6f5a000 r-xp 00000000 08:01 41469226   /usr/lib/libgcrypt.so.11.2.2
b6f5a000-b6f5c000 rw-p 0004e000 08:01 41469226   /usr/lib/libgcrypt.so.11.2.2
b6f5c000-b6f70000 r-xp 00000000 08:01 41469253   /usr/lib/libtasn1.so.3.0.6
b6f70000-b6f71000 rw-p 00013000 08:01 41469253   /usr/lib/libtasn1.so.3.0.6
b6f71000-b6f75000 r-xp 00000000 08:01 41469181   /usr/lib/libXdmcp.so.6.0.0
b6f75000-b6f76000 rw-p 00003000 08:01 41469181   /usr/lib/libXdmcp.so.6.0.0
b6f76000-b6f77000 rw-p b6f76000 00:00 0 
b6f77000-b6f79000 r-xp 00000000 08:01 12682222   /lib/tls/i686/cmov/libutil-2.5.so
b6f79000-b6f7b000 rw-p 00001000 08:01 12682222   /lib/tls/i686/cmov/libutil-2.5.so
b6f7b000-b6f8f000 r-xp 00000000 08:01 12648565   /lib/libselinux.so.1
b6f8f000-b6f91000 rw-p 00013000 08:01 12648565   /lib/libselinux.so.1
b6f91000-b6fa0000 r-xp 00000000 08:01 12682218   /lib/tls/i686/cmov/libresolv-2.5.so
b6fa0000-b6fa2000 rw-p 0000f000 08:01 12682218   /lib/tls/i686/cmov/libresolv-2.5.so
b6fa2000-b6fa4000 rw-p b6fa2000 00:00 0 
b6fa4000-b6fb2000 r-xp 00000000 08:01 41468804   /usr/lib/libavahi-client.so.3.2.2
b6fb2000-b6fb3000 rw-p 0000e000 08:01 41468804   /usr/lib/libavahi-client.so.3.2.2
b6fb3000-b6fbd000 r-xp 00000000 08:01 41467946   /usr/lib/libavahi-common.so.3.4.3
b6fbd000-b6fbe000 rw-p 00009000 08:01 41467946   /usr/lib/libavahi-common.so.3.4.3
b6fbe000-b6fbf000 rw-p b6fbe000 00:00 0 
b6fbf000-b6fc1000 r-xp 00000000 08:01 41469309   /usr/lib/libavahi-glib.so.1.0.1
b6fc1000-b6fc2000 rw-p 00001000 08:01 41469309   /usr/lib/libavahi-glib.so.1.0.1
b6fc2000-b702c000 r-xp 00000000 08:01 41469278   /usr/lib/libgnutls.so.13.0.9
b702c000-b7032000 rw-p 0006a000 08:01 41469278   /usr/lib/libgnutls.so.13.0.9
b7032000-b7054000 r-xp 00000000 08:01 41469797   /usr/lib/libpng12.so.0.15.0
b7054000-b7055000 rw-p 00021000 08:01 41469797   /usr/lib/libpng12.so.0.15.0
b7055000-b7073000 r-xp 00000000 08:01 41469528   /usr/lib/libexpat.so.1.0.0
b7073000-b7075000 rw-p 0001d000 08:01 41469528   /usr/lib/libexpat.so.1.0.0
b7075000-b70dc000 r-xp 00000000 08:01 41469385   /usr/lib/libfreetype.so.6.3.10
b70dc000-b70df000 rw-p 00067000 08:01 41469385   /usr/lib/libfreetype.so.6.3.10
b70df000-b70e0000 rw-p b70df000 00:00 0 
b70e0000-b70f3000 r-xp 00000000 08:01 41467935   /usr/lib/libz.so.1.2.3
b70f3000-b70f4000 rw-p 00012000 08:01 41467935   /usr/lib/libz.so.1.2.3
b70f4000-b7107000 r-xp 00000000 08:01 12682209   /lib/tls/i686/cmov/libnsl-2.5.so
b7107000-b7109000 rw-p 00012000 08:01 12682209   /lib/tls/i686/cmov/libnsl-2.5.so
b7109000-b710b000 rw-p b7109000 00:00 0 
b710b000-b710f000 r-xp 00000000 08:01 41469156   /usr/lib/libORBitCosNaming-2.so.0.1.0
b710f000-b7110000 rw-p 00003000 08:01 41469156   /usr/lib/libORBitCosNaming-2.so.0.1.0
b7110000-b7127000 r-xp 00000000 08:01 41469815   /usr/lib/libxcb.so.1.0.0
b7127000-b7128000 rw-p 00016000 08:01 41469815   /usr/lib/libxcb.so.1.0.0
b7128000-b7129000 rw-p b7128000 00:00 0 
b7129000-b712a000 r-xp 00000000 08:01 41469836   /usr/lib/libxcb-xlib.so.0.0.0
b712a000-b712b000 rw-p 00000000 08:01 41469836   /usr/lib/libxcb-xlib.so.0.0.0
b712b000-b7149000 r-xp 00000000 08:01 41469664   /usr/lib/libjpeg.so.62.0.0
b7149000-b714a000 rw-p 0001d000 08:01 41469664   /usr/lib/libjpeg.so.62.0.0
b714a000-b7152000 r-xp 00000000 08:01 41468121   /usr/lib/libstartup-notification-1.so.0.0.0
b7152000-b7153000 rw-p 00007000 08:01 41468121   /usr/lib/libstartup-notification-1.so.0.0.0
b7153000-b7154000 rw-p b7153000 00:00 0 
b7154000-b715b000 r-xp 00000000 08:01 12682219   /lib/tls/i686/cmov/librt-2.5.so
b715b000-b715d000 rw-p 00006000 08:01 12682219   /lib/tls/i686/cmov/librt-2.5.so
b715d000-b7161000 r-xp 00000000 08:01 41468198   /usr/lib/libgthread-2.0.so.0.1200.11
b7161000-b7162000 rw-p 00003000 08:01 41468198   /usr/lib/libgthread-2.0.so.0.1200.11
b7162000-b7164000 r-xp 00000000 08:01 12682204   /lib/tls/i686/cmov/libdl-2.5.so
b7164000-b7166000 rw-p 00001000 08:01 12682204   /lib/tls/i686/cmov/libdl-2.5.so
b7166000-b7168000 r-xp 00000000 08:01 41468197   /usr/lib/libgmodule-2.0.so.0.1200.11
b7168000-b7169000 rw-p 00002000 08:01 41468197   /usr/lib/libgmodule-2.0.so.0.1200.11
b7169000-b71be000 r-xp 00000000 08:01 41468065   /usr/lib/libgnomevfs-2.so.0.1799.1
b71be000-b71c1000 rw-p 00055000 08:01 41468065   /usr/lib/libgnomevfs-2.so.0.1799.1
b71c1000-b722f000 r-xp 00000000 08:01 41468463   /usr/lib/libcairo.so.2.11.1
b722f000-b7231000 rw-p 0006d000 08:01 41468463   /usr/lib/libcairo.so.2.11.1
b7231000-b7232000 rw-p b7231000 00:00 0 
b7232000-b7236000 r-xp 00000000 08:01 41469187   /usr/lib/libXfixes.so.3.1.0
b7236000-b7237000 rw-p 00003000 08:01 41469187   /usr/lib/libXfixes.so.3.1.0
b7237000-b723f000 r-xp 00000000 08:01 41469177   /usr/lib/libXcursor.so.1.0.2
b723f000-b7240000 rw-p 00007000 08:01 41469177   /usr/lib/libXcursor.so.1.0.2
b7240000-b7247000 r-xp 00000000 08:01 41469193   /usr/lib/libXi.so.6.0.0
b7247000-b7248000 rw-p 00006000 08:01 41469193   /usr/lib/libXi.so.6.0.0
b7248000-b724a000 r-xp 00000000 08:01 41469195   /usr/lib/libXinerama.so.1.0.0
b724a000-b724b000 rw-p 00001000 08:01 41469195   /usr/lib/libXinerama.so.1.0.0
b724b000-b7252000 r-xp 00000000 08:01 41469207   /usr/lib/libXrender.so.1.3.0
b7252000-b7253000 rw-p 00006000 08:01 41469207   /usr/lib/libXrender.so.1.3.0
b7253000-b7260000 r-xp 00000000 08:01 41469185   /usr/lib/libXext.so.6.4.0
b7260000-b7261000 rw-p 0000d000 08:01 41469185   /usr/lib/libXext.so.6.4.0
b7261000-b7262000 rw-p b7261000 00:00 0 
b7262000-b7285000 r-xp 00000000 08:01 41469375   /usr/lib/libfontconfig.so.1.2.0
b7285000-b728d000 rw-p 00023000 08:01 41469375   /usr/lib/libfontconfig.so.1.2.0
b728d000-b7294000 r-xp 00000000 08:01 41469588   /usr/lib/libpangocairo-1.0.so.0.1600.1
b7294000-b7295000 rw-p 00007000 08:01 41469588   /usr/lib/libpangocairo-1.0.so.0.1600.1
b7295000-b72bf000 r-xp 00000000 08:01 41469628   /usr/lib/libpangoft2-1.0.so.0.1600.1
b72bf000-b72c0000 rw-p 0002a000 08:01 41469628   /usr/lib/libpangoft2-1.0.so.0.1600.1
b72c0000-b72d4000 r-xp 00000000 08:01 41469233   /usr/lib/libart_lgpl_2.so.2.3.17
b72d4000-b72d5000 rw-p 00013000 08:01 41469233   /usr/lib/libart_lgpl_2.so.2.3.17
b72d5000-b72dc000 r-xp 00000000 08:01 12648484   /lib/libpopt.so.0.0.0
b72dc000-b72dd000 rw-p 00006000 08:01 12648484   /lib/libpopt.so.0.0.0
b72dd000-b7306000 r-xp 00000000 08:01 41469507   /usr/lib/libgnomecanvas-2.so.0.1400.0
b7306000-b7307000 rw-p 00029000 08:01 41469507   /usr/lib/libgnomecanvas-2.so.0.1400.0
b7307000-b7308000 rw-p b7307000 00:00 0 
b7308000-b7363000 r-xp 00000000 08:01 41469433   /usr/lib/libbonoboui-2.so.0.0.0
b7363000-b7366000 rw-p 0005a000 08:01 41469433   /usr/lib/libbonoboui-2.so.0.0.0
b7366000-b747d000 r-xp 00000000 08:01 41469939   /usr/lib/libxml2.so.2.6.27
b747d000-b7483000 rw-p 00116000 08:01 41469939   /usr/lib/libxml2.so.2.6.27
b7483000-b7543000 r-xp 00000000 08:01 41469214   /usr/lib/libasound.so.2.0.0
b7543000-b7548000 rw-p 000bf000 08:01 41469214   /usr/lib/libasound.so.2.0.0
b7548000-b756d000 r-xp 00000000 08:01 12682205   /lib/tls/i686/cmov/libm-2.5.so
b756d000-b756f000 rw-p 00024000 08:01 12682205   /lib/tls/i686/cmov/libm-2.5.so
b756f000-b758f000 r-xp 00000000 08:01 41469250   /usr/lib/libaudiofile.so.0.0.2
b758f000-b7591000 rw-p 00020000 08:01 41469250   /usr/lib/libaudiofile.so.0.0.2
b7591000-b76cc000 r-xp 00000000 08:01 12682201   /lib/tls/i686/cmov/libc-2.5.so
b76cc000-b76cd000 r--p 0013b000 08:01 12682201   /lib/tls/i686/cmov/libc-2.5.so
b76cd000-b76cf000 rw-p 0013c000 08:01 12682201   /lib/tls/i686/cmov/libc-2.5.so
b76cf000-b76d3000 rw-p b76cf000 00:00 0 
b76d3000-b76da000 r-xp 00000000 08:01 12648554   /lib/libwrap.so.0.7.6
b76da000-b76db000 rw-p 00007000 08:01 12648554   /lib/libwrap.so.0.7.6
b76db000-b776f000 r-xp 00000000 08:01 41468194   /usr/lib/libglib-2.0.so.0.1200.11
b776f000-b7770000 rw-p 00093000 08:01 41468194   /usr/lib/libglib-2.0.so.0.1200.11
b7770000-b777c000 r-xp 00000000 08:01 41469272   /usr/lib/libgnome-keyring.so.0.0.1
b777c000-b777d000 rw-p 0000b000 08:01 41469272   /usr/lib/libgnome-keyring.so.0.0.1
b777d000-b77b6000 r-xp 00000000 08:01 41468196   /usr/lib/libgobject-2.0.so.0.1200.11
b77b6000-b77b7000 rw-p 00039000 08:01 41468196   /usr/lib/libgobject-2.0.so.0.1200.11
b77b7000-b77e8000 r-xp 00000000 08:01 41468960   /usr/lib/libdbus-1.so.3.2.0
b77e8000-b77e9000 rw-p 00031000 08:01 41468960   /usr/lib/libdbus-1.so.3.2.0
b77e9000-b7803000 r-xp 00000000 08:01 41469313   /usr/lib/libdbus-glib-1.so.2.1.0
b7803000-b7804000 rw-p 0001a000 08:01 41469313   /usr/lib/libdbus-glib-1.so.2.1.0
b7804000-b7805000 rw-p b7804000 00:00 0 
b7805000-b7818000 r-xp 00000000 08:01 12682217   /lib/tls/i686/cmov/libpthread-2.5.so
b7818000-b781a000 rw-p 00013000 08:01 12682217   /lib/tls/i686/cmov/libpthread-2.5.so
b781a000-b781c000 rw-p b781a000 00:00 0 
b781c000-b7865000 r-xp 00000000 08:01 41469152   /usr/lib/libORBit-2.so.0.1.0
b7865000-b786f000 rw-p 00048000 08:01 41469152   /usr/lib/libORBit-2.so.0.1.0
b786f000-b789e000 r-xp 00000000 08:01 41468227   /usr/lib/libgconf-2.so.4.1.2
b789e000-b78a1000 rw-p 0002e000 08:01 41468227   /usr/lib/libgconf-2.so.4.1.2
b78a1000-b78b4000 r-xp 00000000 08:01 41468901   /usr/lib/libbonobo-activation.so.4.0.0
b78b4000-b78b6000 rw-p 00013000 08:01 41468901   /usr/lib/libbonobo-activation.so.4.0.0
b78b6000-b7908000 r-xp 00000000 08:01 41468895   /usr/lib/libbonobo-2.so.0.0.0
b7908000-b7912000 rw-p 00051000 08:01 41468895   /usr/lib/libbonobo-2.so.0.0.0
b7912000-b7913000 rw-p b7912000 00:00 0 
b7913000-b79fa000 r-xp 00000000 08:01 41469164   /usr/lib/libX11.so.6.2.0
b79fa000-b79fe000 rw-p 000e7000 08:01 41469164   /usr/lib/libX11.so.6.2.0
b79fe000-b7a3a000 r-xp 00000000 08:01 41469490   /usr/lib/libpango-1.0.so.0.1600.1
b7a3a000-b7a3c000 rw-p 0003b000 08:01 41469490   /usr/lib/libpango-1.0.so.0.1600.1
b7a3c000-b7a41000 r-xp 00000000 08:01 41469205   /usr/lib/libXrandr.so.2.1.0
b7a41000-b7a42000 rw-p 00005000 08:01 41469205   /usr/lib/libXrandr.so.2.1.0
b7a42000-b7a58000 r-xp 00000000 08:01 41468407   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a58000-b7a59000 rw-p 00015000 08:01 41468407   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a59000-b7a72000 r-xp 00000000 08:01 41468633   /usr/lib/libatk-1.0.so.0.1809.1
b7a72000-b7a74000 rw-p 00018000 08:01 41468633   /usr/lib/libatk-1.0.so.0.1809.1
b7a74000-b7af7000 r-xp 00000000 08:01 41468408   /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7af7000-b7afa000 rw-p 00083000 08:01 41468408   /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7afa000-b7afb000 rw-p b7afa000 00:00 0 
b7afb000-b7e4c000 r-xp 00000000 08:01 41469788   /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e4c000-b7e52000 rw-p 00351000 08:01 41469788   /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e52000-b7e53000 rw-p b7e52000 00:00 0 
b7e53000-b7e67000 r-xp 00000000 08:01 41468951   /usr/lib/libgnome-2.so.0.1800.0
b7e67000-b7e68000 rw-p 00014000 08:01 41468951   /usr/lib/libgnome-2.so.0.1800.0
b7e68000-b7e7d000 r-xp 00000000 08:01 41469142   /usr/lib/libICE.so.6.3.0
b7e7d000-b7e7f000 rw-p 00014000 08:01 41469142   /usr/lib/libICE.so.6.3.0
b7e7f000-b7e80000 rw-p b7e7f000 00:00 0 
b7e80000-b7e88000 r-xp 00000000 08:01 41469160   /usr/lib/libSM.so.6.0.0
b7e88000-b7e89000 rw-p 00007000 08:01 41469160   /usr/lib/libSM.so.6.0.0
b7e89000-b7f13000 r-xp 00000000 08:01 41469523   /usr/lib/libgnomeui-2.so.0.1788.4
b7f13000-b7f17000 rw-p 00089000 08:01 41469523   /usr/lib/libgnomeui-2.so.0.1788.4
b7f17000-b7f2b000 r-xp 00000000 08:01 41469874   /usr/lib/libgnome-desktop-2.so.2.3.4
b7f2b000-b7f2c000 rw-p 00014000 08:01 41469874   /usr/lib/libgnome-desktop-2.so.2.3.4
b7f2c000-b7f2d000 rw-p b7f2c000 00:00 0 
b7f2d000-b7f36000 r-xp 00000000 08:01 41469360   /usr/lib/libesd.so.0.2.36
b7f36000-b7f37000 rw-p 00009000 08:01 41469360   /usr/lib/libesd.so.0.2.36
b7f37000-b7f39000 r-xp 00000000 08:01 41469170   /usr/lib/libXau.so.6.0.0
b7f39000-b7f3a000 rw-p 00001000 08:01 41469170   /usr/lib/libXau.so.6.0.0
b7f3b000-b7f3c000 r--s 00000000 08:01 31245986   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7f3c000-b7f3e000 r--s 00000000 08:01 31244690   /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b7f3e000-b7f41000 r-xp 00000000 08:01 12648479   /lib/libattr.so.1.1.0
b7f41000-b7f42000 rw-p 00002000 08:01 12648479   /lib/libattr.so.1.1.0
b7f42000-b7f43000 r--p 00000000 08:01 41518406   /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7f43000-b7f44000 r--p 00000000 08:01 41518409   /usr/lib/locale/en_US.utf8/LC_TIME
b7f44000-b7f45000 r--p 00000000 08:01 41518404   /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f45000-b7f46000 r--p 00000000 08:01 41533498   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f46000-b7f47000 r--p 00000000 08:01 41518407   /usr/lib/locale/en_US.utf8/LC_PAPER
b7f47000-b7f48000 r--p 00000000 08:01 41518405   /usr/lib/locale/en_US.utf8/LC_NAME
b7f48000-b7f49000 r--p 00000000 08:01 41518399   /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f49000-b7f4a000 r--p 00000000 08:01 41518408   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f4a000-b7f4b000 r--p 00000000 08:01 41518403   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f4b000-b7f52000 r--s 00000000 08:01 41485545   /usr/lib/gconv/gconv-modules.cache
b7f52000-b7f53000 r--p 00000000 08:01 41518402   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f53000-b7f55000 rw-p b7f53000 00:00 0 
b7f55000-b7f6e000 r-xp 00000000 08:01 12648586   /lib/ld-2.5.so
b7f6e000-b7f70000 rw-p 00019000 08:01 12648586   /lib/ld-2.5.so
bf898000-bf8ad000 rw-p bf898000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

Connecting to daemon [ ###         ]Initializing gnome-mount extension

(evolution-alarm-notify:6395): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

i can load KDE fluxbox all of that it's just gnome that does it any ideas on what's going wrong?  I can still do anything i need to but it has that error message up and beryl dosn't load.

---

### Post by pradeepadapa on 2007-04-01
first of all r u trying to install gnome or what is ur default desktop GNOME or KDE, u hav to be a little detail so that we know the details t help solve ur problem..

---

### Post by Opeth115 on 2007-04-01
ok well my default desktop is gnome but i also have kde xfce and fluxbox installed.l  all of them load except for gnome.  Gnome is my default and i would really like to get back to it.

---

### Post by pradeepadapa on 2007-04-01
why dont u reinstall gnome using the following command from KDE or XFCE desktop

> sudo aptitude install ubuntu-desktop

---

### Post by pradeepadapa on 2007-04-01
there is also another solution, why dont u try this command

in console (ctrl+alt+f2)

> sudo dpkg-reconfigure xserver-xorg

u can also try the above command frm the KONSOLE in KDE

---

### Post by Opeth115 on 2007-04-01
ok if im to reinstall the ubuntu desktop it wouldn't get rid of my files right?  Like if i were to

sudo apt-get remove ubuntu-desktop

then 

sudo apt-get install ubuntu-desktop i wouldn't loose anything it would just reinstall gnome?

---

### Post by pradeepadapa on 2007-04-01
i myself hasnt tested it to reinstall gnome bec i dont hav any problems as of now but why not try it or this

> sudo dpkg-reconfigure xserver-xorg

---

### Post by Opeth115 on 2007-04-01
i just tried both with no success any other ideas?

---

### Post by Rui Pais on 2007-04-01
> **Opeth115 said:**
> ok if im to reinstall the ubuntu desktop it wouldn't get rid of my files right?  Like if i were to

sudo apt-get remove ubuntu-desktop

then 

sudo apt-get install ubuntu-desktop i wouldn't loose anything it would just reinstall gnome?

You should not get none of your personal (at your home) files deleted.
But should be:
```
sudo aptitude reinstall ubuntu-desktop
```

Your problem don't seem related with the X server... i doubt that reconfigure it would do any difference.

Can you log in in Gnome with other user?

---

### Post by Opeth115 on 2007-04-01
ok well i tried creating a new user and logging into gnome and it worked perfectly  so that would mean that it's just realted to my user right?  also sudo aptitude reinstall ubuntu-desktop did not work

---

### Post by Rui Pais on 2007-04-01
> **Opeth115 said:**
> ok well i tried creating a new user and logging into gnome and it worked perfectly  so that would mean that it's just realted to my user right?  also sudo aptitude reinstall ubuntu-desktop did not work

Reinstalling gnoem didn't work cause your problem is just a borked configuration (you're lucky)

Just login as your normal user on a console (Ctrl+Alt+F1) 
and do:
```
mkdir tmps
```
and then
```
mv .gnome* tmps/
mv .gconf* tmps/
```
logout, Ctrl+Alt+F7 and try to login to Gnome again.

---

### Post by Opeth115 on 2007-04-01
thank you very much that worked great but now beryl is weird lol...  all the effects work but i get no window borders.  any ideas?  i deleted .beryl and it still does the same thing.

---

### Post by Opeth115 on 2007-04-01
thats what the terminal spits out:

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32

```

---

### Post by Rui Pais on 2007-04-01
hi again,
glad that you have your gnome back.

Sorry that beryl is still broken. Regretabilly i don't know about it (don't use it) so can give much help on that. Maybe wait for someone else to give some ideas. Or make a new post or change the title of this one to something like 'beryl broke after gnome recuperation' or something...

Just a clue, a shoot in the dark. Your error log ends with references to glxfbconfig... 
maybe the sudo dpkg-reconfigure xserver-xorg have broken glx or something related with the X server... 

Have you tried to restart X? does your glxgears work?

---

