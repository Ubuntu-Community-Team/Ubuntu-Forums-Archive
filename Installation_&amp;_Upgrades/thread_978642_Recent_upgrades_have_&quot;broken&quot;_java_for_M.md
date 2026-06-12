---
title: "Recent upgrades have &quot;broken&quot; java for Matlab and MIPAV - SIGSEGV/libc.so.6 problems"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by bennett172 on 2008-11-11
I recently applied the latest 8.04 patch and Matlab 2008a/2008b and MIPAV ([http://mipav.cit.nih.gov/](http://mipav.cit.nih.gov/)) started crashing. Both require Sun's java jvm. The error message for both programs is the same (as follows). I upgraded to 8.10, but the problem remains. 

Any help would be greatly appreciated. 
-Bennett

 #8 [0x7fd7d8fd9878]

#

# An unexpected error has been detected by Java Runtime Environment:

#

#  SIGSEGV (0xb) at pc=0x00007fd7dda9b5af, pid=10095, tid=1084684624

#

# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b19 mixed mode linux-amd64)

# Problematic frame:

# C  [libc.so.6+0x315af]  catgets+0x1f

#

# An error report file with more information is saved as:

# /usr/local/matlab-2008b/hs_err_pid10095.log

#

# If you would like to submit a bug report, please visit:

#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)

# The crash happened outside the Java Virtual Machine in native code.

# See problematic frame for where to report the bug.

#

Aborted


Another note: I have always had the following error message on startup (and it is still there), but it has never caused any problems: 
#0 /usr/lib/libxcb-xlib.so.0 [0x7fd7915b29fc]

#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7fd7915b2ab4]

#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7fd79202f698]

#3 /usr/local/matlab-2008b/sys/java/jre/glnxa64/jre/lib/amd64/motif21/libmawt.so [0x7fd792c16096]

#4 /usr/local/matlab-2008b/sys/java/jre/glnxa64/jre/lib/amd64/motif21/libmawt.so [0x7fd792bc2bfb]

#5 /usr/local/matlab-2008b/sys/java/jre/glnxa64/jre/lib/amd64/motif21/libmawt.so [0x7fd792bc2ecd]

#6 /usr/local/matlab-2008b/sys/java/jre/glnxa64/jre/lib/amd64/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7fd792bc3142]

#7 [0x7fd7d8fd9878]

Locking assertion failure.  Backtrace:

#0 /usr/lib/libxcb-xlib.so.0 [0x7fd7915b29fc]

#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7fd7915b2b77]

#2 /usr/lib/libX11.so.6 [0x7fd79202e8c0]

#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x2e) [0x7fd79202508e]

#4 /usr/local/matlab-2008b/sys/java/jre/glnxa64/jre/lib/amd64/motif21/libmawt.so [0x7fd792bc1f25]

#5 /usr/local/matlab-2008b/sys/java/jre/glnxa64/jre/lib/amd64/motif21/libmawt.so [0x7fd792bc2179]

#6 /usr/local/matlab-2008b/sys/java/jre/glnxa64/jre/lib/amd64/motif21/libmawt.so [0x7fd792bc2f6f]

#7 /usr/local/matlab-2008b/sys/java/jre/glnxa64/jre/lib/amd64/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7fd792bc3142]

---

### Post by bennett172 on 2008-11-12
As a follow-up note, this issue appears to be related to some permission somewhere. I can run mipav as root (sudo -i), but not as my regular user. This is not a work around for Matlab because Matlab is locked to my username. Does anyone know what permissions might have changed that would cause java to throw this type of critical error? 

Thanks!
Bennett

---

### Post by bennett172 on 2008-11-13
Just to follow up with a fix. Apparently one of the upgrades caused this environment variables to start crashing things. 

Thanks Mathworks Support!


This error can also be the result of having the environment variable: 

AWT_TOOLKIT=MLtoolkit 

set on this machine.  To resolve this error, you can unset this variable and try running MATLAB again.

---

