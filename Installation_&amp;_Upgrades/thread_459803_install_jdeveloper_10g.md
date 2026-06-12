---
title: "install jdeveloper 10g"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by rajankarthickbabu on 2007-05-31
error : jdeveloper.exe: No application suitable for automatic installation is available for handling this kind of file.

while try to run its shows above  error.... anyone help me to configure or install it give me a steps

---

### Post by aamr on 2007-08-29
I still don't know how to run it as I'm still downloading it, but what I'm sure of is that you can't run .exe files on Linux, you'll find another alternative for that file to run on Linux.

---

### Post by nicolasdiogo on 2007-09-26
:popcorn:

hi are you still trying to run jdev?

---

### Post by nelson.bolanos on 2007-10-26
After you unzip the jdeveloper package, you should try browsing to $JDEV_PATH/jdev/bin, and executing ./jdev.

I'm having trouble displaying jdev, it runs and all, but I cant see anything inside it, I guess its because I running compiz(sqldeveloper had a similar issue), so I'll try the same fix.

Tk Care.
:popcorn:

---

### Post by nelson.bolanos on 2007-10-26
Googling, I found this 2 great answers in other forums :

modify the jdev script place this on the second line

export AWT_TOOLKIT=MToolkit


or,

Download and install xnest or xephyr "sudo apt-get install xnest" or "sudo apt-get install xserver-xephyr"

and add this to your jdev script.

#!/bin/bash
Xephyr :2 -ac -screen 1024x768 &
icewm --display :2 &
export DISPLAY=:2
/opt/netbeans/bin/netbeans &

Hope this solves your issue.

:guitar:

---

### Post by tammersalem on 2007-11-26
Hi I used:

```
export AWT_TOOLKIT=MToolkit
```

and it worked fine.

---

