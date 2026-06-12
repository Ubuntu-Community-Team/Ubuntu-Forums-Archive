---
title: "Bad problem &quot;making&quot; Intel Video Driver"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Totonno on 2006-11-06
Hello!
I'm compiling the Intel Drivers for my i915 Video Card but when I run 
"make World"
I get :

make[3]: Leaving directory `/xc/include/fonts'
installing in include/GL...
make[3]: Entering directory `/xc/include/GL'
make[3]: *** No rule to make target `/X11R6/SourceForge/Mesa6.2/Mesa/include/GL/gl.h', needed by `gl.h'.  Stop.
make[3]: Leaving directory `/xc/include/GL'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/xc/include'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/xc'
make: *** [install] Error 2


and it's 2 days I'm completely stuck. I'm searching on the web for a solution, but no success...Can someone help me please?

Thanks very much!

---

