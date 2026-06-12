---
title: "Linkage problem after upgrade to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by ArthurH on 2011-10-15
Upgrade from 11.04 to 11.10 worked fine, but getting linkage problems. In 11.04 CodeBlock built my project using Mesa OpenGL Utility library (specifically libglu1-mesa...) and ran no problems. In 11.10 the same build complains that the  gluPerspective (and many other glu routines) cannot be found (but it does compile). It's like the library doesn't exist any more. What happened?  I know libglu1 is static and libGL is shared. Is that an issue now in 11.10?

---

