---
title: "Problems running X-Plane after upgrade to 11.10 64-bit"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by billfish1881 on 2011-10-24
Hi Folks,
     I recently did an upgrade from Natty to Oneiric Ocelot. My X-Plane 9 flight simulator was running just fine prior to the upgrade and now it won't even run the executable files. The install file will not run either. This is what I get when i try to launch X-Plane:

billfish@billDesktop:~/X-Plane-9$ ./"X-Plane-i686"
./X-Plane-i686: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory

So I did a dependency check:


billfish@billDesktop:~/X-Plane-9$ ldd ./"X-Plane-i686"
	linux-gate.so.1 =>  (0xf7794000)
	libGL.so.1 => /usr/lib32/nvidia-current-updates/libGL.so.1 (0xf76aa000)
	libGLU.so.1 => not found
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf7696000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf7560000)
	libXrandr.so.2 => /usr/lib/i386-linux-gnu/libXrandr.so.2 (0xf7557000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf753c000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7537000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf750c000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7390000)
	/lib/ld-linux.so.2 (0xf7795000)
	libnvidia-tls.so.280.13 => /usr/lib32/nvidia-current-updates/tls/libnvidia-tls.so.280.13 (0xf738d000)
	libnvidia-glcore.so.280.13 => /usr/lib32/nvidia-current-updates/libnvidia-glcore.so.280.13 (0xf5a7c000)
	librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf5a73000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf5a53000)
	libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf5a48000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf5a44000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf5a3d000)


Seems like there is an issue with "libGLU.so.1"
I am running a 64-bit system. If anyone can shed some light on why this is happening and how I can fix it I would be forever grateful to you.

---

