---
title: "Install Gnome 2.16 on Drapper, i have a few problems:"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by sbmd on 2006-09-07
Hello I am getting a few errors and I am too noobish to linux to figure them all out. 


I am using the Garnome script to install Gnome 2.16.0.

This is what I get before it errors out:

```

In file included from glitz_glx_drawable.c:30:
glitz_glxint.h:34:19: error: GL/gl.h: No such file or directory
glitz_glxint.h:35:20: error: GL/glx.h: No such file or directory
In file included from glitz_glxint.h:37,
                 from glitz_glx_drawable.c:30:
glitz_glxext.h:110: error: syntax error before 'GLXDrawable'
glitz_glxext.h:111: warning: function declaration isn't a prototype
glitz_glxext.h:113: error: syntax error before 'GLXDrawable'
glitz_glxext.h:113: warning: function declaration isn't a prototype
glitz_glxext.h:114: error: syntax error before '*' token
glitz_glxext.h:116: error: syntax error before 'GLXContext'
glitz_glxext.h:116: warning: type defaults to 'int' in declaration of 'GLXContext'
glitz_glxext.h:116: warning: function declaration isn't a prototype
glitz_glxext.h:116: error: 'GLXContext' declared as function returning a function
glitz_glxext.h:116: warning: function declaration isn't a prototype
glitz_glxext.h:124: error: syntax error before 'GLXDrawable'
glitz_glxext.h:124: warning: function declaration isn't a prototype
In file included from glitz_glx_drawable.c:30:
glitz_glxint.h:61: error: syntax error before 'glitz_glx_create_new_context_t'
glitz_glxint.h:61: warning: no semicolon at end of struct or union
glitz_glxint.h:63: error: syntax error before '}' token
glitz_glxint.h:63: warning: type defaults to 'int' in declaration of 'glitz_glx_static_proc_address_list_t'
glitz_glxint.h:63: warning: data definition has no type or storage class
glitz_glxint.h:88: error: field 'context' declared as a function
glitz_glxint.h:105: error: field 'root_context' declared as a function
glitz_glxint.h:108: error: syntax error before 'glitz_glx_static_proc_address_list_t'
glitz_glxint.h:108: warning: no semicolon at end of struct or union
glitz_glxint.h:110: error: syntax error before '}' token
glitz_glxint.h:117: error: syntax error before 'GLXDrawable'
glitz_glxint.h:117: warning: no semicolon at end of struct or union
glitz_glxint.h:118: warning: type defaults to 'int' in declaration of 'pbuffer'
glitz_glxint.h:118: warning: data definition has no type or storage class
glitz_glxint.h:121: error: syntax error before '}' token
glitz_glx_drawable.c:36: error: syntax error before 'GLXDrawable'
glitz_glx_drawable.c:40: warning: function declaration isn't a prototype
glitz_glx_drawable.c: In function '_glitz_glx_create_drawable':
glitz_glx_drawable.c:43: error: invalid application of 'sizeof' to incomplete type 'glitz_glx_drawable_t'
glitz_glx_drawable.c:47: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:47: error: 'screen_info' undeclared (first use in this function)
glitz_glx_drawable.c:47: error: (Each undeclared identifier is reported only once
glitz_glx_drawable.c:47: error: for each function it appears in.)
glitz_glx_drawable.c:48: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:48: error: 'context' undeclared (first use in this function)
glitz_glx_drawable.c:49: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:49: error: 'glx_drawable' undeclared (first use in this function)
glitz_glx_drawable.c:50: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:50: error: 'glx_pbuffer' undeclared (first use in this function)
glitz_glx_drawable.c:51: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:52: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:54: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:55: error: 'format' undeclared (first use in this function)
glitz_glx_drawable.c: In function '_glitz_glx_drawable_update_size':
glitz_glx_drawable.c:80: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:82: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:82: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:83: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:83: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:84: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:85: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:87: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:91: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:92: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function '_glitz_glx_create_pbuffer_drawable':
glitz_glx_drawable.c:124: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_create_pbuffer':
glitz_glx_drawable.c:135: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_create_drawable_for_window':
glitz_glx_drawable.c:156: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:159: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:173: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_create_pbuffer_drawable':
glitz_glx_drawable.c:191: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:194: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_destroy':
glitz_glx_drawable.c:209: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:210: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:217: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:218: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:219: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:223: warning: implicit declaration of function 'glXGetCurrentDrawable'
glitz_glx_drawable.c:223: warning: nested extern declaration of 'glXGetCurrentDrawable'
glitz_glx_drawable.c:223: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:224: warning: implicit declaration of function 'glXMakeCurrent'
glitz_glx_drawable.c:224: warning: nested extern declaration of 'glXMakeCurrent'
glitz_glx_drawable.c:224: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:227: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:228: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:228: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_swap_buffers':
glitz_glx_drawable.c:239: warning: implicit declaration of function 'glXSwapBuffers'
glitz_glx_drawable.c:239: warning: nested extern declaration of 'glXSwapBuffers'
glitz_glx_drawable.c:239: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:240: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_copy_sub_buffer':
glitz_glx_drawable.c:254: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:256: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:258: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:258: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:259: error: dereferencing pointer to incomplete type
make[9]: *** [glitz_glx_drawable.lo] Error 1
make[9]: Leaving directory `/home/bobz/downloads/garnome-2.16.0/freedesktop/glitz/work/main.d/glitz-0.5.6/src/glx'
make[8]: *** [all-recursive] Error 1
make[8]: Leaving directory `/home/bobz/downloads/garnome-2.16.0/freedesktop/glitz/work/main.d/glitz-0.5.6/src'
make[7]: *** [all-recursive] Error 1
make[7]: Leaving directory `/home/bobz/downloads/garnome-2.16.0/freedesktop/glitz/work/main.d/glitz-0.5.6'
make[6]: *** [all] Error 2
make[6]: Leaving directory `/home/bobz/downloads/garnome-2.16.0/freedesktop/glitz/work/main.d/glitz-0.5.6'
make[5]: *** [build-work/main.d/glitz-0.5.6/Makefile] Error 2
make[5]: Leaving directory `/home/bobz/downloads/garnome-2.16.0/freedesktop/glitz'
make[4]: *** [../../freedesktop/glitz/cookies/main.d/install] Error 2
make[4]: Leaving directory `/home/bobz/downloads/garnome-2.16.0/freedesktop/cairo'
make[3]: *** [../../freedesktop/cairo/cookies/main.d/install] Error 2
make[3]: Leaving directory `/home/bobz/downloads/garnome-2.16.0/platform/gtk+'
make[2]: *** [../../platform/gtk+/cookies/main.d/install] Error 2
make[2]: Leaving directory `/home/bobz/downloads/garnome-2.16.0/bindings/pygtk'
make[1]: *** [../../bindings/pygtk/cookies/main.d/install] Error 2
make[1]: Leaving directory `/home/bobz/downloads/garnome-2.16.0/desktop/alacarte'
make: *** [paranoid-install] Error 2

