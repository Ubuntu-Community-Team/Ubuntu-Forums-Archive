---
title: "Intel drivers Opengl 2.0 for cairo-dock?"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Taiebot65 on 2009-02-22
Hello All
I'm following cairo-dock-2 dev and i would like to know if the intels driver are going to be able to use opengl 2.0 in the future. For the moment i ve got those specifications

OpenGL version: 1.4 Mesa 7.3
OpenGL vendor: Tungsten Graphics, Inc
OpenGL renderer: Mesa DRI Intel(R) 945GM GEM 20090114 x86/MMX/SSE2

I would like to have the full support for opengl 2.0 but i think it ll not make it to jaunty...:(
There is a huge improvement from intrepid because with opengl effects activated x was crashing now i can see the dock and all the effects but the background is not translucent and always seems to be the desktop wallpaper

there is some .deb if you want to test

[http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=15624]("http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=15624")

[http://www.youtube.com/watch?v=yWwXaQMdhiQ&feature=channel_page]("http://www.youtube.com/watch?v=yWwXaQMdhiQ&feature=channel_page")

Shall i report it as a bug?

---

### Post by RAOF on 2009-02-22
Report what as a bug?  The lack of OpenGL 2.0 support?  Probably not; none of the free drivers support OpenGL 2.0 - you'll have to check for the extensions you're after regardless.

---

### Post by Taiebot65 on 2009-03-03
Ok so i found some information and it seems that my problems is related to rgba support i tried as well a small program made by macslow and i ve got exactly the same problems...

[http://bazaar.launchpad.net/~macslow/gtk-gl-rgba-1/trunk/files]("http://bazaar.launchpad.net/~macslow/gtk-gl-rgba-1/trunk/files")

---

### Post by Taiebot65 on 2009-03-03
I answer to myself.. Well this little program works fine when i put UXA option in my xorg so maybe a bug in cairo-dock

---

### Post by Taiebot65 on 2009-03-16
Great news for intel users... Cairo-dock opengl is usable for intel drivers.

First you have to enable UXA in your xorg and after launch cairo-dock in terminal  by using the option -i
the only problem actually is the autohide function see screenshot but you can easily solve this problem by keeping the dock behind windows in the configuration manager....
New version is available [http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=15624]("http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=15624") 

[IMG]http://farm4.static.flickr.com/3646/3359778248_d16cfc7f7b_t.jpg[/IMG]

[http://farm4.static.flickr.com/3646/3359778248_d950c518a2_o.png]("http://farm4.static.flickr.com/3646/3359778248_d950c518a2_o.png")

---

### Post by Taiebot65 on 2009-03-21
Wouuuuuhhhhh you can now use full cairo-dock opengl with UXA enable.... no need to -i anymore

Come and test this new dock.

[http://www.cairo-dock.org/bg_forumlist.php]("http://www.cairo-dock.org/bg_forumlist.php")

---

### Post by scaine on 2009-03-21
I really like Cairo Dock, but I have fallen in love with Docky recently.  If only Docky had a notification area, I'd lose all my gnome-panels and just use that.

With Cairo Dock, there is a notification area plug-in, but it wasn't actually all that great - I seem to remember that once you click on the icon to see your notification area, it then "stuck" and wouldn't vanish again once you were finished with it, which took up loads of room.

Cairo Dock's options are also a bit of a maze.

But it's a beautiful dock and very functional and flexible.  I'll have to check it out again later.

---

### Post by Taiebot65 on 2009-03-21
A plugin a la gnome do is planned maybe it will not be as good as gnome-do but if there is a lots of request :guitar:

---

### Post by biji on 2009-03-28
me too....  i tried alpha version of Gnome-do docky... awesome ... previously i;m using awn manager and cairo dock

---

### Post by forcecore on 2009-03-29
i started using cairo-dock too and it is really good for launching and futuristic visual effects too, i try to show this to other people too and i am sure they like it and want ubuntu then.

Cairo-dock is available in one .deb file (2 if plugins too) but why the heck Docky needs so much .deb dependencies.

i tested intel chip laptop but 2-dev do not run and only 1.6.3.1 runs fine.

---

