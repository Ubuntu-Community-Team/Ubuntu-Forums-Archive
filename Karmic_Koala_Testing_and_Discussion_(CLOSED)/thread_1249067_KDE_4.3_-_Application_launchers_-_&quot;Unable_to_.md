---
title: "KDE 4.3 - Application launchers - &quot;Unable to make the service executable&quot;"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by skullmunky on 2009-08-24
I installed kde 4.3 on Jaunty from the backports ppa.  I've just run into a problem with the .desktop launcher for Maya 2009.  When I try to launch it from the application menu, nothing happens.  When I drag the icon to the panel and launch it from there, it asks if I trust the program.  If I click continue, I get this error:
```

Unable to make the service Autodesk Maya 2009 (64-bit) executable, aborting execution

```

---

### Post by Gen2ly on 2009-08-24
Try to look at the .desktop file with a text editor and find out how to run the program from the command line and see if it gives you any other useful feedback.  My guess from that short blurb would be that possibly you are trying to start a 64-bit executable on a 32-bit system.

---

### Post by skullmunky on 2009-08-26
the actual executable works fine (/usr/autodesk/maya2009-x64/bin/maya).  the desktop file in /usr/share/applications is a link to /usr/autodesk/maya2009-x64/desktop/Autodesk-Maya.desktop

```

[Desktop Entry]
Name=Autodesk Maya 2009 (64-bit)
Type=Application
Comment=Run Autodesk Maya 2009 (64-bit)
Categories=Application;Graphics;3DGraphics
Icon=Maya2009.png
Exec=/usr/autodesk/maya2009-x64/bin/maya
Encoding=UTF-8

```

---

### Post by OutOfReach on 2009-08-26
Hmm, I think that the .desktop file is not executable.
Try going into the directory were the .desktop file is at, and doing:
```

chmod +x DESIRED_FILE.desktop

```
You'll most likely need root permissions so do it as sudo

---

### Post by skullmunky on 2009-09-14
Thanks, that did solve it.  But why does the file need to be executable?  None of the ones for other applications are executable, and .desktop files are not executed anyway...:confused:

---

### Post by inportb on 2009-09-14
They do contain commands to be executed, though.

---