```

So I guess what do I need to do to get passed this point? 
I have been searching, and I am going to continue searching until i get it, but I was just hoping that someone here could help. Thankx for any help in advance!!](*,)

---

### Post by scto on 2006-09-07
hi,

you've to install some gl dev packages like libgl-mesa-dev (for glx.h) and mesa-common-dev (for gl.h).
This will fix:

glitz_glxint.h:34:19: error: GL/gl.h: No such file or directory
glitz_glxint.h:35:20: error: GL/glx.h: No such file or directory.

Hope this helps
regards
scto

---

### Post by sbmd on 2006-09-07
Yes thankx, i was not looking for the correct name of the packages. I am trying to finish the install now.

---

### Post by BLTicklemonster on 2006-09-07
No fair at all! You have 2.16 and I don't! Where'd you get it? Or are you compiling it from source?

---

### Post by sbmd on 2006-09-07
> Yes I am compiling it, well at least trying too. LOL

I now have another error that I am going to need some help on:

```

[===== NOW BUILDING:    gamin-0.1.7     =====]
        [fetch] complete for gamin.
        [checksum] complete for gamin.
        [extract] complete for gamin.
        [patch] complete for gamin.
        [fixup] complete for gamin.
lib/Makefile.am:1: INCLUDES defined both conditionally and unconditionally
libgamin/Makefile.am:1: INCLUDES defined both conditionally and unconditionally
libgamin/Makefile.am:58: variable `LDADDS' not defined
server/Makefile.am:1: INCLUDES defined both conditionally and unconditionally
server/Makefile.am:19: gam_server_SOURCES defined both conditionally and unconditionally
server/Makefile.am:78: gam_server_LDADD defined both conditionally and unconditionally
server/Makefile.am:78: variable `LDADDS' not defined
tests/Makefile.am:13: variable `LDADDS' not defined
python/Makefile.am:13: bad macro name `_gamin_la_LDFLAGS'
python/Makefile.am:23: bad macro name `_gamin_la_SOURCES'
python/Makefile.am:24: bad macro name `_gamin_la_LIBADD'
make[6]: *** [pre-configure] Error 1
make[6]: Leaving directory `/home/bobz/garnome-2.16.0/bootstrap/gamin'
make[5]: *** [../../bootstrap/gamin/cookies/main.d/install] Error 2
make[5]: Leaving directory `/home/bobz/garnome-2.16.0/platform/gnome-vfs'
make[4]: *** [../../platform/gnome-vfs/cookies/main.d/install] Error 2
make[4]: Leaving directory `/home/bobz/garnome-2.16.0/platform/libgnome'
make[3]: *** [../../platform/libgnome/cookies/main.d/install] Error 2
make[3]: Leaving directory `/home/bobz/garnome-2.16.0/platform/libbonoboui'
make[2]: *** [../../platform/libbonoboui/cookies/main.d/install] Error 2
make[2]: Leaving directory `/home/bobz/garnome-2.16.0/platform/libgnomeui'
make[1]: *** [../../platform/libgnomeui/cookies/main.d/install] Error 2
make[1]: Leaving directory `/home/bobz/garnome-2.16.0/desktop/bug-buddy'
make: *** [paranoid-install] Error 2

