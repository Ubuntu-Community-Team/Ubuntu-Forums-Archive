---
title: "gnome-settings-deamon crash"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by iph1ps99 on 2013-12-04
Hey,
I am getting this error when I try to manually start gnome-settings-daemon: ```
[B]Gdk-ERROR **: The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 179 error_code 8 request_code 140 minor_code 30)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/B]


```

If my system tries to start the same error appears. Can sombody help me?

---

### Post by ibjsb4 on 2013-12-05
Could it be a bug?

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1228585](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1228585)

I have not encountered this error, but others have

[https://www.google.com/search?client=ubuntu&channel=fs&q=Gdk-ERROR+**%3A+The+program+%27gnome-settings-daemon%27+received+an+X+Window+System+error.&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Gdk-ERROR+**%3A+The+program+%27gnome-settings-daemon%27+received+an+X+Window+System+error.&ie=utf-8&oe=utf-8)

---

