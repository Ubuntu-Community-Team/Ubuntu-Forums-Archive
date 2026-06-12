---
title: "I can't Login!!!"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by Splower on 2008-02-27
Re: I cant login!
I have almost the same problem, but, it started right after I installed xserver......

I get this when I run "tail -24 ~/.xsession-errors":

Refusing to initialize GTK+.

(process:5214): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present.
Starting Xgl with options: -accel xvbuffer -accel glxbuffer -nolisten tcp -fullscreen -br +xinerama

Fatal server error:
no screens found
rm: cannot remove `/tmp/.X1-lock': No such file or directory
xmodmap: unable to open display ':1'

(x-session-manager:5207): Gtk-WARNING **: cannot open display:
__________________

---

### Post by dstew on 2008-02-27
> I have almost the same problem, but, it started right after I installed xserver......How did you install xserver?

---

### Post by Rocket2DMn on 2008-02-27
Have you tried reconfiguring X?  Try this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you need more help, please post back the output of these commands:
```
cat /etc/X11/xorg.conf
lspci | grep VGA
```
If you know your video card make/model, post that too, although that last command should tell us.

---

### Post by arpad9 on 2008-03-02
This seems to be a common problem which could occur if permission are wrong on /tmp.

Make sure /tmp is 777.  Since /tmp should only be used for temporary data, IMHO, you could remove everything in it and reboot but don't quote me on that - though it's what I would do :-)

Arpad

---

