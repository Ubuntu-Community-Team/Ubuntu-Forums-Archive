---
title: "Tkgate install from source"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by max246 on 2008-11-26
I have install tkgate from source and  tk,tcl 8.4.
When I run the programm it didn't load libtk8.4.so!

Result:
 ldd `which tkgate`
	linux-gate.so.1 =>  (0xb802d000)
	libtk8.4.so => not found
	libtcl8.4.so => not found
	libX11.so.6 => /usr/lib/libX11.so.6 (0x480e3000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x48082000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0x48be8000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x480a3000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x47f22000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x481fb000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x481d9000)
	/lib/ld-linux.so.2 (0x4742a000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x481d4000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x481f4000)

but the program wish a found the lib!

 ldd `which wish`
	linux-gate.so.1 =>  (0xb7f5d000)
	libtk8.4.so.0 => /usr/lib/libtk8.4.so.0 (0x47505000)
	libtcl8.4.so.0 => /usr/lib/libtcl8.4.so.0 (0x47449000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x48088000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x480e3000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x48082000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x480a3000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x47f22000)
	/lib/ld-linux.so.2 (0x4742a000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x481fb000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x481d9000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x481d4000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x481f4000)


The lib is install from source and work!

What do link libtk and libtcl on tkgate??????

(Sorry for my bad english)

---

### Post by lemming465 on 2008-11-28
Did you re-run "ldconfig" after installing stuff?

---

