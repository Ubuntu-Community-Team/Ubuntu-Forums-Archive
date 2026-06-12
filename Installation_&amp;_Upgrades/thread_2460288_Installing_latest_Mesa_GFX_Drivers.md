---
title: "Installing latest Mesa GFX Drivers"
date: 2021-04-06
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2021-04-06
I am using an XPS13-9330 laptop with Ubuntu 20.04. The machine came with windows and I dual booted it.

I want to use a program called VirtScreen but am getting errors that it cannot find a driver:

```

makem@XPS-13-9300:~$ virtscreen
libGL error: MESA-LOADER: failed to open iris (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri)
libGL error: failed to load driver: iris
libGL error: MESA-LOADER: failed to open iris (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri)
libGL error: failed to load driver: iris
libGL error: MESA-LOADER: failed to open swrast (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri)
libGL error: failed to load driver: swrast
QGLXContext: Failed to create dummy context
qml: Loader Status Changed. 1
Failed to create OpenGL context for format QSurfaceFormat(version 2.0, options QFlags<QSurfaceFormat::FormatOption>(), depthBufferSize 24, redBufferSize -1, greenBufferSize -1, blueBufferSize -1, alphaBufferSize -1, stencilBufferSize 8, samples -1, swapBehavior QSurfaceFormat::SwapBehavior(DoubleBuffer), swapInterval 1, colorSpace QSurfaceFormat::ColorSpace(DefaultColorSpace), profile  QSurfaceFormat::OpenGLContextProfile(NoProfile)) 
Aborted (core dumped)
makem@XPS-13-9300:~$

```

The Gfx card is:

```

makem@XPS-13-9300:~$ lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Iris Plus Graphics G7 [8086:8a52] (rev 07) (prog-if 00 [VGA controller])
makem@XPS-13-9300:~$

```

OpenGl is:

```

makem@XPS-13-9300:~$ glxinfo | grep "OpenGL version"
OpenGL version string: 4.6 (Compatibility Profile) Mesa 20.2.6
makem@XPS-13-9300:~$

```

I have come across the web page below which tells how to install the latest Mesa drivers. However, before I attempt that, two things, where can I find the latest Mesa version number and, is the web page fraught with danger for someone not familiar with the subject?


[https://itsfoss.com/install-mesa-ubuntu/](https://itsfoss.com/install-mesa-ubuntu/)

Edit: Found the latest Mesa drivers 21.01 but I don't know if the web page is to be trusted.

---

