---
title: "How do I run Gnome Shell? (Karmic repos)"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by aamukahvi on 2009-09-08
Hi,

This thread is about getting the karmic packaged (now up to 2.27.2) gnome-shell to work, not compiling. (I tried searching the other threads and also looked at the Gnome wiki page).

Just thought I'd try and ask for some help. I've been trying to run gnome-shell on my Karmic test VM (virtualbox).
I have enabled 3D support and installed the guest additions. Compiz works very well.

Gnome Shell, on the other hand, won't start. It just gives me this error:```
@karmic:~$ gnome-shell --replace
      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
Window manager warning: Log level 16: Failed to load shared library 'clutter-glx-1.0' referenced by the typelib: libclutter-glx-1.0.so: cannot open shared object file: No such file or directory
    JS ERROR: !!!   Exception was: Error: Error invoking Clutter.from_pixel: Could not locate clutter_color_from_pixel: libclutter-glx-1.0.so: cannot open shared object file: No such file or directory
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Error invoking Clutter.from_pixel: Could not locate clutter_color_from_pixel: libclutter-glx-1.0.so: cannot open shared object file: No such file or directory")@:0
("Error invoking Clutter.from_pixel: Could not locate clutter_color_from_pixel: libclutter-glx-1.0.so: cannot open shared object file: No such file or directory")@gjs_throw:0
@:0
@/usr/share/gnome-shell/js/ui/button.js:12
'
    JS ERROR: !!!     message = 'Error invoking Clutter.from_pixel: Could not locate clutter_color_from_pixel: libclutter-glx-1.0.so: cannot open shared object file: No such file or directory'
    JS ERROR: !!!   Exception was: Error: Error invoking Clutter.from_pixel: Could not locate clutter_color_from_pixel: libclutter-glx-1.0.so: cannot open shared object file: No such file or directory
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Error invoking Clutter.from_pixel: Could not locate clutter_color_from_pixel: libclutter-glx-1.0.so: cannot open shared object file: No such file or directory")@:0
("Error invoking Clutter.from_pixel: Could not locate clutter_color_from_pixel: libclutter-glx-1.0.so: cannot open shared object file: No such file or directory")
```

Is there some library still that I need to install or should it just work?
Sometimes I also get something about the display 0:0 already being in use. I've tried both xephyr and --replace.

So, any suggestions? :)

---

### Post by aamukahvi on 2009-09-08
Ok, did a little bit more digging:```
sudo ln -s /usr/lib/libclutter-glx-1.0.so.0 /usr/lib/libclutter-glx-1.0.so
```

Solved. :P

Getting some weird drawing and artifacts but otherwise looks nice. Edit: not so nice, very bad artifacts and finally lockup :)

---

### Post by mariner09 on 2009-09-08
So, gnome-shell not yet ready for Karmic consumption???

---

### Post by 23meg on 2009-09-08
> **mariner09 said:**
> So, gnome-shell not yet ready for Karmic consumption???

No, it wasn't meant to be ready either; it was packaged for preliminary testing.

---

### Post by NCLI on 2009-09-08
What, you mean ready for production use? No, definitely not, maybe in Karmic+1.

---

### Post by graaant on 2009-09-08
If I'm correct, the packaged version is pretty out-of-date.
The best way to test would be to build using the instructions on live.gnome.

Correct me if I'm wrong.

---

### Post by 23meg on 2009-09-08
> **graaant said:**
> If I'm correct, the packaged version is pretty out-of-date.
The best way to test would be to build using the instructions on live.gnome.

Correct me if I'm wrong.

Where do you get that information? 2.27.2 was released four days ago and we've had it in Karmic since yesterday.

---

### Post by Eclipse. on 2009-09-08
> **NCLI said:**
> What, you mean ready for production use? No, definitely not, maybe in Karmic+1.

More like 11.04 instead of karmic+1.Gnome shell is a while off before its going to ship by default onto peoples machines.

---

### Post by Starks on 2009-09-09
> **aamukahvi said:**
> Ok, did a little bit more digging:```
sudo ln -s /usr/lib/libclutter-glx-1.0.so.0 /usr/lib/libclutter-glx-1.0.so
```Solved. :P

Getting some weird drawing and artifacts but otherwise looks nice. Edit: not so nice, very bad artifacts and finally lockup :)
Can you file a bug against the gnome-shell package with that info, please?

---

### Post by cmccauley on 2009-09-09
Wow, that works great.

Needed to do 


sudo gnome-shell --replace


after linking to the correct lib but really cool and very fast.

Anyone know if this packaged version is particularly out of date?

---

### Post by 23meg on 2009-09-09
> **cmccauley said:**
> 
Anyone know if this packaged version is particularly out of date?

Read [post #7]("http://ubuntuforums.org/showpost.php?p=7918667&postcount=7"). You can also always check that by [looking at the changelog]("http://ubuntuforums.org/showpost.php?p=7896280&postcount=514").

---

### Post by cmccauley on 2009-09-09
I didn't know about the aptitude changelog - thanks. Looks like this is a pretty recent snapshot then.

---

