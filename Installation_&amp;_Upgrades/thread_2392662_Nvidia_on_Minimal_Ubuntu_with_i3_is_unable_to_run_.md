---
title: "Nvidia on Minimal Ubuntu with i3 is unable to run 3D"
date: 2018-05-23
forum: Installation &amp; Upgrades
---

### Post by Notsgnik on 2018-05-23
Hello, i just installed an ubuntu minimal following this tutorial: [https://gist.github.com/richardjuan/33db032a0dc4ae66f216436dd4ec3e5f](https://gist.github.com/richardjuan/33db032a0dc4ae66f216436dd4ec3e5f).

The nvidia drivers seems to be loaded but I can't run glxgears or run a webgl demo, yet I can watch videos on youtube.

Before installing them everything was working but 3D was slow.
I don't know where to look for :/

```

$ glxinfo | egrep "OpenGL vendor|OpenGL renderer*"
Error: couldn't find RGB GLX visual or fbconfig

```

---

