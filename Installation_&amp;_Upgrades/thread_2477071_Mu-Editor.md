---
title: "Mu-Editor???"
date: 2022-07-13
forum: Installation &amp; Upgrades
---

### Post by sgordon777 on 2022-07-13
I've tried to install this thing, a code editor for Circuit Python three ways, each without success:

1. Download app-image: WHen I made the file executable and run it, it gives me some error about a dependency, FUSE/libfuse.2.so  I think (isn't the entire point of AppImage to package all the dependencies into one file??)

2. apt install. After a huge install with tons of dependencies, it also fails to run with some stupid error(message below):
stepheng@stepheng-Inspiron-7405-2n1:~$ mu-editor
{CUT bunch of stuff}
TypeError: arguments did not match any overloaded call:
  move(self, QPoint): argument 1 has unexpected type 'float'
  move(self, int, int): argument 1 has unexpected type 'float'
stepheng@stepheng-Inspiron-7405-2n1:~$ 

3. Use the Ubuntu installer
Same failure mode as #2.

**{UPDATE: Failed with snap too}**
4. Install with snap
snap install --edge mu-editor

# no sudo
stepheng@stepheng-Inspiron-7405-2n1:~$ mu-editor
Logging to /home/stepheng/snap/mu-editor/common/.cache/mu/log/mu.log
This application failed to start because it could not find or load the Qt platform plugin "wayland-egl".


Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, xcb.


Reinstalling the application may fix this problem.
Aborted (core dumped)

#with sudo
stepheng@stepheng-Inspiron-7405-2n1:~$ sudo mu-editor
[sudo] password for stepheng: 
mkdir: cannot create directory '/run/user/0': Permission denied
Logging to /root/snap/mu-editor/common/.cache/mu/log/mu.log
Authorization required, but no authorization protocol specified
QXcbConnection: Could not connect to display :0
Aborted
stepheng@stepheng-Inspiron-7405-2n1:~$ 





So 4 ways of installling Mu-editor on the latest version of Ubunto have failed


Does anybody have this running? How'd you do it?

---

### Post by Xian on 2022-07-14
Hmmmmm ..... you may consider to give pip a try. 

[https://ubunlog.com/en/mu-editor-python-principantes/](https://ubunlog.com/en/mu-editor-python-principantes/)

---

