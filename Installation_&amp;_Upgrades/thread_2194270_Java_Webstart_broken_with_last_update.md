---
title: "Java Webstart broken with last update?"
date: 2013-12-17
forum: Installation &amp; Upgrades
---

### Post by NYxkCsy on 2013-12-17
Anyone else finding that jnlp files won't start since the last update to 12.04. Mostly I'm getting file not found errors. There are some references to this on older Ubuntu versions but the directory structure has changed so the solutions are different. Specific file I'm trying to run is bitminter.jnlp from bitminter.com.
When I try to run from terminal "javaws https://bitminter.com/bitminter.jnlp" I get a Fatal read error - could not read or parse the jnlp file with the following details.

net.sourceforge.jnlp.LaunchException: Fatal: Read Error: Could not read or parse the JNLP file. 
    at net.sourceforge.jnlp.Launcher.fromUrl(Launcher.java:491)
    at net.sourceforge.jnlp.Launcher.launch(Launcher.java:283)
    at net.sourceforge.jnlp.runtime.Boot.run(Boot.java:211)
    at net.sourceforge.jnlp.runtime.Boot.run(Boot.java:53)
    at java.security.AccessController.doPrivileged(Native Method)
    at net.sourceforge.jnlp.runtime.Boot.main(Boot.java:177)
Caused by: java.io.IOException: [https://bitminter.com/bitminter.jnlp](https://bitminter.com/bitminter.jnlp)
    at net.sourceforge.jnlp.JNLPFile.openURL(JNLPFile.java:282)
    at net.sourceforge.jnlp.JNLPFile.<init>(JNLPFile.java:204)
    at net.sourceforge.jnlp.JNLPFile.<init>(JNLPFile.java:188)
    at net.sourceforge.jnlp.JNLPFile.<init>(JNLPFile.java:173)
    at net.sourceforge.jnlp.JNLPFile.<init>(JNLPFile.java:159)
    at net.sourceforge.jnlp.Launcher.fromUrl(Launcher.java:477)
    ... 5 more
Caused by: 
java.io.IOException: [https://bitminter.com/bitminter.jnlp](https://bitminter.com/bitminter.jnlp)
    at net.sourceforge.jnlp.JNLPFile.openURL(JNLPFile.java:282)
    at net.sourceforge.jnlp.JNLPFile.<init>(JNLPFile.java:204)
    at net.sourceforge.jnlp.JNLPFile.<init>(JNLPFile.java:188)
    at net.sourceforge.jnlp.JNLPFile.<init>(JNLPFile.java:173)
    at net.sourceforge.jnlp.JNLPFile.<init>(JNLPFile.java:159)
    at net.sourceforge.jnlp.Launcher.fromUrl(Launcher.java:477)
    at net.sourceforge.jnlp.Launcher.launch(Launcher.java:283)
    at net.sourceforge.jnlp.runtime.Boot.run(Boot.java:211)
    at net.sourceforge.jnlp.runtime.Boot.run(Boot.java:53)
    at java.security.AccessController.doPrivileged(Native Method)
    at net.sourceforge.jnlp.runtime.Boot.main(Boot.java:177)

---

