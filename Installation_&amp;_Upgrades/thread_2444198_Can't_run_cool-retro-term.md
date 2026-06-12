---
title: "Can't run cool-retro-term"
date: 2020-05-26
forum: Installation &amp; Upgrades
---

### Post by cutefatseal331 on 2020-05-26
Hello.

So I recently wanted to run cool-retro-term on my Windows installation, but it's a Linux app.

So I went and installed Linux subsystem for Windows, Ubuntu 20.04 shell and Xming (I need an X-server, right?)

I compiled cool-retro-term, but, when I try to run it, this happens:

```
seal@mymachinename:/mnt/c/Users/myusername/coolretroterm/cool-retro-term$ ./cool-retro-term
qt.qpa.xcb: X server does not support XInput 2
failed to get the current screen resources
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-seal'
QQmlApplicationEngine failed to load component
qrc:/main.qml:137 Type TerminalContainer unavailable
qrc:/TerminalContainer.qml:23 Type PreprocessedTerminal unavailable
qrc:/PreprocessedTerminal.qml:97 Cannot assign to non-existent property "blinkingCursor"


Cannot load QML interface
seal@mymachinename:/mnt/c/Users/myusername/coolretroterm/cool-retro-term$
```

Please help or redirect me to a different forum if this one doesn't deal with Ubuntu on WSL.

---

