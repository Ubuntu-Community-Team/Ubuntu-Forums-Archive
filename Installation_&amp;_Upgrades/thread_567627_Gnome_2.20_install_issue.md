---
title: "Gnome 2.20 install issue"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by mobiu5 on 2007-10-04
Running Ubuntu, and trying to update Gnome.  I know a new version of Ubuntu is coming, but I just want to update Gnome right now.

However, when I try to run the command "make install", it runs for about 20 minutes, but then fails with the following errors.  Can someone help me diagnose what the problem is?

Thanks.

```
In file included from glitz_glx_drawable.c:30:
glitz_glxint.h:34:19: error: GL/gl.h: No such file or directory
glitz_glxint.h:35:20: error: GL/glx.h: No such file or directory
In file included from glitz_glxint.h:37,
                 from glitz_glx_drawable.c:30:
glitz_glxext.h:110: error: expected declaration specifiers or '...' before 'GLXDrawable'
glitz_glxext.h:113: error: expected declaration specifiers or '...' before 'GLXDrawable'
glitz_glxext.h:113: error: expected declaration specifiers or '...' before 'GLXDrawable'
glitz_glxext.h:113: error: expected declaration specifiers or '...' before 'GLXContext'
glitz_glxext.h:114: error: expected declaration specifiers or '...' before '*' token
glitz_glxext.h:116: error: expected declaration specifiers or '...' before 'GLXContext'
glitz_glxext.h:116: warning: type defaults to 'int' in declaration of 'GLXContext'
glitz_glxext.h:116: error: 'GLXContext' declared as function returning a function
glitz_glxext.h:116: warning: function declaration isn't a prototype
glitz_glxext.h:124: error: expected declaration specifiers or '...' before 'GLXDrawable'
In file included from glitz_glx_drawable.c:30:
glitz_glxint.h:61: error: expected specifier-qualifier-list before 'glitz_glx_create_new_context_t'
glitz_glxint.h:88: error: field 'context' declared as a function
glitz_glxint.h:105: error: field 'root_context' declared as a function
glitz_glxint.h:117: error: expected specifier-qualifier-list before 'GLXDrawable'
glitz_glx_drawable.c:36: error: expected declaration specifiers or '...' before 'GLXDrawable'
glitz_glx_drawable.c: In function '_glitz_glx_create_drawable':
glitz_glx_drawable.c:49: error: 'glitz_glx_drawable_t' has no member named 'drawable'
glitz_glx_drawable.c:49: error: 'glx_drawable' undeclared (first use in this function)
glitz_glx_drawable.c:49: error: (Each undeclared identifier is reported only once
glitz_glx_drawable.c:49: error: for each function it appears in.)
glitz_glx_drawable.c:50: error: 'glitz_glx_drawable_t' has no member named 'pbuffer'
glitz_glx_drawable.c:51: error: 'glitz_glx_drawable_t' has no member named 'width'
glitz_glx_drawable.c:52: error: 'glitz_glx_drawable_t' has no member named 'height'
glitz_glx_drawable.c: In function '_glitz_glx_drawable_update_size':
glitz_glx_drawable.c:80: error: 'glitz_glx_drawable_t' has no member named 'pbuffer'
glitz_glx_drawable.c:82: error: 'glitz_glx_drawable_t' has no member named 'pbuffer'
glitz_glx_drawable.c:83: error: 'glitz_glx_drawable_t' has no member named 'drawable'
glitz_glx_drawable.c:83: error: 'glitz_glx_drawable_t' has no member named 'pbuffer'
glitz_glx_drawable.c:87: error: 'glitz_glx_drawable_t' has no member named 'pbuffer'
glitz_glx_drawable.c:91: error: 'glitz_glx_drawable_t' has no member named 'width'
glitz_glx_drawable.c:92: error: 'glitz_glx_drawable_t' has no member named 'height'
glitz_glx_drawable.c: In function '_glitz_glx_create_pbuffer_drawable':
glitz_glx_drawable.c:118: error: too many arguments to function '_glitz_glx_create_drawable'
glitz_glx_drawable.c: In function 'glitz_glx_create_drawable_for_window':
glitz_glx_drawable.c:169: error: too many arguments to function '_glitz_glx_create_drawable'
glitz_glx_drawable.c: In function 'glitz_glx_destroy':
glitz_glx_drawable.c:223: warning: implicit declaration of function 'glXGetCurrentDrawable'
glitz_glx_drawable.c:223: warning: nested extern declaration of 'glXGetCurrentDrawable'
glitz_glx_drawable.c:223: error: 'glitz_glx_drawable_t' has no member named 'drawable'
glitz_glx_drawable.c:224: warning: implicit declaration of function 'glXMakeCurrent'
glitz_glx_drawable.c:224: warning: nested extern declaration of 'glXMakeCurrent'
glitz_glx_drawable.c:227: error: 'glitz_glx_drawable_t' has no member named 'pbuffer'
glitz_glx_drawable.c:228: error: 'glitz_glx_drawable_t' has no member named 'pbuffer'
glitz_glx_drawable.c: In function 'glitz_glx_swap_buffers':
glitz_glx_drawable.c:239: warning: implicit declaration of function 'glXSwapBuffers'
glitz_glx_drawable.c:239: warning: nested extern declaration of 'glXSwapBuffers'
glitz_glx_drawable.c:240: error: 'glitz_glx_drawable_t' has no member named 'drawable'
glitz_glx_drawable.c: In function 'glitz_glx_copy_sub_buffer':
glitz_glx_drawable.c:258: error: 'glitz_glx_static_proc_address_list_t' has no member named 'copy_sub_buffer'
glitz_glx_drawable.c:259: error: 'glitz_glx_drawable_t' has no member named 'drawable'
make[8]: *** [glitz_glx_drawable.lo] Error 1
make[8]: Leaving directory `/home/mathew/garnome-2.20.0/freedesktop/glitz/work/main.d/glitz-0.5.6/src/glx'
make[7]: *** [all-recursive] Error 1
make[7]: Leaving directory `/home/mathew/garnome-2.20.0/freedesktop/glitz/work/main.d/glitz-0.5.6/src'
make[6]: *** [all-recursive] Error 1
make[6]: Leaving directory `/home/mathew/garnome-2.20.0/freedesktop/glitz/work/main.d/glitz-0.5.6'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/mathew/garnome-2.20.0/freedesktop/glitz/work/main.d/glitz-0.5.6'
make[4]: *** [build-work/main.d/glitz-0.5.6/Makefile] Error 2
make[4]: Leaving directory `/home/mathew/garnome-2.20.0/freedesktop/glitz'
make[3]: *** [../../freedesktop/glitz/cookies/main.d/install] Error 2
make[3]: Leaving directory `/home/mathew/garnome-2.20.0/freedesktop/cairo'
make[2]: *** [../../freedesktop/cairo/cookies/main.d/install] Error 2
make[2]: Leaving directory `/home/mathew/garnome-2.20.0/platform/pango'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/mathew/garnome-2.20.0/platform'
make: *** [install] Error 2

```

---

### Post by mobiu5 on 2007-10-05
Figured it out... Glitz was an issue.

But now that I can get the build finish, what do I need to do to upgrade my current Ubuntu install.  I am not to interested right now in Gutsy, as the beta has crashed my system 4 times already...

---

