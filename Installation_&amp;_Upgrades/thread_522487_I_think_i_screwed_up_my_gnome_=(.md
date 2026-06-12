---
title: "I think i screwed up my gnome =("
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by Opeth115 on 2007-08-10
everytime i try to log into gnome i get this error

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "satan"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/God:/tmp/.ICE-unix/22525
Initializing gnome-mount extension
*** glibc detected *** x-session-manager: malloc(): memory corruption (fast): 0x0834d980 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x425046fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0x4250560e]
/usr/lib/libSM.so.6(_SmsProcessMessage+0xe75)[0x42970755]
/usr/lib/libICE.so.6(IceProcessMessages+0x311)[0x42962ef1]
/usr/lib/libgnomeui-2.so.0[0x41b97605]
/usr/lib/libglib-2.0.so.0[0x428a740d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0x4287ddf2]
/usr/lib/libglib-2.0.so.0[0x42880dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0x42881179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0x42b94044]
x-session-manager(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0x424b1ebc]
x-session-manager[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:01 13085474   /usr/bin/gnome-session
08068000-0806c000 rw-p 00020000 08:01 13085474   /usr/bin/gnome-session
0806c000-0838c000 rw-p 0806c000 00:00 0          [heap]
41a6e000-41a87000 r-xp 00000000 08:01 34752044   /lib/ld-2.5.so
41a87000-41a89000 rw-p 00019000 08:01 34752044   /lib/ld-2.5.so
41a8b000-41a92000 r-xp 00000000 08:01 34752057   /lib/libpopt.so.0.0.0
41a92000-41a93000 rw-p 00006000 08:01 34752057   /lib/libpopt.so.0.0.0
41a95000-41aa8000 r-xp 00000000 08:01 13089220   /usr/lib/libbonobo-activation.so.4.0.0
41aa8000-41aaa000 rw-p 00013000 08:01 13089220   /usr/lib/libbonobo-activation.so.4.0.0
41aac000-41ab0000 r-xp 00000000 08:01 13089219   /usr/lib/libORBitCosNaming-2.so.0.1.0
41ab0000-41ab1000 rw-p 00003000 08:01 13089219   /usr/lib/libORBitCosNaming-2.so.0.1.0
41ab3000-41b05000 r-xp 00000000 08:01 13089221   /usr/lib/libbonobo-2.so.0.0.0
41b05000-41b0f000 rw-p 00051000 08:01 13089221   /usr/lib/libbonobo-2.so.0.0.0
41b11000-41b3a000 r-xp 00000000 08:01 13089211   /usr/lib/libgnomecanvas-2.so.0.1400.0
41b3a000-41b3b000 rw-p 00029000 08:01 13089211   /usr/lib/libgnomecanvas-2.so.0.1400.0
41b3d000-41b51000 r-xp 00000000 08:01 13089225   /usr/lib/libgnome-2.so.0.1800.0
41b51000-41b52000 rw-p 00014000 08:01 13089225   /usr/lib/libgnome-2.so.0.1800.0
41b54000-41bde000 r-xp 00000000 08:01 13089228   /usr/lib/libgnomeui-2.so.0.1788.4
41bde000-41be2000 rw-p 00089000 08:01 13089228   /usr/lib/libgnomeui-2.so.0.1788.4
41be4000-41c3f000 r-xp 00000000 08:01 13089226   /usr/lib/libbonoboui-2.so.0.0.0
41c3f000-41c42000 rw-p 0005a000 08:01 13089226   /usr/lib/libbonoboui-2.so.0.0.0
41c44000-41c50000 r-xp 00000000 08:01 13089227   /usr/lib/libgnome-keyring.so.0.0.1
41c50000-41c51000 rw-p 0000b000 08:01 13089227   /usr/lib/libgnome-keyring.so.0.0.1
41c53000-41c5a000 r-xp 00000000 08:01 34751902   /lib/libwrap.so.0.7.6
41c5a000-41c5b000 rw-p 00007000 08:01 34751902   /lib/libwrap.so.0.7.6
41c91000-41ca5000 r-xp 00000000 08:01 13089235   /usr/lib/libgnome-desktop-2.so.2.3.5
41ca5000-41ca6000 rw-p 00014000 08:01 13089235   /usr/lib/libgnome-desktop-2.so.2.3.5
4249c000-425d7000 r-xp 00000000 08:01 34752045   /lib/tls/i686/cmov/libc-2.5.so
425d7000-425d8000 r--p 0013b000 08:01 34752045   /lib/tls/i686/cmov/libc-2.5.so
425d8000-425da000 rw-p 0013c000 08:01 34752045   /lib/tls/i686/cmov/libc-2.5.so
425da000-425dd000 rw-p 425da000 00:00 0 
425df000-425e1000 r-xp 00000000 08:01 34752046   /lib/tls/i686/cmov/libdl-2.5.so
425e1000-425e3000 rw-p 00001000 08:01 34752046   /lib/tls/i686/cmov/libdl-2.5.so
425e5000-4260a000 r-xp 00000000 08:01 34752047   /lib/tls/i686/cmov/libm-2.5.so
4260a000-4260c000 rw-p 00024000 08:01 34752047   /lib/tls/i686/cmov/libm-2.5.so
4260e000-42621000 r-xp 00000000 08:01 34752048   /lib/tls/i686/cmov/libpthread-2.5.so
42621000-42623000 rw-p 00013000 08:01 34752048   /lib/tls/i686/cmov/libpthread-2.5.so
42623000-42625000 rw-p 42623000 00:00 0 
42627000-4263a000 r-xp 00000000 08:01 13089167   /usr/lib/libz.so.1.2.3
4263a000-4263b000 rw-p 00012000 08:01 13089167   /usr/lib/libz.so.1.2.3
4263d000-42725000 r-xp 00000000 08:01 13089176   /usr/lib/libX11.so.6.2.0
42725000-42728000 rw-p 000e7000 08:01 13089176   /usr/lib/libX11.so.6.2.0
42728000-42729000 rw-p 42728000 00:00 0 
4272b000-4272d000 r-xp 00000000 08:01 13089172   /usr/lib/libXau.so.6.0.0
4272d000-4272e000 rw-p 00001000 08:01 13089172   /usr/lib/libXau.so.6.0.0
42730000-42731000 r-xp 00000000 08:01 13089175   /usr/lib/libxcb-xlib.so.0.0.0
42731000-42732000 rw-p 00000000 08:01 13089175   /usr/lib/libxcb-xlib.so.0.0.0
42734000-4274b000 r-xp 00000000 08:01 13089174   /usr/lib/libxcb.so.1.0.0
4274b000-4274c000 rw-p 00016000 08:01 13089174   /usr/lib/libxcb.so.1.0.0
4274e000-42752000 r-xp 00000000 08:01 13089173   /usr/lib/libXdmcp.so.6.0.0
42752000-42753000 rw-p 00003000 08:01 13089173   /usr/lib/libXdmcp.so.6.0.0
42755000-42762000 r-xp 00000000 08:01 13089181   /usr/lib/libXext.so.6.4.0
42762000-42763000 rw-p 0000d000 08:01 13089181   /usr/lib/libXext.so.6.4.0
42765000-42783000 r-xp 00000000 08:01 13089169   /usr/lib/libexpat.so.1.0.0
42783000-42785000 rw-p 0001d000 08:01 13089169   /usr/lib/libexpat.so.1.0.0
42787000-427a9000 r-xp 00000000 08:01 13089171   /usr/lib/libpng12.so.0.15.0
427a9000-427aa000 rw-p 00021000 08:01 13089171   /usr/lib/libpng12.so.0.15.0
427ac000-427cf000 r-xp 00000000 08:01 13089170   /usr/lib/libfontconfig.so.1.2.0
427cf000-427d7000 rw-p 00023000 08:01 13089170   /usr/lib/libfontconfig.so.1.2.0
427d9000-42841000 r-xp 00000000 08:01 13089168   /usr/lib/libfreetype.so.6.3.10
42841000-42844000 rw-p 00068000 08:01 13089168   /usr/lib/libfreetype.so.6.3.10
42846000-4284d000 r-xp 00000000 08:01 13089177   /usr/lib/libXrender.so.1.3.0
4284d000-4284e000 rw-p 00006000 08:01 13089177   /usr/lib/libXrender.so.1.3.0
42850000-428e4000 r-xp 00000000 08:01 13089162   /usr/lib/libglib-2.0.so.0.1200.11
428e4000-428e5000 rw-p 00093000 08:01 13089162   /usr/lib/libglib-2.0.so.0.1200.11
428e7000-428eb000 r-xp 00000000 08:01 13089185   /usr/lib/libXfixes.so.3.1.0
428eb000-428ec000 rw-p 00003000 08:01 13089185   /usr/lib/libXfixes.so.3.1.0
428ee000-428f0000 r-xp 00000000 08:01 13089182   /usr/lib/libXinerama.so.1.0.0
428f0000-428f1000 rw-p 00001000 08:01 13089182   /usr/lib/libXinerama.so.1.0.0
428f3000-428fa000 r-xp 00000000 08:01 13089183   /usr/lib/libXi.so.6.0.0
428fa000-428fb000 rw-p 00006000 08:01 13089183   /usr/lib/libXi.so.6.0.0
428fd000-42905000 r-xp 00000000 08:01 13089186   /usr/lib/libXcursor.so.1.0.2
42905000-42906000 rw-p 00007000 08:01 13089186   /usr/lib/libXcursor.so.1.0.2
42908000-4290d000 r-xp 00000000 08:01 13089184   /usr/lib/libXrandr.so.2.1.0
4290d000-4290e000 rw-p 00005000 08:01 13089184   /usr/lib/libXrandr.so.2.1.0
42910000-42949000 r-xp 00000000 08:01 13089164   /usr/lib/libgobject-2.0.so.0.1200.11
42949000-4294a000 rw-p 00039000 08:01 13089164   /usr/lib/libgobject-2.0.so.0.1200.11
4294c000-4294e000 r-xp 00000000 08:01 13089163   /usr/lib/libgmodule-2.0.so.0.1200.11
4294e000-4294f000 rw-p 00002000 08:01 13089163   /usr/lib/libgmodule-2.0.so.0.1200.11
42951000-42966000 r-xp 00000000 08:01 13089190   /usr/lib/libICE.so.6.3.0
42966000-42968000 rw-p 00014000 08:01 13089190   /usr/lib/libICE.so.6.3.0
42968000-42969000 rw-p 42968000 00:00 0 
4296b000-42973000 r-xp 00000000 08:01 13089191   /usr/lib/libSM.so.6.0.0
42973000-42974000 rw-p 00007000 08:01 13089191   /usr/lib/libSM.so.6.0.0
42976000-4298c000 r-xp 00000000 08:01 13089165   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
4298c000-4298d000 rw-p 00015000 08:01 13089165   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
4298f000-42996000 r-xp 00000000 08:01 13089180   /usr/lib/libpangocairo-1.0.so.0.1600.2
42996000-42997000 rw-p 00007000 08:01 13089180   /usr/lib/libpangocairo-1.0.so.0.1600.2
42999000-429c3000 r-xp 00000000 08:01 13089179   /usr/lib/libpangoft2-1.0.so.0.1600.2
429c3000-429c4000 rw-p 0002a000 08:01 13089179   /usr/lib/libpangoft2-1.0.so.0.1600.2
429c6000-42a34000 r-xp 00000000 08:01 13089178   /usr/lib/libcairo.so.2.11.1
42a34000-42a36000 rw-p 0006d000 08:01 13089178   /usr/lib/libcairo.so.2.11.1
42a38000-42a51000 r-xp 00000000 08:01 13089188   /usr/lib/libatk-1.0.so.0.1809.1
42a51000-42a53000 rw-p 00018000 08:01 13089188   /usr/lib/libatk-1.0.so.0.1809.1
42a55000-42da6000 r-xp 00000000 08:01 13089189   /usr/lib/libgtk-x11-2.0.so.0.1000.11
42da6000-42dac000 rw-p 00351000 08:01 13089189   /usr/lib/libgtk-x11-2.0.so.0.1000.11
42dac000-42dad000 rw-p 42dac000 00:00 0 
42daf000-42deb000 r-xp 00000000 08:01 13089166   /usr/lib/libpango-1.0.so.0.1600.2
42deb000-42ded000 rw-p 0003b000 08:01 13089166   /usr/lib/libpango-1.0.so.0.1600.2
42def000-42e72000 r-xp 00000000 08:01 13089187   /usr/lib/libgdk-x11-2.0.so.0.1000.11
42e72000-42e75000 rw-p 00083000 08:01 13089187   /usr/lib/libgdk-x11-2.0.so.0.1000.11
42e77000-42e82000 r-xp 00000000 08:01 34752060   /lib/libgcc_s.so.1
42e82000-42e83000 rw-p 0000a000 08:01 34752060   /lib/libgcc_s.so.1
42e85000-42e94000 r-xp 00000000 08:01 34752053   /lib/tls/i686/cmov/libresolv-2.5.so
42e94000-42e96000 rw-p 0000f000 08:01 34752053   /lib/tls/i686/cmov/libresolv-2.5.so
42e96000-42e98000 rw-p 42e96000 00:00 0 
42f88000-42f9b000 r-xp 00000000 08:01 34752050   /lib/tls/i686/cmov/libnsl-2.5.so
42f9b000-42f9d000 rw-p 00012000 08:01 34752050   /lib/tls/i686/cmov/libnsl-2.5.so
42f9d000-42f9f000 rw-p 42f9d000 00:00 0 
42fa1000-42fbf000 r-xp 00000000 08:01 13089198   /usr/lib/libjpeg.so.62.0.0
42fbf000-42fc0000 rw-p 0001d000 08:01 13089198   /usr/lib/libjpeg.so.62.0.0
42fc2000-42fc4000 r-xp 00000000 08:01 34752056   /lib/tls/i686/cmov/libutil-2.5.so
42fc4000-42fc6000 rw-p 00001000 08:01 34752056   /lib/tls/i686/cmov/libutil-2.5.so
42fc8000-42fcf000 r-xp 00000000 08:01 34752052   /lib/tls/i686/cmov/librt-2.5.so
42fcf000-42fd1000 rw-p 00006000 08:01 34752052   /lib/tls/i686/cmov/librt-2.5.so
42fd3000-42fe7000 r-xp 00000000 08:01 34752055   /lib/libselinux.so.1
42fe7000-42fe9000 rw-p 00013000 08:01 34752055   /lib/libselinux.so.1
42feb000-42fee000 r-xp 00000000 08:01 13089201   /usr/lib/libgpg-error.so.0.3.0
42fee000-42fef000 rw-p 00002000 08:01 13089201   /usr/lib/libgpg-error.so.0.3.0
42ff1000-43027000 r-xp 00000000 08:01 34752054   /lib/libsepol.so.1
43027000-43028000 rw-p 00035000 08:01 34752054   /lib/libsepol.so.1
43028000-43032000 rw-p 43028000 00:00 0 
43034000-43083000 r-xp 00000000 08:01 13089202   /usr/lib/libgcrypt.so.11.2.2
43083000-43085000 rw-p 0004e000 08:01 13089202   /usr/lib/libgcrypt.so.11.2.2
43087000-430f1000 r-xp 00000000 08:01 13089203   /usr/lib/libgnutls.so.13.0.9
430f1000-430f7000 rw-p 0006a000 08:01 13089203   /usr/lib/libgnutls.so.13.0.9
430f9000-4310d000 r-xp 00000000 08:01 13089200   /usr/lib/libtasn1.so.3.0.6
4310d000-4310e000 rw-p 00013000 08:01 13089200   /usr/lib/libtasn1.so.3.0.6
43110000-43227000 r-xp 00000000 08:01 13089195   /usr/lib/libxml2.so.2.6.27
43227000-4322d000 rw-p 00116000 08:01 13089195   /usr/lib/libxml2.so.2.6.27
4322f000-43243000 r-xp 00000000 08:01 13089210   /usr/lib/libart_lgpl_2.so.2.3.17
43243000-43244000 rw-p 00013000 08:01 13089210   /usr/lib/libart_lgpl_2.so.2.3.17
43246000-43278000 r-xp 00000000 08:01 13080867   /usr/lib/libdbus-1.so.3.2.0
43278000-43279000 rw-p 00031000 08:01 13080867   /usr/lib/libdbus-1.so.3.2.0
4327b000-43295000 r-xp 00000000 08:01 13089208   /usr/lib/libdbus-glib-1.so.2.1.0
43295000-43296000 rw-p 0001a000 08:01 13089208   /usr/lib/libdbus-glib-1.so.2.1.0
43298000-432c7000 r-xp 00000000 08:01 13089214   /usr/lib/libgconf-2.so.4.1.2
432c7000-432ca000 rw-p 0002e000 08:01 13089214   /usr/lib/libgconf-2.so.4.1.2
432cf000-432d3000 r-xp 00000000 08:01 13089212   /usr/lib/libgthread-2.0.so.0.1200.11
432d3000-432d4000 rw-p 00003000 08:01 13089212   /usr/lib/libgthread-2.0.so.0.1200.11
432d6000-4331f000 r-xp 00000000 08:01 13089213   /usr/lib/libORBit-2.so.0.1.0
4331f000-43329000 rw-p 00048000 08:01 13089213   /usr/lib/libORBit-2.so.0.1.0
4332b000-43381000 r-xp 00000000 08:01 13089218   /usr/lib/libgnomevfs-2.so.0.1800.1
43381000-43384000 rw-p 00055000 08:01 13089218   /usr/lib/libgnomevfs-2.so.0.1800.1
43386000-43390000 r-xp 00000000 08:01 13089215   /usr/lib/libavahi-common.so.3.4.3
43390000-43391000 rw-p 00009000 08:01 13089215   /usr/lib/libavahi-common.so.3.4.3
43393000-43395000 r-xp 00000000 08:01 13089216   /usr/lib/libavahi-glib.so.1.0.1
43395000-43396000 rw-p 00001000 08:01 13089216   /usr/lib/libavahi-glib.so.1.0.1
43398000-433a6000 r-xp 00000000 08:01 13089217   /usr/lib/libavahi-client.so.3.2.2
433a6000-433a7000 rw-p 0000e000 08:01 13089217   /usr/lib/libavahi-client.so.3.2.2
433a9000-43469000 r-xp 00000000 08:01 13089223   /usr/lib/libasound.so.2.0.0
43469000-4346e000 rw-p 000bf000 08:01 13089223   /usr/lib/libasound.so.2.0.0
43470000-43490000 r-xp 00000000 08:01 13089222   /usr/lib/libaudiofile.so.0.0.2
43490000-43492000 rw-p 00020000 08:01 13089222   /usr/lib/libaudiofile.so.0.0.2
434a6000-434ae000 r-xp 00000000 08:01 13089192   /usr/lib/libstartup-notification-1.so.0.0.0
434ae000-434af000 rw-p 00007000 08:01 13089192   /usr/lib/libstartup-notification-1.so.0.0.0
434c4000-434cd000 r-xp 00000000 08:01 13089224   /usr/lib/libesd.so.0.2.36
434cd000-434ce000 rw-p 00009000 08:01 13089224   /usr/lib/libesd.so.0.2.36
b4d00000-b4d21000 rw-p b4d00000 00:00 0 
b4d21000-b4e00000 ---p b4d21000 00:00 0 
b4eff000-b4f05000 r-xp 00000000 08:01 13143685   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b4f05000-b4f06000 rw-p 00005000 08:01 13143685   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b4f06000-b4f66000 rw-s 00000000 00:08 51281924   /SYSV00000000 (deleted)
b4f66000-b4f67000 ---p b4f66000 00:00 0 
b4f67000-b5767000 rw-p b4f67000 00:00 0 
b5767000-b57e4000 r--p 00000000 08:01 13124123   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b57e4000-b57e6000 r-xp 00000000 08:01 13143494   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b57e6000-b57e7000 rw-p 00001000 08:01 13143494   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b57e7000-b57ea000 r--s 00000000 08:01 4178090    /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b57ea000-b57f0000 r--s 00000000 08:01 4177996    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b57f0000-b57f1000 r--s 00000000 08:01 4177994    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b57f1000-b57f4000 r--s 00000000 08:01 4177993    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b57f4000-b57f5000 r--s 00000000 08:01 4177992    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b57f5000-b57f6000 r--s 00000000 08:01 4177991    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b57f6000-b57fa000 r--s 00000000 08:01 4177990    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b57fa000-b57fb000 r--s 00000000 08:01 4177988    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b57fb000-b57fd000 r--s 00000000 08:01 4177987    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b57fd000-b57ff000 r--s 00000000 08:01 4177986    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b57ff000-b5800000 r--s 00000000 08:01 4177985    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b5800000-b5802000 r--s 00000000 08:01 4177984    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b5802000-b5808000 r--s 00000000 08:01 4177983    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5808000-b580a000 r--s 00000000 08:01 4177982    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b580a000-b580c000 r--s 00000000 08:01 4177981    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b580c000-b5814000 r--s 00000000 08:01 4177980    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5814000-b581a000 r--s 00000000 08:01 4177979    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b581a000-b581b000 r--s 00000000 08:01 4177978    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b581b000-b581d000 r--s 00000000 08:01 4177977    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b581d000-b5823000 r--s 00000000 08:01 4177976    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5823000-b5826000 r--s 00000000 08:01 4177975    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b5826000-b582a000 r--s 00000000 08:01 4177974    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b582a000-b5831000 r--s 00000000 08:01 4178088    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b5831000-b5832000 r--s 00000000 08:01 4178450    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b5832000-b5833000 r--s 00000000 08:01 4178449    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b5833000-b5834000 r--s 00000000 08:01 4178447    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b5834000-b5835000 r--s 00000000 08:01 4178424    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b5835000-b5836000 r--s 00000000 08:01 4178369    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b5836000-b5839000 r--s 00000000 08:01 4179019    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b5839000-b583e000 r--s 00000000 08:01 4178367    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b583e000-b5840000 r--s 00000000 08:01 4178366    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b5840000-b5841000 r--s 00000000 08:01 4178365    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b5841000-b5843000 r--s 00000000 08:01 4178364    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b5843000-b5844000 r--s 00000000 08:01 4178363    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b5844000-b5849000 r--s 00000000 08:01 4178362    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b5849000-b584d000 r--s 00000000 08:01 4178361    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b584d000-b584f000 r--s 00000000 08:01 4178360    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b584f000-b5852000 r--s 00000000 08:01 4178282    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b5852000-b5853000 r--s 00000000 08:01 4178281    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b5853000-b5856000 r--s 00000000 08:01 4179018    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b5856000-b585a000 r--s 00000000 08:01 4178279    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b585a000-b5860000 r--s 00000000 08:01 4178251    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b5860000-b5861000 r--s 00000000 08:01 4178224    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b5861000-b5869000 r--s 00000000 08:01 4178223    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b5869000-b586b000 r--s 00000000 08:01 4179017    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b586b000-b586e000 r--s 00000000 08:01 4178065    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b586e000-b5870000 r--s 00000000 08:01 4178059    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b5870000-b5bb1000 r--p 00000000 08:01 13157679   /usr/share/icons/hicolor/icon-theme.cache
b5bb1000-b5bc9000 r--p 00000000 08:01 13750044   /usr/local/share/icons/hicolor/icon-theme.cache
b5bc9000-b741c000 r--p 00000000 08:01 13617126   /usr/share/icons/crystalsvg/icon-theme.cache
b741c000-b7ac5000 r--p 00000000 08:01 13179497   /usr/share/icons/gnome/icon-theme.cache
b7ac5000-b7d1c000 r--p 00000000 08:01 13488530   /usr/share/icons/Tango/icon-theme.cache
b7d1c000-b7d2e000 r-xp 00000000 08:01 13179446   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b7d2e000-b7d2f000 rw-p 00012000 08:01 13179446   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b7d2f000-b7d8f000 rw-s 00000000 00:08 51249155   /SYSV00000000 (deleted)
b7d8f000-b7dec000 rw-p b7d8f000 00:00 0 
b7dec000-b7df3000 r-xp 00000000 08:01 13079036   /usr/lib/libfam.so.0.0.0
b7df3000-b7df4000 rw-p 00006000 08:01 13079036   /usr/lib/libfam.so.0.0.0
b7df4000-b7dfa000 r-xp 00000000 08:01 34752063   /lib/libacl.so.1.1.0
b7dfa000-b7dfb000 rw-p 00005000 08:01 34752063   /lib/libacl.so.1.1.0
b7dfb000-b7e02000 r--s 00000000 08:01 4178087    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b7e02000-b7e09000 r-xp 00000000 08:01 13179491   /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b7e09000-b7e0a000 rw-p 00007000 08:01 13179491   /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b7e0a000-b7e0e000 r-xp 00000000 08:01 13143679   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b7e0e000-b7e0f000 rw-p 00003000 08:01 13143679   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b7e10000-b7e1c000 r-xp 00000000 08:01 13156371   /usr/lib/gnome-vfs-2.0/modules/libfile.so
b7e1c000-b7e1d000 rw-p 0000b000 08:01 13156371   /usr/lib/gnome-vfs-2.0/modules/libfile.so
b7e1d000-b7e1e000 r-xp 00000000 08:01 13077127   /usr/lib/gconv/ISO8859-1.so
b7e1e000-b7e20000 rw-p 00000000 08:01 13077127   /usr/lib/gconv/ISO8859-1.so
b7e20000-b7e5b000 r--p 00000000 08:01 13109192   /usr/lib/locale/en_US.utf8/LC_CTYPE
b7e5b000-b7f32000 r--p 00000000 08:01 13109195   /usr/lib/locale/en_US.utf8/LC_COLLATE
b7f32000-b7f3b000 r-xp 00000000 08:01 34750626   /lib/tls/i686/cmov/libnss_files-2.5.so
b7f3b000-b7f3d000 rw-p 00008000 08:01 34750626   /lib/tls/i686/cmov/libnss_files-2.5.so
b7f3d000-b7f45000 r-xp 00000000 08:01 34750629   /lib/tls/i686/cmov/libnss_nis-2.5.so
b7f45000-b7f47000 rw-p 00007000 08:01 34750629   /lib/tls/i686/cmov/libnss_nis-2.5.so
b7f47000-b7f4e000 r-xp 00000000 08:01 34750624   /lib/tls/i686/cmov/libnss_compat-2.5.so
b7f4e000-b7f50000 rw-p 00006000 08:01 34750624   /lib/tls/i686/cmov/libnss_compat-2.5.so
b7f50000-b7f61000 rw-p b7f50000 00:00 0 
b7f61000-b7f64000 r-xp 00000000 08:01 34752062   /lib/libattr.so.1.1.0
b7f64000-b7f65000 rw-p 00002000 08:01 34752062   /lib/libattr.so.1.1.0
b7f65000-b7f66000 r--p 00000000 08:01 13109193   /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7f66000-b7f67000 r--p 00000000 08:01 13109194   /usr/lib/locale/en_US.utf8/LC_TIME
b7f67000-b7f68000 r--p 00000000 08:01 13109196   /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f68000-b7f69000 r--p 00000000 08:01 13109198   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f69000-b7f6a000 r--p 00000000 08:01 13109199   /usr/lib/locale/en_US.utf8/LC_PAPER
b7f6a000-b7f6b000 r--p 00000000 08:01 13109200   /usr/lib/locale/en_US.utf8/LC_NAME
b7f6b000-b7f6c000 r--p 00000000 08:01 13109201   /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f6c000-b7f6d000 r--p 00000000 08:01 13109202   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f6d000-b7f6e000 r--p 00000000 08:01 13109203   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f6e000-b7f75000 r--s 00000000 08:01 13076489   /usr/lib/gconv/gconv-modules.cache
b7f75000-b7f76000 r--p 00000000 08:01 13109204   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f76000-b7f78000 rw-p b7f76000 00:00 0 
bfb43000-bfb58000 rw-p bfb43000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
/usr/local/bin/ccsm

(update-notifier:22615): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```

can anyone help me with this please?

---

### Post by Pumalite on 2007-08-10
Is Gnome your default? You mean when you boot you get those errors?

---

### Post by Opeth115 on 2007-08-10
yes gnome is my default. no i get it when i try to log in from gdm.  it's one of those ur session has only lasted 10 seconds error messages

---

### Post by Pumalite on 2007-08-10
[http://marc.info/?l=gnome&m=112760670403796&w=2](http://marc.info/?l=gnome&m=112760670403796&w=2)

[http://www.linuxquestions.org/questions/showthread.php?t=386010](http://www.linuxquestions.org/questions/showthread.php?t=386010)

[http://www.linuxquestions.org/questions/showthread.php?t=373299](http://www.linuxquestions.org/questions/showthread.php?t=373299)

[http://ubuntuforums.org/archive/index.php/t-374662.html](http://ubuntuforums.org/archive/index.php/t-374662.html)

[http://ubuntuforums.org/showthread.php?t=23467](http://ubuntuforums.org/showthread.php?t=23467)

[http://www.fedoraforum.org/forum/showthread.php?p=844604#post844](http://www.fedoraforum.org/forum/showthread.php?p=844604#post844)

---

### Post by Opeth115 on 2007-08-10
hey ok well id on't know what i did lol but i no longer get that error on login i now get this before the login evenm starts. (right after i type my password and press enter)  

"Users $HOME/.dmrc file is being ignored.  This prevents the default session and language form being saved.  File should be owned by user and have 644 permissions.  Users $HOME directory must be owned by user and not writeable by other users."

any help on that one? lol i can now log in but that pops up after i type my password...

---

### Post by Pumalite on 2007-08-10
I think you can safely ignore that. Just click: 'OK'

---

### Post by Opeth115 on 2007-08-10
ok thank you very much for helping me!

---

