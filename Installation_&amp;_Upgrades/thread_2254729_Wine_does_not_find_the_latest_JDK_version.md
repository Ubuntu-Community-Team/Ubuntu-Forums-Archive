---
title: "Wine does not find the latest JDK version ?"
date: 2014-11-29
forum: Installation &amp; Upgrades
---

### Post by zn52 on 2014-11-29
[COLOR=#000000]hello,[/COLOR]
[COLOR=#000000]I want to run an .EXE file which exists in the windows directory under Program files - It runs well under windows . but as I'm anti-windows, I wanted to execute it in ubuntu.[/COLOR]
[COLOR=#000000]But I get the message : this application requires a java runtime environment 1.7.0_51 or higher[/COLOR]
[COLOR=#000000]But in the terminal I have the latest :[/COLOR]

[COLOR=#000000]java - version[/COLOR]
[COLOR=#000000]java version "1.8.0_11"[/COLOR]
[COLOR=#000000]Java(TM) SE Runtime Environment (build 1.8.0_11-b12)[/COLOR]
[COLOR=#000000]Java HotSpot(TM) Server VM (build 25.11-b03, mixed mode)[/COLOR]

[COLOR=#000000]How come it does not recognize the JDK version ?[/COLOR]
[COLOR=#000000]thank you,[/COLOR]

---

### Post by kostkon on 2014-11-29
If it's an Java app, then the first thing you need to do is check whether the author distributes the app in other formats, namely as jar or at least as a zip file.

If that's not the case, you could try right-clicking on the exe file and selecting to open it with the archive manager. After doing that, you could try extracting its contents. If that's successful, then try running it with your installed jvm.

If you can't extract the contents of the exe, then you need to install the windows version of Java in Wine and try to run it with Wine.


Hope that helps.

---

