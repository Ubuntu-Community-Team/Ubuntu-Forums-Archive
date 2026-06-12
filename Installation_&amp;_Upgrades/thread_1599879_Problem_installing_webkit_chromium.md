---
title: "Problem installing webkit chromium"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by bakie on 2010-10-18
Hello, I have installed the basis webkit (build-webkit) without any problems. But now I wanted to install chromium (build-webkit --chromium) and I keep getting this error:

WebKit/chromium/app/gtk_dnd_util.h:14: fatal error: third_party/WebKit/WebKit/chromium/public/WebDragOperation.h: No such file or directory
compilation terminated.
make: *** [out/Release/obj.target/app_base/WebKit/chromium/app/gtk_dnd_util.o] Error 1

I have tried to find a solution with google, but still can't fix it.

Thx in advance.

---

### Post by bakie on 2010-10-18
I fixed the previous problem, I just replaced the wrong path to the correct one in the file. But now I get a new error:

Illegal instruction
make: *** [out/Release/obj.host/geni/third_party/yasm/x86insn_nasm.c] Error 132

---

### Post by bakie on 2010-10-19
No one ever tried to compile webkit chromium ?

---

