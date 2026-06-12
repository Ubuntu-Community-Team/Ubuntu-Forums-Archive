---
title: "Macbook 2,1 with Intel 945 no 3D acceleration (Lucid)"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mnml on 2010-04-11
Hi, this is the errors I'm getting when I'm using the glxinfo | grep direct command, I would like to know how I can solve that.

glxinfo | grep direct
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/i915_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/i915_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/i915_dri.so failed (/usr/lib/fglrx/dri/i915_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: i915_dri.so
libGL error: driver pointer missing
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrast_dri.so failed (/usr/lib/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: reverting to indirect rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

---

