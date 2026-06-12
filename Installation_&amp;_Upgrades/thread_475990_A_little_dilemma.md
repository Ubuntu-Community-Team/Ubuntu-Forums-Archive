---
title: "A little dilemma?"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by Opeth115 on 2007-06-16
ok well my ubuntu install is installed and running perfectly but i have a massive amount of space to the LEFT of my home partition, when i say big i mean 248 gigs lol... i wuold really like to add that to my home partition without loosing all of my data on my home partition is there anyway i can do this?

---

### Post by yabbadabbadont on 2007-06-16
Create a new partition using the free space.  Mount it and copy all your data to it, including your current home directory.  Edit your /etc/fstab and change  the current "home" entry so that it points to the new partition.  Reboot to verify that it works.  Download a live CD that includes gparted  (you can get one on the gparted website) and boot with it.  Remove your old home partition so that you now have free space to the right of your new home.  Resize your new home partition to use this space you have just created.

---

### Post by Pumalite on 2007-06-16
> **Opeth115 said:**
> ok well my ubuntu install is installed and running perfectly but i have a massive amount of space to the LEFT of my home partition, when i say big i mean 248 gigs lol... i wuold really like to add that to my home partition without loosing all of my data on my home partition is there anyway i can do this?

We need a little more info. At the terminal: fdisk -l Post the output. As root: 'blkid' Post that. Also type: cat /etc/fstab Post that too.

---

