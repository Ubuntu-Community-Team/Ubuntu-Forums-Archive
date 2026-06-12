---
title: "X not working"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by jon4paz on 2007-10-10
X is not working from either my Dell server or my SSH/Putty session. 

My ultimate goal is just to get Webmin working so I can administer remotely

When I have monitor connected to server it looks like it is trying to put a window together but it looks like it can't find the right fonts to use. 

I get a message that says it can't start X and gives me the option to look at something. When I say yes, there is still the funky window and just an option to quit. When I do I am back at the command line.

I have an ATI Rage XL on motherboard. I have tried the VESA option, tried different Horiz & Vert frequency (Samsung SyncMaster 770TFT) and depth (24 ->16 ->8). My highest display mode is 1024x768.

I looked at my /etc/X11/xinti/xserverrc

exec /usr/bin/X11/X -dpi 100 -nolisten tcp

I changed this to -dpi 75 but nothing changed.


when i run the command "startx x" this is what I get

xauth: creating new authority file /home/j/.serverauth.5640

xauth: error in locking authority file /home/j/.Xauthority (repeats several times)

xinit: Server error.

xauth: error in locking authority file /home/j/.Xauthority

Couldnt get a file descriptor referring to the console.


I have looked at the log and it contains:

xinit: connection refused (errno 111): unable to connect to x server

xinit: No such process (error 3): server error.

I use ubuntu 7.04 server

Thanks for your help

The font directories I find are:
 
/usr/share/fonts/X11/75dpi  -- this is the directory listed in the Files section of /etc/X11/xorg.conf
   this folder only contains one item: fonts.alias
/usr/share/fonts/X11/encodings/ lots of .gz files
/usr/share/fonts/X11/encodings/encoding.dir
/usr/share/fonts/X11/encodings/large/lots of .gz files
/usr/share/fonts/X11/util
/usr/X11R6/lib/X11/fonts/encodings/encoding.dir
/usr/X11R6/lib/X11/fonts/encodings/large/encoding.dir

---

### Post by jon4paz on 2007-10-12
I found I needed to change permissions on .Xauthority from rw. to rwx.
 
and now the authority file /home/_/.serverauth.nnnn is created

Now all I have is:

xinit: Server error.

---

