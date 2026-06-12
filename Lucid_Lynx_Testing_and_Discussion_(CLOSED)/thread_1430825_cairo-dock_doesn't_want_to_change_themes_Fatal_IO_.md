---
title: "cairo-dock doesn't want to change themes Fatal IO error 11"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ankspo71 on 2010-03-15
Hello,
I installed cairo-dock today and I was able to change a theme only once. I went to try other themes but it crashes without changing the themes. 
I tried changing nvidia drivers from 195 to 173, 
I tried reinstalling cairo-dock, 
I tried reinstalling after purging cairo-dock, 
I tried deleting the configuration directory /home/james/.config/cairo-dock .
I tried running cairo-dock with and without opengl.
I tried to download cairo-dock themes from gnome-look too, but cairo-dock will not install them using the theme changer.
```
james@James:~$ cairo-dock -o
/usr/share/themes/airlines/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/airlines/gtk-2.0/gtkrc:91: Murrine configuration option "gradients" is no longer supported and will be ignored.

 ============================================================================ 
    Cairo-Dock version: 2.1.3-6
    Compiled date:  Mar 10 2010 17:33:45
    Running with OpenGL: 1
 ============================================================================

OpenGL config summary :
 - bNonPowerOfTwoAvailable : 1
 - bPBufferAvailable : 1
 - direct rendering : 1
 - bTextureFromPixmapAvailable : 1
 - GLX version : 1.4
 - OpenGL version: 3.2.0 NVIDIA 195.36.08
 - OpenGL vendor: NVIDIA Corporation
 - OpenGL renderer: GeForce 8400 GS/PCI/SSE2

warning :  (cairo-dock-config.c:cairo_dock_get_string_key_value:227)  
  Key file does not have key 'no input image'
activating pbuffer, usually buggy drivers will crash here ... ok, they are fine enough.
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:184)  
  Key file does not have key 'scroll speed'
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:184)  
  Key file does not have key 'scroll accel'
cairo_dock_replace_values_in_conf_file (/home/james/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
warning :  (cairo-dock-keyfile-utilities.c:cairo_dock_open_key_file:34)  
  No such file or directory
clock : default needle size
5 -> 5;-1
cairo_dock_replace_values_in_conf_file (/home/james/.config/cairo-dock/current_theme/cairo-dock.conf)
not really outside (0;0)
iNbConfigDialogs <- 1
cairo_dock_set_status_message (Listing themes in '(null)' ...)
cairo_dock_set_status_message ()
2/1/2
cairo_dock_set_status_message ()
preview : 361x200
on force a quitter (iRefCount:0)
not really outside (1027;141)
cairo_dock_set_status_message (Importing theme Elementary_Dragonfly[2] ...)
glXMakeCurrent() failed
cairo-dock: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
james@James:~$ 
```Before trying cairo-dock, I was using cairo-clock but it quit working due to a segfault error. I wonder if they share something wrong (because of the same name cairo). I'm working on bug reports to submit shortly, but I was wondering if anyone had an idea on what the problem could be before I do. I see that fabounet visits here often so I'm hoping fabounet sees this.

I am able to install a new theme by manually replacing the theme in the "current_theme" folder though.
thanks.
(Lucid alpha3 fully updated)

Edit: I am able to change clock themes in cairo-dock, but not dock themes.

---

### Post by ankspo71 on 2010-03-15
Hello,
I kept at it all night and I fixed cairo-dock but I'm not sure how it broke in the first place. It ended up being a bad configuration file (reported to me by the terminal this time), and seems to be working fine now after removing the configuration folder (again). I'll keep an eye on this. ;)

Now to see if I can work out that cairo-clock problem.
Thanks.

---

### Post by lindsay7 on 2010-03-16
Go to home/username/.config/cairo_dock/themes and add the themes that you download.  

Two things to note, 1. .config is a hidden folder and 2. Most of the themes need to be extracted then you just copy and past to the themes folder  as shown above.  I just use nautalus to do this. Right click on your home folder and choose preferences/view and check off "show hidden".

---

### Post by fabounet on 2010-03-16
> Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Not sure, but this error seems quite a low-level one, maybe being under Lucid doesn't help to have a stable system. ^^
just to know, which theme did you have when you got this error ?

by the way the dock has its own clock applet, that can be placed on the desktop, so you don't need to load another program like Cairo-Clock ;-)

---

### Post by ankspo71 on 2010-03-16
Hi Fabounet,

The first theme I installed was Humanity-Dock. I think I narrowed down the problem to the unusually slow loading of the gnome desktop in Lucid. I'm using a startup script to launch cairo-dock now and now I don't see the "Manage Themes" window pop up instead of the dock when I turn on the computer anymore. So now everything is even better.
```
#!/bin/bash 
sleep 30 && cairo-dock -o ;
```Oh yes, I know I don't need cairo-clock with cairo-dock. At first I only installed cairo-clock because I saw people uploading some nice clock themes at gnome-look.org. (I seemed to have forgotten that the those clock themes can also be used in cairo-dock).

Also, I think the segfault error in cairo-clock was also related to the slow loading of the gnome desktop, because a start up script fixed that segfault problem, and the occasional render problem as well. I don't have cairo-clock installed anymore now that I am using the clock in cairo-dock.

Thanks for taking the time to look into this problem.

---

### Post by ankspo71 on 2010-03-16
To Fabounet:
I found the bug. ;) (I think)

I always like to create a shortcut to my home folder in my dock by doing the following:


[LIST=1]
[*]Right click on Cairo-dock.
[*]Add > "add a custom launcher"
[*]Launcher name: Nautilus
[*]Command to run on click: nautilus /home
[*](it happens with or without the icon value)
[*]click apply
[/LIST]
Then when I try to change the theme it doesn't work and either hangs cairo-dock or crashes cairo-dock. (as seen in the original post).

If I don't create a custom launcher for my home folder, then I can change themes any time without problems.

I recreated this problem about 5 or 6 times today to make sure this is the actual problem.

Can anyone else confirm this?
thanks.

Edit: I still feel the startup script has helped me too, because of the very slow loading of the gnome desktop in Lucid (on my computer)

---

