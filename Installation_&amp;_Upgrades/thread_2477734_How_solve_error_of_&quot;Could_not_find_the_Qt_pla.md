---
title: "How solve error of &quot;Could not find the Qt platform plugin&quot; in Conda on Ubuntu 22.04 ?"
date: 2022-08-05
forum: Installation &amp; Upgrades
---

### Post by GwibberFooey on 2022-08-05
I installed Conda onto (Mate)Ubuntu 22.04 X86_64. I have a Python script that looks like this:
```
import matplotlib.pyplot as plt
plt.plot([0,0,1,1],[0,-1/3,-1/3,0])
```

When I run that script, then I get an error message that looks like this:
```
qt.qpa.plugin: Could not find the Qt platform plugin "xcb" in ""
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

Available platform plugins are: eglfs, minimal, minimalegl, offscreen, vnc, webgl.

Aborted (core dumped)
```

What is the recommended procedure to get ```
import matplotlib.pyplot as plt
``` to function using Conda on Ubuntu 22.04?


For the record, the question that I am now posing is more or less a direct reformulation of the question that I posed some 17 hours earlier at Stack Overflow:
[https://stackoverflow.com/questions/73239265/how-to-solve-the-error-of-could-not-find-the-qt-platform-plugin-in-conda-on-ub](https://stackoverflow.com/questions/73239265/how-to-solve-the-error-of-could-not-find-the-qt-platform-plugin-in-conda-on-ub)

---