### Post by Opeth115 on 2007-06-16
ok well i went to do that but now i can't stay logged in... an error message comes up saying that my session hasn't lsted longer then 10 seconds with this output:

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "matt"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/matt-room:/tmp/.ICE-unix/31051
/home/matt/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
/home/matt/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/matt/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
Initializing gnome-mount extension
/home/matt/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
/home/matt/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
/home/matt/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
/home/matt/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
/home/matt/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
/home/matt/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/firefox.desktop
LOADED : /home/matt/.local/share/applications/gconf-editor.desktop
LOADED : /usr/share/applications/gaim.desktop
LOADED : /usr/share/applications/emerald-theme-manager.desktop
LOADED : /usr/share/applications/gimp-2.2.desktop
LOADED : /usr/share/applications/inkscape.desktop
LOADED : /usr/share/applications/banshee.desktop
LOADED : /usr/share/applications/vlc.desktop
LOADED : /usr/share/applications/kde/k3b.desktop
LOADED : /usr/share/applications/synaptic.desktop
LOADED : /usr/share/applications/nautilus-computer.desktop
*** glibc detected *** /usr/bin/gnome-session: free(): invalid pointer: 0x082da970 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76137cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7616e30]
/usr/lib/libICE.so.6(_IceFreeConnection+0xde)[0xb7e9c08e]
/usr/lib/libICE.so.6(IceCloseConnection+0xb9)[0xb7e9c1a9]
/usr/lib/libgnomeui-2.so.0[0xb7eed698]
/usr/lib/libglib-2.0.so.0[0xb774d40d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7723df2]
/usr/lib/libglib-2.0.so.0[0xb7726dcf]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb7727335]
/usr/bin/gnome-session[0x8055789]
/usr/lib/libglib-2.0.so.0[0xb774d40d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7723df2]
/usr/lib/libglib-2.0.so.0[0xb7726dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7727179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c5b044]
/usr/bin/gnome-session(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75c1ebc]
/usr/bin/gnome-session[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:01 411        /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:01 411        /usr/bin/gnome-session
08069000-08314000 rw-p 08069000 00:00 0          [heap]
b3600000-b3621000 rw-p b3600000 00:00 0 
b3621000-b3700000 ---p b3621000 00:00 0 
b3744000-b374f000 r-xp 00000000 08:01 173206     /lib/libgcc_s.so.1
b374f000-b3750000 rw-p 0000a000 08:01 173206     /lib/libgcc_s.so.1
b3766000-b3769000 r-xp 00000000 08:01 6140       /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-ico.so
b3769000-b376a000 rw-p 00002000 08:01 6140       /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-ico.so
b376a000-b376b000 ---p b376a000 00:00 0 
b376b000-b3f6b000 rw-p b376b000 00:00 0 
b3f6b000-b3fe8000 r--p 00000000 08:01 39326      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b3fe8000-b3fea000 r-xp 00000000 08:01 16228      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b3fea000-b3feb000 rw-p 00001000 08:01 16228      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b3feb000-b3ff1000 r--s 00000000 08:01 158419     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b3ff1000-b3ff2000 r--s 00000000 08:01 159412     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b3ff2000-b3ff5000 r--s 00000000 08:01 159411     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b3ff5000-b3ff6000 r--s 00000000 08:01 159410     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b3ff6000-b3ff7000 r--s 00000000 08:01 159409     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b3ff7000-b3ffb000 r--s 00000000 08:01 158416     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b3ffb000-b3ffc000 r--s 00000000 08:01 159407     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b3ffc000-b3ffe000 r--s 00000000 08:01 159406     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b3ffe000-b4000000 r--s 00000000 08:01 159405     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b4000000-b4001000 r--s 00000000 08:01 159404     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b4001000-b4003000 r--s 00000000 08:01 159403     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b4003000-b4009000 r--s 00000000 08:01 159402     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4009000-b400b000 r--s 00000000 08:01 159401     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b400b000-b400d000 r--s 00000000 08:01 159400     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b400d000-b4015000 r--s 00000000 08:01 159399     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b4015000-b401b000 r--s 00000000 08:01 159398     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b401b000-b401c000 r--s 00000000 08:01 159397     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b401c000-b4033000 r--s 00000000 08:01 159473     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b4033000-b4035000 r--s 00000000 08:01 159396     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4035000-b403b000 r--s 00000000 08:01 159395     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b403b000-b403e000 r--s 00000000 08:01 159394     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b403e000-b4042000 r--s 00000000 08:01 158401     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4042000-b4044000 r--s 00000000 08:01 158733     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b4044000-b4045000 r--s 00000000 08:01 159437     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b4045000-b4046000 r--s 00000000 08:01 159436     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b4046000-b4047000 r--s 00000000 08:01 159435     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b4047000-b4048000 r--s 00000000 08:01 159434     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b4048000-b4049000 r--s 00000000 08:01 159470     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4049000-b404c000 r--s 00000000 08:01 159432     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b404c000-b4051000 r--s 00000000 08:01 159469     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b4051000-b4053000 r--s 00000000 08:01 159430     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b4053000-b4054000 r--s 00000000 08:01 159429     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b4054000-b4056000 r--s 00000000 08:01 159426     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4056000-b4057000 r--s 00000000 08:01 159427     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b4057000-b405c000 r--s 00000000 08:01 159421     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b405c000-b4060000 r--s 00000000 08:01 159425     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b4060000-b4062000 r--s 00000000 08:01 159438     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b4062000-b4065000 r--s 00000000 08:01 159424     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b4065000-b4066000 r--s 00000000 08:01 159423     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b4066000-b4068000 r--s 00000000 08:01 159422     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b4068000-b406c000 r--s 00000000 08:01 159467     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b406c000-b4072000 r--s 00000000 08:01 159420     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b4072000-b4073000 r--s 00000000 08:01 159419     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b4073000-b407b000 r--s 00000000 08:01 159418     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b407b000-b407d000 r--s 00000000 08:01 159466     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b407d000-b4080000 r--s 00000000 08:01 159416     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b4080000-b49fa000 r--p 00000000 08:01 60735      /usr/share/icons/hicolor/icon-theme.cache
b49fa000-b6431000 r--p 00000000 08:01 111943     /usr/share/icons/crystalsvg/icon-theme.cache
b6431000-b6ada000 r--p 00000000 08:01 622595     /usr/share/icons/gnome/icon-theme.cache
b6ada000-b6d31000 r--p 00000000 08:01 50143      /usr/share/icons/Tango/icon-theme.cache
b6d31000-b6d91000 rw-s 00000000 00:08 149192710  /SYSV00000000 (deleted)
b6d91000-b6d98000 r-xp 00000000 08:01 1381       /usr/lib/libfam.so.0.0.0
b6d98000-b6d99000 rw-p 00006000 08:01 1381       /usr/lib/libfam.so.0.0.0
b6d99000-b6d9f000 r-xp 00000000 08:01 173156     /lib/libacl.so.1.1.0
b6d9f000-b6da0000 rw-p 00005000 08:01 173156     /lib/libacl.so.1.1.0
b6da1000-b6da3000 r--s 00000000 08:01 159464     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6da3000-b6da5000 r--s 00000000 08:01 158729     /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6da5000-b6da9000 r--s 00000000 08:03 10421640   /home/matt/.fontconfig/73d5fe6ec61ef0ba9f7085baf56e4370-x86.cache-2
b6da9000-b6db0000 r-xp 00000000 08:01 6098       /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b6db0000-b6db1000 rw-p 00007000 08:01 6098       /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b6db1000-b6db5000 r-xp 00000000 08:01 6043       /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6db5000-b6db6000 rw-p 00003000 08:01 6043       /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6db6000-b6dc2000 r-xp 00000000 08:01 6241       /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6dc2000-b6dc3000 rw-p 0000b000 08:01 6241       /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6dc3000-b6dc4000 r-xp 00000000 08:01 171466     /usr/lib/gconv/ISO8859-1.so
b6dc4000-b6dc6000 rw-p 00000000 08:01 171466     /usr/lib/gconv/ISO8859-1.so
b6dc6000-b6e01000 r--p 00000000 08:01 7121       /usr/lib/locale/en_US.utf8/LC_CTYPE
b6e01000-b6ed8000 r--p 00000000 08:01 7120       /usr/lib/locale/en_US.utf8/LC_COLLATE
b6ed8000-b6ee1000 r-xp 00000000 08:01 176198     /lib/tls/i686/cmov/libnss_files-2.5.so
b6ee1000-b6ee3000 rw-p 00008000 08:01 176198     /lib/tls/i686/cmov/libnss_files-2.5.so
b6ee3000-b6eeb000 r-xp 00000000 08:01 176200     /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eeb000-b6eed000 rw-p 00007000 08:01 176200     /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eed000-b6ef4000 r-xp 00000000 08:01 176196     /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ef4000-b6ef6000 rw-p 00006000 08:01 176196     /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ef6000-b6ef9000 rw-p b6ef6000 00:00 0 
b6ef9000-b6f2f000 r-xp 00000000 08:01 173167     /lib/libsepol.so.1
b6f2f000-b6f30000 rw-p 00035000 08:01 173167     /lib/libsepol.so.1
b6f30000-b6f3a000 rw-p b6f30000 00:00 0 
b6f3a000-b6f3d000 r-xp 00000000 08:01 315        /usr/lib/libgpg-error.so.0.3.0
b6f3d000-b6f3e000 rw-p 00002000 08:01 315        /usr/lib/libgpg-error.so.0.3.0
b6f3e000-b6f8d000 r-xp 00000000 08:01 317        /usr/lib/libgcrypt.so.11.2.2
b6f8d000-b6f8f000 rw-p 0004e000 08:01 317        /usr/lib/libgcrypt.so.11.2.2
b6f8f000-b6f90000 rw-p b6f8f000 00:00 0 
b6f90000-b6fa4000 r-xp 00000000 08:01 322        /usr/lib/libtasn1.so.3.0.6
b6fa4000-b6fa5000 rw-p 00013000 08:01 322        /usr/lib/libtasn1.so.3.0.6
b6fa5000-b6fa7000 r-xp 00000000 08:01 176208     /lib/tls/i686/cmov/libutil-2.5.so
b6fa7000-b6fa9000 rw-p 00001000 08:01 176208     /lib/tls/i686/cmov/libutil-2.5.so
b6fa9000-b6fbd000 r-xp 00000000 08:01 173241     /lib/libselinux.so.1
b6fbd000-b6fbf000 rw-p 00013000 08:01 173241     /lib/libselinux.so.1
b6fbf000-b6fce000 r-xp 00000000 08:01 176204     /lib/tls/i686/cmov/libresolv-2.5.so
b6fce000-b6fd0000 rw-p 0000f000 08:01 176204     /lib/tls/i686/cmov/libresolv-2.5.so
b6fd0000-b6fd2000 rw-p b6fd0000 00:00 0 
b6fd2000-b6fe0000 r-xp 00000000 08:01 1377       /usr/lib/libavahi-client.so.3.2.2
b6fe0000-b6fe1000 rw-p 0000e000 08:01 1377       /usr/lib/libavahi-client.so.3.2.2
b6fe1000-b6fe2000 rw-p b6fe1000 00:00 0 
b6fe2000-b6fec000 r-xp 00000000 08:01 354        /usr/lib/libavahi-common.so.3.4.3
b6fec000-b6fed000 rw-p 00009000 08:01 354        /usr/lib/libavahi-common.so.3.4.3
b6fed000-b6fef000 r-xp 00000000 08:01 1375       /usr/lib/libavahi-glib.so.1.0.1
b6fef000-b6ff0000 rw-p 00001000 08:01 1375       /usr/lib/libavahi-glib.so.1.0.1
b6ff0000-b705a000 r-xp 00000000 08:01 1250       /usr/lib/libgnutls.so.13.0.9
b705a000-b7060000 rw-p 0006a000 08:01 1250       /usr/lib/libgnutls.so.13.0.9
b7060000-b7082000 r-xp 00000000 08:01 573447     /usr/lib/libpng12.so.0.15.0
b7082000-b7083000 rw-p 00021000 08:01 573447     /usr/lib/libpng12.so.0.15.0
b7083000-b70a1000 r-xp 00000000 08:01 936        /usr/lib/libexpat.so.1.0.0
b70a1000-b70a3000 rw-p 0001d000 08:01 936        /usr/lib/libexpat.so.1.0.0
b70a3000-b70a4000 rw-p b70a3000 00:00 0 
b70a4000-b710c000 r-xp 00000000 08:01 2637       /usr/lib/libfreetype.so.6.3.10
b710c000-b710f000 rw-p 00068000 08:01 2637       /usr/lib/libfreetype.so.6.3.10
b710f000-b7122000 r-xp 00000000 08:01 824        /usr/lib/libz.so.1.2.3
b7122000-b7123000 rw-p 00012000 08:01 824        /usr/lib/libz.so.1.2.3
b7123000-b7136000 r-xp 00000000 08:01 176195     /lib/tls/i686/cmov/libnsl-2.5.so
b7136000-b7138000 rw-p 00012000 08:01 176195     /lib/tls/i686/cmov/libnsl-2.5.so
b7138000-b713a000 rw-p b7138000 00:00 0 
b713a000-b713e000 r-xp 00000000 08:01 1280       /usr/lib/libORBitCosNaming-2.so.0.1.0
b713e000-b713f000 rw-p 00003000 08:01 1280       /usr/lib/libORBitCosNaming-2.so.0.1.0
b713f000-b7140000 rw-p b713f000 00:00 0 
b7140000-b7144000 r-xp 00000000 08:01 1305       /usr/lib/libXdmcp.so.6.0.0
b7144000-b7145000 rw-p 00003000 08:01 1305       /usr/lib/libXdmcp.so.6.0.0
b7145000-b7163000 r-xp 00000000 08:01 1788       /usr/lib/libjpeg.so.62.0.0
b7163000-b7164000 rw-p 0001d000 08:01 1788       /usr/lib/libjpeg.so.62.0.0
b7164000-b716c000 r-xp 00000000 08:01 361        /usr/lib/libstartup-notification-1.so.0.0.0
b716c000-b716d000 rw-p 00007000 08:01 361        /usr/lib/libstartup-notification-1.so.0.0.0
b716d000-b716e000 rw-p b716d000 00:00 0 
b716e000-b7175000 r-xp 00000000 08:01 176205     /lib/tls/i686/cmov/librt-2.5.so
b7175000-b7177000 rw-p 00006000 08:01 176205     /lib/tls/i686/cmov/librt-2.5.so
b7177000-b717b000 r-xp 00000000 08:01 2166       /usr/lib/libgthread-2.0.so.0.1200.11
b717b000-b717c000 rw-p 00003000 08:01 2166       /usr/lib/libgthread-2.0.so.0.1200.11
b717c000-b717e000 r-xp 00000000 08:01 176192     /lib/tls/i686/cmov/libdl-2.5.so
b717e000-b7180000 rw-p 00001000 08:01 176192     /lib/tls/i686/cmov/libdl-2.5.so
b7180000-b7182000 r-xp 00000000 08:01 2165       /usr/lib/libgmodule-2.0.so.0.1200.11
b7182000-b7183000 rw-p 00002000 08:01 2165       /usr/lib/libgmodule-2.0.so.0.1200.11
b7183000-b71d9000 r-xp 00000000 08:01 1075       /usr/lib/libgnomevfs-2.so.0.1800.1
b71d9000-b71dc000 rw-p 00055000 08:01 1075       /usr/lib/libgnomevfs-2.so.0.1800.1
b71dc000-b724a000 r-xp 00000000 08:01 1287       /usr/lib/libcairo.so.2.11.1
b724a000-b724c000 rw-p 0006d000 08:01 1287       /usr/lib/libcairo.so.2.11.1
b724c000-b724d000 rw-p b724c000 00:00 0 
b724d000-b7251000 r-xp 00000000 08:01 1311       /usr/lib/libXfixes.so.3.1.0
b7251000-b7252000 rw-p 00003000 08:01 1311       /usr/lib/libXfixes.so.3.1.0
b7252000-b725a000 r-xp 00000000 08:01 1301       /usr/lib/libXcursor.so.1.0.2
b725a000-b725b000 rw-p 00007000 08:01 1301       /usr/lib/libXcursor.so.1.0.2
b725b000-b7262000 r-xp 00000000 08:01 1317       /usr/lib/libXi.so.6.0.0
b7262000-b7263000 rw-p 00006000 08:01 1317       /usr/lib/libXi.so.6.0.0
b7263000-b7265000 r-xp 00000000 08:01 1319       /usr/lib/libXinerama.so.1.0.0
b7265000-b7266000 rw-p 00001000 08:01 1319       /usr/lib/libXinerama.so.1.0.0
b7266000-b726d000 r-xp 00000000 08:01 1331       /usr/lib/libXrender.so.1.3.0
b726d000-b726e000 rw-p 00006000 08:01 1331       /usr/lib/libXrender.so.1.3.0
b726e000-b727b000 r-xp 00000000 08:01 1309       /usr/lib/libXext.so.6.4.0
b727b000-b727c000 rw-p 0000d000 08:01 1309       /usr/lib/libXext.so.6.4.0
b727c000-b727d000 rw-p b727c000 00:00 0 
b727d000-b72a0000 r-xp 00000000 08:01 1499       /usr/lib/libfontconfig.so.1.2.0
b72a0000-b72a8000 rw-p 00023000 08:01 1499       /usr/lib/libfontconfig.so.1.2.0
b72a8000-b72af000 r-xp 00000000 08:01 2353       /usr/lib/libpangocairo-1.0.so.0.1600.2
b72af000-b72b0000 rw-p 00007000 08:01 2353       /usr/lib/libpangocairo-1.0.so.0.1600.2
b72b0000-b72da000 r-xp 00000000 08:01 2354       /usr/lib/libpangoft2-1.0.so.0.1600.2
b72da000-b72db000 rw-p 0002a000 08:01 2354       /usr/lib/libpangoft2-1.0.so.0.1600.2
b72db000-b72ef000 r-xp 00000000 08:01 1357       /usr/lib/libart_lgpl_2.so.2.3.17
b72ef000-b72f0000 rw-p 00013000 08:01 1357       /usr/lib/libart_lgpl_2.so.2.3.17
b72f0000-b72f7000 r-xp 00000000 08:01 173256     /lib/libpopt.so.0.0.0
b72f7000-b72f8000 rw-p 00006000 08:01 173256     /lib/libpopt.so.0.0.0
b72f8000-b7321000 r-xp 00000000 08:01 1631       /usr/lib/libgnomecanvas-2.so.0.1400.0
b7321000-b7322000 rw-p 00029000 08:01 1631       /usr/lib/libgnomecanvas-2.so.0.1400.0
b7322000-b7323000 rw-p b7322000 00:00 0 
b7323000-b737e000 r-xp 00000000 08:01 441        /usr/lib/libbonoboui-2.so.0.0.0
b737e000-b7381000 rw-p 0005a000 08:01 441        /usr/lib/libbonoboui-2.so.0.0.0
b7381000-b7498000 r-xp 00000000 08:01 2063       /usr/lib/libxml2.so.2.6.27
b7498000-b749e000 rw-p 00116000 08:01 2063       /usr/lib/libxml2.so.2.6.27
b749e000-b755e000 r-xp 00000000 08:01 621        /usr/lib/libasound.so.2.0.0
b755e000-b7563000 rw-p 000bf000 08:01 621        /usr/lib/libasound.so.2.0.0
b7563000-b7588000 r-xp 00000000 08:01 176193     /lib/tls/i686/cmov/libm-2.5.so
b7588000-b758a000 rw-p 00024000 08:01 176193     /lib/tls/i686/cmov/libm-2.5.so
b758a000-b75aa000 r-xp 00000000 08:01 1374       /usr/lib/libaudiofile.so.0.0.2
b75aa000-b75ac000 rw-p 00020000 08:01 1374       /usr/lib/libaudiofile.so.0.0.2
b75ac000-b76e7000 r-xp 00000000 08:01 176189     /lib/tls/i686/cmov/libc-2.5.so
b76e7000-b76e8000 r--p 0013b000 08:01 176189     /lib/tls/i686/cmov/libc-2.5.so
b76e8000-b76ea000 rw-p 0013c000 08:01 176189     /lib/tls/i686/cmov/libc-2.5.so
b76ea000-b76ee000 rw-p b76ea000 00:00 0 
b76ee000-b76f5000 r-xp 00000000 08:01 173252     /lib/libwrap.so.0.7.6
b76f5000-b76f6000 rw-p 00007000 08:01 173252     /lib/libwrap.so.0.7.6
b76f6000-b778a000 r-xp 00000000 08:01 57         /usr/lib/libglib-2.0.so.0.1200.11
b778a000-b778b000 rw-p 00093000 08:01 57         /usr/lib/libglib-2.0.so.0.1200.11
b778b000-b7797000 r-xp 00000000 08:01 1557       /usr/lib/libgnome-keyring.so.0.0.1
b7797000-b7798000 rw-p 0000b000 08:01 1557       /usr/lib/libgnome-keyring.so.0.0.1
b7798000-b77d1000 r-xp 00000000 08:01 2164       /usr/lib/libgobject-2.0.so.0.1200.11
b77d1000-b77d2000 rw-p 00039000 08:01 2164       /usr/lib/libgobject-2.0.so.0.1200.11
b77d2000-b7803000 r-xp 00000000 08:01 1426       /usr/lib/libdbus-1.so.3.2.0
b7803000-b7804000 rw-p 00031000 08:01 1426       /usr/lib/libdbus-1.so.3.2.0
b7804000-b781e000 r-xp 00000000 08:01 1437       /usr/lib/libdbus-glib-1.so.2.1.0
b781e000-b781f000 rw-p 0001a000 08:01 1437       /usr/lib/libdbus-glib-1.so.2.1.0
b781f000-b7820000 rw-p b781f000 00:00 0 
b7820000-b7833000 r-xp 00000000 08:01 176203     /lib/tls/i686/cmov/libpthread-2.5.so
b7833000-b7835000 rw-p 00013000 08:01 176203     /lib/tls/i686/cmov/libpthread-2.5.so
b7835000-b7837000 rw-p b7835000 00:00 0 
b7837000-b7880000 r-xp 00000000 08:01 1276       /usr/lib/libORBit-2.so.0.1.0
b7880000-b788a000 rw-p 00048000 08:01 1276       /usr/lib/libORBit-2.so.0.1.0
b788a000-b78b9000 r-xp 00000000 08:01 351        /usr/lib/libgconf-2.so.4.1.2
b78b9000-b78bc000 rw-p 0002e000 08:01 351        /usr/lib/libgconf-2.so.4.1.2
b78bc000-b78cf000 r-xp 00000000 08:01 2173       /usr/lib/libbonobo-activation.so.4.0.0
b78cf000-b78d1000 rw-p 00013000 08:01 2173       /usr/lib/libbonobo-activation.so.4.0.0
b78d1000-b7923000 r-xp 00000000 08:01 1367       /usr/lib/libbonobo-2.so.0.0.0
b7923000-b792d000 rw-p 00051000 08:01 1367       /usr/lib/libbonobo-2.so.0.0.0
b792d000-b792e000 rw-p b792d000 00:00 0 
b792e000-b7a1b000 r-xp 00000000 08:01 1508       /usr/lib/libX11.so.6.2.0
b7a1b000-b7a1f000 rw-p 000ed000 08:01 1508       /usr/lib/libX11.so.6.2.0
b7a1f000-b7a5b000 r-xp 00000000 08:01 2352       /usr/lib/libpango-1.0.so.0.1600.2
b7a5b000-b7a5d000 rw-p 0003b000 08:01 2352       /usr/lib/libpango-1.0.so.0.1600.2
b7a5d000-b7a62000 r-xp 00000000 08:01 1329       /usr/lib/libXrandr.so.2.1.0
b7a62000-b7a63000 rw-p 00005000 08:01 1329       /usr/lib/libXrandr.so.2.1.0
b7a63000-b7a79000 r-xp 00000000 08:01 2517       /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a79000-b7a7a000 rw-p 00015000 08:01 2517       /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a7a000-b7a93000 r-xp 00000000 08:01 1712       /usr/lib/libatk-1.0.so.0.1809.1
b7a93000-b7a95000 rw-p 00018000 08:01 1712       /usr/lib/libatk-1.0.so.0.1809.1
b7a95000-b7b18000 r-xp 00000000 08:01 2518       /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b18000-b7b1b000 rw-p 00083000 08:01 2518       /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b1b000-b7b1c000 rw-p b7b1b000 00:00 0 
b7b1c000-b7e6d000 r-xp 00000000 08:01 2519       /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e6d000-b7e73000 rw-p 00351000 08:01 2519       /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e73000-b7e74000 rw-p b7e73000 00:00 0 
b7e74000-b7e88000 r-xp 00000000 08:01 1648       /usr/lib/libgnome-2.so.0.1800.0
b7e88000-b7e89000 rw-p 00014000 08:01 1648       /usr/lib/libgnome-2.so.0.1800.0
b7e89000-b7e9e000 r-xp 00000000 08:01 1266       /usr/lib/libICE.so.6.3.0
b7e9e000-b7ea0000 rw-p 00014000 08:01 1266       /usr/lib/libICE.so.6.3.0
b7ea0000-b7ea1000 rw-p b7ea0000 00:00 0 
b7ea1000-b7ea9000 r-xp 00000000 08:01 1284       /usr/lib/libSM.so.6.0.0
b7ea9000-b7eaa000 rw-p 00007000 08:01 1284       /usr/lib/libSM.so.6.0.0
b7eaa000-b7f34000 r-xp 00000000 08:01 1647       /usr/lib/libgnomeui-2.so.0.1788.4
b7f34000-b7f38000 rw-p 00089000 08:01 1647       /usr/lib/libgnomeui-2.so.0.1788.4
b7f38000-b7f4c000 r-xp 00000000 08:01 2362       /usr/lib/libgnome-desktop-2.so.2.3.5
b7f4c000-b7f4d000 rw-p 00014000 08:01 2362       /usr/lib/libgnome-desktop-2.so.2.3.5
b7f4d000-b7f4e000 rw-p b7f4d000 00:00 0 
b7f4e000-b7f57000 r-xp 00000000 08:01 1484       /usr/lib/libesd.so.0.2.36
b7f57000-b7f58000 rw-p 00009000 08:01 1484       /usr/lib/libesd.so.0.2.36
b7f58000-b7f5a000 r-xp 00000000 08:01 1294       /usr/lib/libXau.so.6.0.0
b7f5a000-b7f5b000 rw-p 00001000 08:01 1294       /usr/lib/libXau.so.6.0.0
b7f5c000-b7f5f000 r-xp 00000000 08:01 173160     /lib/libattr.so.1.1.0
b7f5f000-b7f60000 rw-p 00002000 08:01 173160     /lib/libattr.so.1.1.0
b7f60000-b7f61000 r--p 00000000 08:01 7126       /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7f61000-b7f62000 r--p 00000000 08:01 7129       /usr/lib/locale/en_US.utf8/LC_TIME
b7f62000-b7f63000 r--p 00000000 08:01 7124       /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f63000-b7f64000 r--p 00000000 08:01 8588       /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f64000-b7f65000 r--p 00000000 08:01 7127       /usr/lib/locale/en_US.utf8/LC_PAPER
b7f65000-b7f66000 r--p 00000000 08:01 7125       /usr/lib/locale/en_US.utf8/LC_NAME
b7f66000-b7f67000 r--p 00000000 08:01 7119       /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f67000-b7f68000 r--p 00000000 08:01 7128       /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f68000-b7f69000 r--p 00000000 08:01 7123       /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f69000-b7f70000 r--s 00000000 08:01 171387     /usr/lib/gconv/gconv-modules.cache
b7f70000-b7f71000 r--p 00000000 08:01 7122       /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f71000-b7f73000 rw-p b7f71000 00:00 0 
b7f73000-b7f8c000 r-xp 00000000 08:01 173134     /lib/ld-2.5.so
b7f8c000-b7f8e000 rw-p 00019000 08:01 173134     /lib/ld-2.5.so
bfea9000-bfebe000 rw-p bfea9000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
LOADED : /usr/share/applications/nautilus-home.desktop

(gnome-power-manager:31155): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(Banshee:31138): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
/home/matt/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant

(update-notifier:31141): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.


---

### Post by Pumalite on 2007-06-16
> **Opeth115 said:**
> ok well i went to do that but now i can't stay logged in... an error message comes up saying that my session hasn't lsted longer then 10 seconds with this output:

What is your hardware? Motherboard, graphics card, chipset, kind of drives, what else do you have installed, what kind of partitioning did you do, and is Ubuntu sharing space with another OS, and if so, which one?

---

### Post by Opeth115 on 2007-06-17
Ok well here's my hardware u requested:

Motherboard:  Intel DP965LT
Graphics Card: NVIDIA geforce 7600
Chipset: Intel Core 2 Duo

And Ubuntu is the only operating system installed on this computer.

---

### Post by Opeth115 on 2007-06-17
here is the output of those commands anyway i can logg into gnome as another user.  I can also log into xfce or KDE of i want to just not gnome...

```
**matt@matt-room:~$ sudo fdisk -l**

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2           47892       48641     6024375    5  Extended
/dev/sda3           35057       47891   103097137+  83  Linux
/dev/sda5           47892       48641     6024343+  82  Linux swap / Solaris

Partition table entries are not in disk order
**matt@matt-room:~$ sudo blkid**
/dev/sda1: UUID="d8450be9-62ea-426d-9913-bf4acc45384b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="15c635aa-ccd9-4404-9751-1ad43d75a213" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="9e149e3b-abbe-432b-80d9-0894876c2d71" TYPE="swap" 
**matt@matt-room:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d8450be9-62ea-426d-9913-bf4acc45384b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=15c635aa-ccd9-4404-9751-1ad43d75a213 /home           ext3    defaults        0       2
# /dev/sda5
UUID=9e149e3b-abbe-432b-80d9-0894876c2d71 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
tmpfs           /dev/shm        tmpfs   defaults,ro     0       0

```

---

### Post by Opeth115 on 2007-06-17
anyone have any ideas to help me out?

---

### Post by Opeth115 on 2007-06-17
please anybody?

---

### Post by Opeth115 on 2007-06-17
ok well i fixed the problem of not being able to log in but i still would like to fill my home parition with the extra unused 250 gigs lol

---

### Post by Pumalite on 2007-06-17
> **Opeth115 said:**
> ok well i fixed the problem of not being able to log in but i still would like to fill my home parition with the extra unused 250 gigs lol

Start from scratch with Gparted. Make one BIG partition with the hard drive, formatted ext3. Then reinstall. During installation, choose Guided, Entire disk. Let Ubuntu then do the work.

---

### Post by Opeth115 on 2007-06-17
i don't want to loose all of my data though that's why i have a problem if i where to just reinstall ubuntu it would delete everything

---

### Post by Pumalite on 2007-06-17
> **Opeth115 said:**
> i don't want to loose all of my data though that's why i have a problem if i where to just reinstall ubuntu it would delete everything

Why do you call it '250GB Unused' then?

---

### Post by Opeth115 on 2007-06-17
maybe i worded it weird i meant that i have 250 gigs of unallocated space my home partition right now consists of a 100 gig partition but i want to add the 250 gig partition to that 90 gig one...

---

### Post by joe.turion64x2 on 2007-06-17
If you are talking about unallocated space there is nothing simpler to do. Are you the only user of that machine?

In my case I am and what I did in my laptop was the following:
1.- Create a new partition out of the free space (your 248GB).
2.- Edit /etc/fstab to mount that new partition in your own home folder.
3.- Change the necessary permissions to allow your user to fully read/write the new partition.

This way you will end with something like an 'external' drive mounted in your home folder. Do you need to reinstall? Save everything there and make sure you don't erase that partition, once the reinstall is done you can mount it again. It is also useful when you boot more than one OS (you can mount the drive wherever you want).

Just a suggestion.
Joe.

---

### Post by Opeth115 on 2007-06-17
> **joe.turion64x2 said:**
> If you are talking about unallocated space there is nothing simpler to do. Are you the only user of that machine?

In my case I am and what I did in my laptop was the following:
1.- Create a new partition out of the free space (your 248GB).
2.- Edit /etc/fstab to mount that new partition in your own home folder.
3.- Change the necessary permissions to allow your user to fully read/write the new partition.

This way you will end with something like an 'external' drive mounted in your home folder. Do you need to reinstall? Save everything there and make sure you don't erase that partition, once the reinstall is done you can mount it again. It is also useful when you boot more than one OS (you can mount the drive wherever you want).

Just a suggestion.
Joe.
yes i am the only owner of the machine could ug o and walk me through step by step please just so i do not ocmpletly screws omething up lol

---

### Post by joe.turion64x2 on 2007-06-17
Sure, I can guide you through this.
1.- Install Gparted (you can use Synaptic Package Manager for this).
2.- Run Gparted and create a new partition in the free space. Use the filesystem you prefer, reiser or ext3. Before closing Gparted write down the name of the partition (/dev/something).
3.- In the terminal run *sudo gedit /etc/fstab*.
4.- Add a new line which contains information about your partition. Supposing your user name is openth115, your new partition is /dev/sda2 and that you used the reiser filesystem, the new line shoud read like this:
```
/dev/sda2          /home/openth115/storage          reiserfs          defaults          0 0
```
where *storage* is a folder you created in your home partition before doing anything.
After that type
> sudo mount -a
with which your new partition should be mounted.

Joe.

---

### Post by joe.turion64x2 on 2007-06-17
When you have mounted your partition you may be unable to write on it. To fix this do the following:
1.- From within a terminal run *sudo nautilus*.
2.- Browse the filesystem until you find your folder (the one where you mounted the partition), **storage** in my example.
3.- Right click it and select properties.
4.- Go to the permissions tab and change them as necessary (make yourself the owner).
5.- Save changes and close.

That's all. Good luck.
Joe.

---

### Post by Opeth115 on 2007-06-17
> **joe.turion64x2 said:**
> Sure, I can guide you through this.
1.- Install Gparted (you can use Synaptic Package Manager for this).
2.- Run Gparted and create a new partition in the free space. Use the filesystem you prefer, reiser or ext3. Before closing Gparted write down the name of the partition (/dev/something).
3.- In the terminal run *sudo gedit /etc/fstab*.
4.- Add a new line which contains information about your partition. Supposing your user name is openth115, your new partition is /dev/sda2 and that you used the reiser filesystem, the new line shoud read like this:
```
/dev/sda2          /home/openth115/storage          reiserfs          defaults          0 0
```
where *storage* is a folder you created in your home partition before doing anything.
After that type

with which your new partition should be mounted.

Joe.
im srry lol but that kinda confused me ok so i created the new partition with the reiser filesystem my username is matt and the new parition is labled as dev/sda4.  what is the storage folder?  what i want to do is make my home folder consist of the unallocated space.

---

### Post by joe.turion64x2 on 2007-06-17
You can name the folder with any name you want, it is only to mount your new partition inside of your home folder. Just try to use something simple (without spaces or special characters).

---

### Post by Opeth115 on 2007-06-17
> **joe.turion64x2 said:**
> You can name the folder with any name you want, it is only to mount your new partition inside of your home folder. Just try to use something simple (without spaces or special characters).
is that the only way i can go about doing this? their is no way i can just add the space to my existing parition?

---

### Post by joe.turion64x2 on 2007-06-17
This is the easier way I know, and it is risk free. Adding the space to your partition would be much more complicated and errors there could end in data loss.

---

### Post by joe.turion64x2 on 2007-06-17
With this method you will have your extra space mounted in your personal home directory, thus at your complete disposal. With the benefit that you can easily backup your files there and unmount at will.

---

### Post by Opeth115 on 2007-06-17
> **joe.turion64x2 said:**
> With this method you will have your extra space mounted in your personal home directory, thus at your complete disposal. With the benefit that you can easily backup your files there and unmount at will.
could i do this move all of my files into that partition and then just expand the partition into the other one? Because otheriwse i have a 100 gig partition for no reason

---

### Post by joe.turion64x2 on 2007-06-17
Can you send me a Gparted screenshot of your drive? If you have more space to the right of your /home partition you can of course backup everything in the 248GB one and expand the other one.

---

### Post by Opeth115 on 2007-06-17
> **joe.turion64x2 said:**
> Can you send me a Gparted screenshot of your drive? If you have more space to the right of your /home partition you can of course backup everything in the 248GB one and expand the other one.
here's a screen shot of my gparted i don't knwo what i was thinking when i made my home partition like thisd lol but i want to make my home partition consist of the entire unallocated space...

[[IMG]http://img460.imageshack.us/img460/1949/screenshotip8.th.png[/IMG]](http://img460.imageshack.us/my.php?image=screenshotip8.png)

---

### Post by joe.turion64x2 on 2007-06-17
If I were you I would just mount the new partition (the big one) in your matt home folder (as explained) and move the big files there. As I told you earlier that way you will have ALL the space at your disposal (I don't understand your fear).
By the way, you have a really nice desktop.

Joe.

---

### Post by joe.turion64x2 on 2007-06-17
To merge the unused space with your current home partition you would need a third partition to hold your data. And perhaps you'll need another Linux (a live one) to perform the operation.

---

### Post by Opeth115 on 2007-06-17
> **joe.turion64x2 said:**
> To merge the unused space with your current home partition you would need a third partition to hold your data. And perhaps you'll need another Linux (a live one) to perform the operation.
ok i think i will try to do what u explained onlky i have work right now and won't be back untill 10:30-11 so if you could please stay updated with this thread to help me i would VERY much appreciate it.  if not thanks fo rall the help so far anyways it has been a lot lol.

---

### Post by joe.turion64x2 on 2007-06-17
Ok, see you later then.

---

### Post by Opeth115 on 2007-06-17
ok well thank you very much i got it up and working within minutes lol.  Also thanks for the comliment on the desktop i got the idea form the desktop thread.  i thank you very much for all the help and that walkthrough

---

### Post by joe.turion64x2 on 2007-06-17
You are welcome, I guess we are in the forums to help.

Joe.

---

### Post by poppers1957 on 2007-06-17
Download and burn a disk for partition utilities called gparted.   It is a live CD that runs at boot.  If you can just reinstall Ubuntu.  Use Gparted nice user interface to remove all partitions, make a root partition as ext3 or whatever you prefer.  Make a swap file, probably 1 or 2 gigs, whatever you prefer, and then reinstall.

---