```

Thankx for your help.


I solved this problem with this thread: [http://ubuntuforums.org/showthread.php?p=1432174](http://ubuntuforums.org/showthread.php?p=1432174)

Thankx Mac_D83 \\:D/ 
I am getting closer to the prize!

---

### Post by BLTicklemonster on 2006-09-07
So, just the name, "compiling" scares me. I am already fluent in screwing the pooch from the command line with something as innocuous as "sudo", dare I ask, "so tell me about compiling, how hard is it?", or ought I to just leave it alone?

And what's it like? The new Gnome, that is.

---

### Post by sbmd on 2006-09-08
It is not hard i guess this is my real first try at it and it is sometimes hard to have all the proper packages install ahead of time as I am finding out. LOL

But i have a new problem here if someone can help:

```

src/jni/jg_jnu.h:8:17: error: jni.h: No such file or directory
In file included from src/jni/jg_jnu.c:6:
src/jni/jg_jnu.h:16: error: syntax error before '*' token
src/jni/jg_jnu.h:16: error: syntax error before '*' token
src/jni/jg_jnu.h:16: error: 'jobject' declared as function returning a function
src/jni/jg_jnu.h:23: error: syntax error before '*' token
src/jni/jg_jnu.h:23: warning: data definition has no type or storage class
src/jni/jg_jnu.h:32: error: syntax error before '*' token
src/jni/jg_jnu.h:34: error: syntax error before '*' token
src/jni/jg_jnu.h:36: error: syntax error before '*' token
src/jni/jg_jnu.h:38: error: syntax error before 'getJavaStringArray'
src/jni/jg_jnu.h:38: error: syntax error before '*' token
src/jni/jg_jnu.h:38: warning: data definition has no type or storage class
src/jni/jg_jnu.h:46: error: syntax error before 'getSList'
src/jni/jg_jnu.h:46: error: syntax error before '*' token
src/jni/jg_jnu.h:46: warning: data definition has no type or storage class
src/jni/jg_jnu.h:54: error: syntax error before 'getList'
src/jni/jg_jnu.h:54: error: syntax error before '*' token
src/jni/jg_jnu.h:54: warning: data definition has no type or storage class
src/jni/jg_jnu.h:56: error: syntax error before '*' token
src/jni/jg_jnu.h:58: error: syntax error before '*' token
src/jni/jg_jnu.h:58: error: 'getHandleFromPointer' declared as function returning a function
src/jni/jg_jnu.h:60: error: syntax error before '*' token
src/jni/jg_jnu.h:62: error: syntax error before '*' token
src/jni/jg_jnu.h:64: error: syntax error before 'getHandleArrayFromPointers'
src/jni/jg_jnu.h:64: error: syntax error before '*' token
src/jni/jg_jnu.h:64: warning: data definition has no type or storage class
src/jni/jg_jnu.h:66: error: syntax error before 'getHandlesFromPointers'
src/jni/jg_jnu.h:66: error: syntax error before '*' token
src/jni/jg_jnu.h:67: warning: data definition has no type or storage class
src/jni/jg_jnu.h:69: error: syntax error before 'getHandleArrayFromGList'
src/jni/jg_jnu.h:69: error: syntax error before '*' token
src/jni/jg_jnu.h:69: warning: data definition has no type or storage class
src/jni/jg_jnu.h:71: error: syntax error before 'getHandlesFromGList'
src/jni/jg_jnu.h:71: error: syntax error before '*' token
src/jni/jg_jnu.h:72: warning: data definition has no type or storage class
src/jni/jg_jnu.h:74: error: syntax error before 'getHandleArrayFromGSList'
src/jni/jg_jnu.h:74: error: syntax error before '*' token
src/jni/jg_jnu.h:74: warning: data definition has no type or storage class
src/jni/jg_jnu.h:76: error: syntax error before 'getHandlesFromGSList'
src/jni/jg_jnu.h:76: error: syntax error before '*' token
src/jni/jg_jnu.h:77: warning: data definition has no type or storage class
src/jni/jg_jnu.h:79: error: syntax error before 'getHandleArray'
src/jni/jg_jnu.h:79: error: syntax error before '*' token
src/jni/jg_jnu.h:79: warning: data definition has no type or storage class
src/jni/jg_jnu.h:81: error: syntax error before '*' token
src/jni/jg_jnu.h:83: error: syntax error before '*' token
src/jni/jg_jnu.h:85: error: syntax error before '*' token
src/jni/jg_jnu.h:87: error: syntax error before '*' token
src/jni/jg_jnu.h:89: error: syntax error before '*' token
src/jni/jg_jnu.h:89: error: 'updateHandle' declared as function returning a function
src/jni/jg_jnu.h:91: error: syntax error before 'getHandleClass'
src/jni/jg_jnu.h:91: error: syntax error before '*' token
src/jni/jg_jnu.h:91: warning: data definition has no type or storage class
src/jni/jg_jnu.c:17: error: syntax error before '*' token
src/jni/jg_jnu.c:17: warning: data definition has no type or storage class
src/jni/jg_jnu.c:20: error: syntax error before 'getPointerField'
src/jni/jg_jnu.c:20: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getPointerField':
src/jni/jg_jnu.c:22: error: syntax error before 'pointerField'
src/jni/jg_jnu.c:23: error: 'pointerField' undeclared (first use in this function)
src/jni/jg_jnu.c:23: error: (Each undeclared identifier is reported only once
src/jni/jg_jnu.c:23: error: for each function it appears in.)
src/jni/jg_jnu.c:24: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:24: error: syntax error before 'handleClass'
src/jni/jg_jnu.c:25: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:26: warning: return makes integer from pointer without a cast
src/jni/jg_jnu.c:34: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:47: error: syntax error before 'jint'
src/jni/jg_jnu.c:47: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'JNI_OnLoad':
src/jni/jg_jnu.c:49: error: 'jvm' undeclared (first use in this function)
src/jni/jg_jnu.c:50: error: 'JNI_VERSION_1_2' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:54: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'JG_JNU_GetEnv':
src/jni/jg_jnu.c:57: error: invalid type argument of '->'
src/jni/jg_jnu.c:57: error: 'JNI_VERSION_1_2' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:63: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'JNU_ThrowByName':
src/jni/jg_jnu.c:78: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:78: error: syntax error before 'cls'
src/jni/jg_jnu.c:80: error: 'cls' undeclared (first use in this function)
src/jni/jg_jnu.c:81: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:81: error: 'msg' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:90: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getStringArray':
src/jni/jg_jnu.c:92: error: 'jsize' undeclared (first use in this function)
src/jni/jg_jnu.c:92: error: syntax error before 'len'
src/jni/jg_jnu.c:93: error: 'len' undeclared (first use in this function)
src/jni/jg_jnu.c:95: error: 'jstring' undeclared (first use in this function)
src/jni/jg_jnu.c:95: error: syntax error before 'aString'
src/jni/jg_jnu.c:98: error: 'aString' undeclared (first use in this function)
src/jni/jg_jnu.c:98: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:98: error: 'anArray' undeclared (first use in this function)
src/jni/jg_jnu.c:99: error: syntax error before 'index'
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:108: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'freeStringArray':
src/jni/jg_jnu.c:110: error: 'jsize' undeclared (first use in this function)
src/jni/jg_jnu.c:110: error: syntax error before 'len'
src/jni/jg_jnu.c:112: error: 'jstring' undeclared (first use in this function)
src/jni/jg_jnu.c:112: error: syntax error before 'aString'
src/jni/jg_jnu.c:114: error: 'len' undeclared (first use in this function)
src/jni/jg_jnu.c:115: error: 'aString' undeclared (first use in this function)
src/jni/jg_jnu.c:115: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:115: error: 'anArray' undeclared (first use in this function)
src/jni/jg_jnu.c:116: error: syntax error before 'index'
src/jni/jg_jnu.c:117: error: 'str' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:121: error: syntax error before 'getJavaStringArray'
src/jni/jg_jnu.c:121: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getJavaStringArray':
src/jni/jg_jnu.c:122: error: 'str' undeclared (first use in this function)
src/jni/jg_jnu.c:123: warning: return makes integer from pointer without a cast
src/jni/jg_jnu.c:129: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:129: error: syntax error before 'stringCls'
src/jni/jg_jnu.c:130: error: 'jobjectArray' undeclared (first use in this function)
src/jni/jg_jnu.c:133: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:133: error: 'ret' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:138: error: syntax error before 'getSList'
src/jni/jg_jnu.c:138: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getSList':
src/jni/jg_jnu.c:140: error: 'jobjectArray' undeclared (first use in this function)
src/jni/jg_jnu.c:140: error: syntax error before 'ar'
src/jni/jg_jnu.c:142: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:142: error: syntax error before 'handleClass'
src/jni/jg_jnu.c:143: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:143: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:145: error: 'list' undeclared (first use in this function)
src/jni/jg_jnu.c:146: warning: return makes integer from pointer without a cast
src/jni/jg_jnu.c:147: error: 'ar' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:156: error: syntax error before 'getList'
src/jni/jg_jnu.c:156: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getList':
src/jni/jg_jnu.c:158: error: 'jobjectArray' undeclared (first use in this function)
src/jni/jg_jnu.c:158: error: syntax error before 'ar'
src/jni/jg_jnu.c:160: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:160: error: syntax error before 'handleClass'
src/jni/jg_jnu.c:161: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:161: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:163: error: 'list' undeclared (first use in this function)
src/jni/jg_jnu.c:164: warning: return makes integer from pointer without a cast
src/jni/jg_jnu.c:165: error: 'ar' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:175: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getPointerFromHandle':
src/jni/jg_jnu.c:179: error: 'handle' undeclared (first use in this function)
src/jni/jg_jnu.c:182: error: 'jfieldID' undeclared (first use in this function)
src/jni/jg_jnu.c:182: error: syntax error before 'pointerField'
src/jni/jg_jnu.c:183: error: 'pointerField' undeclared (first use in this function)
src/jni/jg_jnu.c:186: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:192: error: syntax error before '*' token
src/jni/jg_jnu.c:193: error: 'getHandleFromPointer' declared as function returning a function
src/jni/jg_jnu.c: In function 'getHandleFromPointer':
src/jni/jg_jnu.c:194: error: syntax error before 'constructor'
src/jni/jg_jnu.c:197: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:197: error: syntax error before 'handleClass'
src/jni/jg_jnu.c:198: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:199: warning: return makes integer from pointer without a cast
src/jni/jg_jnu.c:201: error: 'jfieldID' undeclared (first use in this function)
src/jni/jg_jnu.c:201: error: syntax error before 'pointerField'
src/jni/jg_jnu.c:202: error: 'pointerField' undeclared (first use in this function)
src/jni/jg_jnu.c:203: warning: return makes integer from pointer without a cast
src/jni/jg_jnu.c:205: error: 'constructor' undeclared (first use in this function)
src/jni/jg_jnu.c:206: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:208: warning: return makes integer from pointer without a cast
src/jni/jg_jnu.c:212: error: 'jint' undeclared (first use in this function)
src/jni/jg_jnu.c:212: error: syntax error before 'pointer'
src/jni/jg_jnu.c:213: warning: return makes integer from pointer without a cast
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:216: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getPointerArrayFromHandles':
src/jni/jg_jnu.c:220: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:220: error: syntax error before 'handleClass'
src/jni/jg_jnu.c:221: error: 'jsize' undeclared (first use in this function)
src/jni/jg_jnu.c:223: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:223: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:227: error: 'len' undeclared (first use in this function)
src/jni/jg_jnu.c:229: error: 'jfieldID' undeclared (first use in this function)
src/jni/jg_jnu.c:229: error: syntax error before 'pointerField'
src/jni/jg_jnu.c:230: error: 'pointerField' undeclared (first use in this function)
src/jni/jg_jnu.c:234: error: 'handles' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:247: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getArrayFromHandles':
src/jni/jg_jnu.c:253: error: 'jsize' undeclared (first use in this function)
src/jni/jg_jnu.c:253: error: syntax error before 'len'
src/jni/jg_jnu.c:256: error: 'size_of_object' undeclared (first use in this function)
src/jni/jg_jnu.c:256: error: 'len' undeclared (first use in this function)
src/jni/jg_jnu.c:260: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:260: error: 'handles' undeclared (first use in this function)
src/jni/jg_jnu.c:264: error: 'update_handles' undeclared (first use in this function)
src/jni/jg_jnu.c:269: error: 'delete_originals' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:275: error: syntax error before 'getHandleArrayFromPointers'
src/jni/jg_jnu.c:275: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getHandleArrayFromPointers':
src/jni/jg_jnu.c:277: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:277: error: 'pointer' undeclared (first use in this function)
src/jni/jg_jnu.c:277: error: 'numPtrs' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:280: error: syntax error before 'getHandlesFromPointers'
src/jni/jg_jnu.c:280: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getHandlesFromPointers':
src/jni/jg_jnu.c:284: error: 'jobjectArray' undeclared (first use in this function)
src/jni/jg_jnu.c:284: error: syntax error before 'ret'
src/jni/jg_jnu.c:285: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:286: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:286: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:288: error: 'ret' undeclared (first use in this function)
src/jni/jg_jnu.c:288: error: 'numPtrs' undeclared (first use in this function)
src/jni/jg_jnu.c:291: error: function 'handle' is initialized like a variable
src/jni/jg_jnu.c:291: error: 'pointer' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:297: error: syntax error before 'getHandleArrayFromGList'
src/jni/jg_jnu.c:297: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getHandleArrayFromGList':
src/jni/jg_jnu.c:299: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:299: error: 'list' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:302: error: syntax error before 'getHandlesFromGList'
src/jni/jg_jnu.c:302: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getHandlesFromGList':
src/jni/jg_jnu.c:306: error: 'jobjectArray' undeclared (first use in this function)
src/jni/jg_jnu.c:306: error: syntax error before 'ret'
src/jni/jg_jnu.c:307: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:308: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:308: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:310: error: 'ret' undeclared (first use in this function)
src/jni/jg_jnu.c:310: error: 'list' undeclared (first use in this function)
src/jni/jg_jnu.c:313: error: function 'handle' is initialized like a variable
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:319: error: syntax error before 'getHandleArrayFromGSList'
src/jni/jg_jnu.c:319: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getHandleArrayFromGSList':
src/jni/jg_jnu.c:321: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:321: error: 'list' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:324: error: syntax error before 'getHandlesFromGSList'
src/jni/jg_jnu.c:324: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getHandlesFromGSList':
src/jni/jg_jnu.c:329: error: 'jobjectArray' undeclared (first use in this function)
src/jni/jg_jnu.c:329: error: syntax error before 'ret'
src/jni/jg_jnu.c:330: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:331: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:331: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:333: error: 'ret' undeclared (first use in this function)
src/jni/jg_jnu.c:333: error: 'list' undeclared (first use in this function)
src/jni/jg_jnu.c:336: error: function 'handle' is initialized like a variable
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:342: error: syntax error before 'getHandleArray'
src/jni/jg_jnu.c:342: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getHandleArray':
src/jni/jg_jnu.c:344: error: 'jobjectArray' undeclared (first use in this function)
src/jni/jg_jnu.c:344: error: syntax error before 'ret'
src/jni/jg_jnu.c:345: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:346: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:346: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:348: error: 'ret' undeclared (first use in this function)
src/jni/jg_jnu.c:348: error: 'length' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:352: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getGSListFromHandles':
src/jni/jg_jnu.c:354: error: 'handles' undeclared (first use in this function)
src/jni/jg_jnu.c:359: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:359: error: syntax error before 'handleClass'
src/jni/jg_jnu.c:360: error: 'jsize' undeclared (first use in this function)
src/jni/jg_jnu.c:362: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:362: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:367: error: 'jfieldID' undeclared (first use in this function)
src/jni/jg_jnu.c:367: error: syntax error before 'pointerField'
src/jni/jg_jnu.c:368: error: 'pointerField' undeclared (first use in this function)
src/jni/jg_jnu.c:371: error: 'len' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:378: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getGListFromHandles':
src/jni/jg_jnu.c:380: error: 'handles' undeclared (first use in this function)
src/jni/jg_jnu.c:385: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:385: error: syntax error before 'handleClass'
src/jni/jg_jnu.c:386: error: 'jsize' undeclared (first use in this function)
src/jni/jg_jnu.c:388: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:388: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:393: error: 'jfieldID' undeclared (first use in this function)
src/jni/jg_jnu.c:393: error: syntax error before 'pointerField'
src/jni/jg_jnu.c:394: error: 'pointerField' undeclared (first use in this function)
src/jni/jg_jnu.c:397: error: 'len' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:404: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getGListFromStringArray':
src/jni/jg_jnu.c:405: error: 'strings' undeclared (first use in this function)
src/jni/jg_jnu.c:410: error: 'jsize' undeclared (first use in this function)
src/jni/jg_jnu.c:410: error: syntax error before 'len'
src/jni/jg_jnu.c:412: error: 'jstring' undeclared (first use in this function)
src/jni/jg_jnu.c:415: error: 'len' undeclared (first use in this function)
src/jni/jg_jnu.c:416: error: 'strobj' undeclared (first use in this function)
src/jni/jg_jnu.c:416: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:424: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'releaseStringArrayInGList':
src/jni/jg_jnu.c:426: error: 'jstring' undeclared (first use in this function)
src/jni/jg_jnu.c:426: error: syntax error before 'aString'
src/jni/jg_jnu.c:429: error: 'list' undeclared (first use in this function)
src/jni/jg_jnu.c:430: error: 'aString' undeclared (first use in this function)
src/jni/jg_jnu.c:430: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:430: error: 'strings' undeclared (first use in this function)
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:437: error: syntax error before '*' token
src/jni/jg_jnu.c:438: error: 'updateHandle' declared as function returning a function
src/jni/jg_jnu.c: In function 'updateHandle':
src/jni/jg_jnu.c:439: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:439: error: syntax error before 'handleClass'
src/jni/jg_jnu.c:440: error: 'handleClass' undeclared (first use in this function)
src/jni/jg_jnu.c:440: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:443: error: 'handle' undeclared (first use in this function)
src/jni/jg_jnu.c:445: error: 'jfieldID' undeclared (first use in this function)
src/jni/jg_jnu.c:445: error: syntax error before 'pointerField'
src/jni/jg_jnu.c:446: error: 'pointerField' undeclared (first use in this function)
src/jni/jg_jnu.c:448: error: 'jint' undeclared (first use in this function)
src/jni/jg_jnu.c:448: error: syntax error before 'pointer'
src/jni/jg_jnu.c: At top level:
src/jni/jg_jnu.c:453: error: syntax error before 'getHandleClass'
src/jni/jg_jnu.c:453: error: syntax error before '*' token
src/jni/jg_jnu.c: In function 'getHandleClass':
src/jni/jg_jnu.c:455: error: syntax error before 'handleCls'
src/jni/jg_jnu.c:456: error: 'handleCls' undeclared (first use in this function)
src/jni/jg_jnu.c:457: error: 'jclass' undeclared (first use in this function)
src/jni/jg_jnu.c:457: error: syntax error before 'localHandleCls'
src/jni/jg_jnu.c:461: error: 'localHandleCls' undeclared (first use in this function)
src/jni/jg_jnu.c:461: error: 'env' undeclared (first use in this function)
src/jni/jg_jnu.c:466: warning: return makes integer from pointer without a cast
make[5]: *** [src/jni/jg_jnu.lo] Error 1
make[5]: Leaving directory `/home/bobz/garnome-2.16.0/bindings/glib-java/work/main.d/glib-java-0.3.2'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/bobz/garnome-2.16.0/bindings/glib-java/work/main.d/glib-java-0.3.2'
make[3]: *** [build-work/main.d/glib-java-0.3.2/Makefile] Error 2
make[3]: Leaving directory `/home/bobz/garnome-2.16.0/bindings/glib-java'
make[2]: *** [../../bindings/glib-java/cookies/main.d/install] Error 2
make[2]: Leaving directory `/home/bobz/garnome-2.16.0/bindings/cairo-java'
make[1]: *** [paranoid-install] Error 2
make[1]: Leaving directory `/home/bobz/garnome-2.16.0/bindings'
make: *** [paranoid-install] Error 2

```

I beleive it has something to do with the correct jdk files being present, but I do not know which ones? Thankx for your help in advance!:oops:

---

### Post by sbmd on 2006-09-08
I have been searching but can not find much on the above error, may be I am searching for it wrong, wrong term or something. But any insight on this would be great. Thankx for all your help, this is one of the best communities on the net!!:-D

---

### Post by eitch on 2006-09-08
Hmm.... sadly I have the same error with the 

glib-java-0.3.2

compile... Something about either the wrong gcj binaries installed or it can't locate the right files... but can't I just use Sun's SDK? 

Any help would be appreciated.

---

