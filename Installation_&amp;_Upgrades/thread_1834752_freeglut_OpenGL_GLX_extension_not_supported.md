---
title: "freeglut OpenGL GLX extension not supported"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by iapx86 on 2011-08-28
I just installed ubuntu 11.04 32 bit
then used synaptic package manager to install pyopencl.
When I try to run pyopencl I get:

[U]Xlib: extension “GLX” missing on display “:0.0&#8243;.
freeglut (main.py): OpenGL GLX extension not supported by display ‘:0.0&#8242;[/U]

When I try to use python pyglet I get many messages including:

_pyglet.gl.glx_info.GLXInfoException: pyglet requires an X server with GLX_

Please advise how to fix this.

pyglet worked correctly on my ubuntu 9.10.

---

### Post by dino99 on 2011-08-28
if you still have xorg.conf:

replace in /etc/X11/xorg.conf (Section "Module")
Load "GLX" to Load "glx" (glx MUST be written with lower case letters!!!)

or remove it as now kernel directly deal with X, so no need of xorg.conf
(old config like CRT or TV sometimes need it because of vertical/horizontal frequencies or else)

sudo rm /etc/X11/xorg.conf

---

### Post by iapx86 on 2011-08-28
Thank you for the response and links.
As you said, there is no file /etc/X11/xorg.conf.
I followed the links, searching for GLX and for freeglut.
I also spent many hours trying to find solutions elsewhere.
The problem is unchanged, but the system is also unchanged.

Do you have any other ideas I could try?

---

### Post by dino99 on 2011-08-28
i'm still searching too, found this doc from synaptic:

" GLUT is designed for constructing small to medium sized OpenGL programs,
however it is not a full-featured toolkit, so large applications requiring
sophisticated user interfaces are better off using native window system
toolkits like GTK+ or Motif. "

so i may ask why you have chosen freeglut ?

[http://www.codeproject.com/KB/openGL/firstGLwindow.aspx?display=Mobile](http://www.codeproject.com/KB/openGL/firstGLwindow.aspx?display=Mobile)

[http://salemsayed.me/?p=164](http://salemsayed.me/?p=164)

[http://www.docstoc.com/docs/31383175/Configuring-Eclipse-and-freeglut-on-Windows-and-Ubuntu-Linux](http://www.docstoc.com/docs/31383175/Configuring-Eclipse-and-freeglut-on-Windows-and-Ubuntu-Linux)

---

### Post by iapx86 on 2011-08-28
I appreciate how quickly you are responding.

Installing freeglut3 was not a choice.
It was installed with pyopengl automatically with pyopencl.
pyopengl is also important to me for other projects.

Synaptic Package Manager removes pyopengl when freeglut3 is removed.
Removing freeglut3 caused problems.
It took removing and reinstalling pyopencl completely
to get back to the original error state.

I still need help.

---

### Post by dino99 on 2011-08-28
as i've no experience with this , i only propose the main doc, sorry if you already know it :(:

[http://pyopengl.sourceforge.net/documentation/](http://pyopengl.sourceforge.net/documentation/)

at least report a bug on launchpad:

ubuntu-bug python-opengl

---

### Post by iapx86 on 2011-08-28
Thank you.
I will report this as a bug as you suggested.

---

### Post by iapx86 on 2011-08-28
Apologies, I am new to ubuntu forums.
When I tried to do as you suggested
I found the thread we have been using.

I don't know how to report the bug as you suggested.
Can you give me more detailed information?
Is there a "best" URL from which to start?

---

