---
title: "evince &quot;pdf not supported&quot;"
date: 2009-05-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cjsteele on 2009-05-27
I'm running Karmic testing.  PDF's I had been able to open in the past (and all other PDF's) fail to open with an error in evince that reads:

"File type PDF document (application/pdf) is not supported"

evince is at version 2.26.1-0ubuntu2.  All linked libraries appear to be present... 

cjs@sxf-cjsteele:~$ ldd `which evince`
	linux-vdso.so.1 =>  (0x00007fff86784000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00007f19b39b5000)
	libevdocument.so.1 => /usr/lib/libevdocument.so.1 (0x00007f19b379a000)
	libevview.so.1 => /usr/lib/libevview.so.1 (0x00007f19b3571000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0x00007f19b3214000)
	liblaunchpad-integration.so.1 => /usr/lib/liblaunchpad-integration.so.1 (0x00007f19b300f000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00007f19b2a15000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00007f19b27f5000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007f19b25c7000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007f19b2342000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007f19b2110000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x00007f19b1f0b000)
	librt.so.1 => /lib/librt.so.1 (0x00007f19b1d03000)
	libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0x00007f19b1ae1000)
	libdbus-1.so.3 => /lib/libdbus-1.so.3 (0x00007f19b18a2000)
	libgnome-keyring.so.0 => /usr/lib/libgnome-keyring.so.0 (0x00007f19b168d000)
	libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0x00007f19b1450000)
	libz.so.1 => /lib/libz.so.1 (0x00007f19b1238000)
	libpoppler-glib.so.4 => /usr/lib/libpoppler-glib.so.4 (0x00007f19b100d000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00007f19b0d6b000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007f19b0b4f000)
	libm.so.6 => /lib/libm.so.6 (0x00007f19b08ca000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007f19b06be000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00007f19b042c000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007f19b01e3000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007f19aff60000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007f19afd17000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007f19afb13000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007f19af84b000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f19af62f000)
	libc.so.6 => /lib/libc.so.6 (0x00007f19af2bd000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00007f19af0a2000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f19aed6b000)
	libuuid.so.1 => /lib/libuuid.so.1 (0x00007f19aeb66000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f19ae962000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f19ae750000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f19ae546000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007f19ae344000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007f19ae139000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007f19adf30000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f19add26000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00007f19adb23000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f19ad921000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f19ad71b000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007f19ad4f1000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00007f19ad2c1000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f19b3bbe000)
	libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0x00007f19ad053000)
	libpoppler.so.4 => /usr/lib/libpoppler.so.4 (0x00007f19acc69000)
	libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0x00007f19aca44000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f19ac735000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f19ac51a000)
	libresolv.so.2 => /lib/libresolv.so.2 (0x00007f19ac302000)
	libselinux.so.1 => /lib/libselinux.so.1 (0x00007f19ac0e5000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007f19abea0000)
	libdirectfb-1.0.so.0 => /usr/lib/libdirectfb-1.0.so.0 (0x00007f19abc2c000)
	libfusion-1.0.so.0 => /usr/lib/libfusion-1.0.so.0 (0x00007f19aba23000)
	libdirect-1.0.so.0 => /usr/lib/libdirect-1.0.so.0 (0x00007f19ab80d000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f19ab5e6000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x00007f19ab3e2000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00007f19ab1d9000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f19aafbd000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f19aadba000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f19aabb5000)




Anyone have any thoughts?  I've tried removing evince and re-installing, still no love.  Ditto for dependencies.

Best,
-C

---

### Post by overdrank on 2009-05-27
Moved to  Karmic Koala Testing and Discussion

---

### Post by userdce on 2009-07-14
me too having this problem

(evince:7691): EvinceDocument-WARNING **: /usr/lib/evince/1/backends/libpdfdocument.so: undefined symbol: poppler_layers_iter_free

(evince:7691): EvinceDocument-WARNING **: Cannot load backend 'pdfdocument' since file '/usr/lib/evince/1/backends/libpdfdocument.so' cannot be read.

(evince:7691): EvinceDocument-WARNING **: /usr/lib/evince/1/backends/libpdfdocument.so: undefined symbol: poppler_layers_iter_free

(evince:7691): EvinceDocument-WARNING **: Cannot load backend 'pdfdocument' since file '/usr/lib/evince/1/backends/libpdfdocument.so' cannot be read.

---

### Post by dino99 on 2009-07-14
have you send a bug report ?

---

