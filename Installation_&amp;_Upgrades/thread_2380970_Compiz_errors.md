---
title: "Compiz errors"
date: 2017-12-24
forum: Installation &amp; Upgrades
---

### Post by pliam1105 on 2017-12-24
I have Windows 10 64bit and I have installed the Ubuntu subsystem on Windows. I have installed ubuntu-desktop, unity, compiz and compiz configuration settings.But when I type compiz on Ubuntu bash, I get the following errors :

```
compiz (core) - Info: Loading plugin: core

compiz (core) - Info: Starting plugin: core

compiz (core) - Info: Loading plugin: ccp

compiz (core) - Info: Starting plugin: ccp

compizconfig - Info: Backend     : ini

compizconfig - Info: Integration : true

compizconfig - Info: Profile     : default

compiz (core) - Info: Loading plugin: composite

compiz (core) - Info: Starting plugin: composite

compiz (core) - Info: Loading plugin: opengl

compiz (core) - Info: Starting plugin: opengl

libGL error: No matching fbConfigs or visuals found

libGL error: failed to load driver: swrast

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

compiz (core) - Error: Plugin initScreen failed: opengl

compiz (core) - Error: Failed to start plugin: opengl

compiz (core) - Info: Unloading plugin: opengl

compiz (core) - Info: Loading plugin: place

compiz (core) - Info: Starting plugin: place

compiz (core) - Info: Loading plugin: resize

compiz (core) - Info: Starting plugin: resize
Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual


Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual

compiz (core) - Info: Loading plugin: snap

compiz (core) - Info: Starting plugin: snap

compiz (core) - Info: Loading plugin: commands

compiz (core) - Info: Starting plugin: commands

compiz (core) - Info: Loading plugin: compiztoolbox

compiz (core) - Info: Starting plugin: compiztoolbox

compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Info: Loading plugin: copytex

compiz (core) - Info: Starting plugin: copytex

compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: copytex

compiz (core) - Error: Failed to start plugin: copytex

compiz (core) - Info: Unloading plugin: copytex

compiz (core) - Info: Loading plugin: imgpng

compiz (core) - Info: Starting plugin: imgpng

compiz (core) - Info: Loading plugin: move

compiz (core) - Info: Starting plugin: move

compiz (core) - Info: Loading plugin: scale

compiz (core) - Info: Starting plugin: scale

compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: scale

compiz (core) - Error: Failed to start plugin: scale

compiz (core) - Info: Unloading plugin: scale

compiz (core) - Info: Loading plugin: expo

compiz (core) - Info: Starting plugin: expo

compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: expo

compiz (core) - Error: Failed to start plugin: expo

compiz (core) - Info: Unloading plugin: expo

compiz (core) - Info: Loading plugin: unityshell

compiz (core) - Info: Starting plugin: unityshell

compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: unityshell

compiz (core) - Error: Failed to start plugin: unityshell

compiz (core) - Info: Unloading plugin: unityshell

Compiz (opengl) - Fatal: Root visual is not a double buffered GL visual
```
and a black screen with nothing on it. Unity doesn't load. What can I do to solve this problem?

---

### Post by monkeybrain20122 on 2017-12-24
How did you install Ubuntu as a "subsystem" of Windows? There is no such thing unless you mean  virtual machine.

---

### Post by deadflowr on 2017-12-24
> **monkeybrain20122 said:**
> How did you install Ubuntu as a "subsystem" of Windows? There is no such thing unless you mean  virtual machine.

I think this:
[https://docs.microsoft.com/en-us/windows/wsl/about]("https://docs.microsoft.com/en-us/windows/wsl/about")

---

