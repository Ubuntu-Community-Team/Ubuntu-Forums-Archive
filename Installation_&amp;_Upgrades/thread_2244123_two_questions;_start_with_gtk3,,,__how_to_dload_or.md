---
title: "two questions; start with gtk3,,,  how to d/load or build src"
date: 2014-09-13
forum: Installation &amp; Upgrades
---

### Post by kline on 2014-09-13
here is the Short of it:  Last night, my volunteer system admin said that the only thing he did while trying to fix something  that's constantly broken was to "remove several copies of my ubuntu 14.04 kernel.  i took most of yesterday as a day-off: shoulder troubles.  when i got back to work on one of my many gtk-3 files, i got the err-output:

pts/97 16:36 <tao> [5176] make                         ~/devel/gtk/cpFiles2Label
Package gtk+-3.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-3.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-3.0' found
cc -g -Wall  -DGSEAL_ENABLE=1 -DG_DISABLE_DEPRECATED=1 -DGDK_DISABLE_DEPRECATED=1 -DGDK_PIXBUF_DISABLE_DEPRECATED=1 -DGTK_DISABLE_DEPRECATED=1   -c -o arrow.o arrow.c
arrow.c:2:21: fatal error: gtk/gtk.h: No such file or directory
 #include <gtk/gtk.h>
                    

compilation terminated.

late yesterday, this build as before: a few std warning and an exit 0;  it is  all in C which i have been using since the early 1980.  this morning, rested, i got the following.   ---i did a locate gtk.h and got only:

/usr/include/gtk-2.0/gtk/gtk.h
/usr/share/gimp/2.0/help/en/file-print-gtk.html


i found a REcent gtk-3 and downloaded it.  the configuration to create Makefile died;  so is there a *safe* gtk+3 for ubuntu 14.04 and if so, where can i get it, and install it?  i am tempted to reboot, but if my sysadmin really did remove my kernel, i would never get up.  --that is my second question; first, i want to save my "cpfiles" so that it builds with gtk+3.

Anybody??

---

### Post by grahammechanical on 2014-09-13
Do you have Synaptic Package Manager installed? You can use that to find which kernels you have left and install other previous kernels if you wish. Or run

```
sudo update-grub
```

the screen printout should should what kernels are still there. 

Regards.

---

### Post by steeldriver on 2014-09-13
I don't see how that would be related to kernel files - the gtk+-3.0.pc file should be provided by package **libgtk-3-dev **

---

### Post by kline on 2014-09-14
libgtk-3-dev  was it.with several/many hours of work this saturday, my sysadmin {and possibly myself} resolved the fault.  right now, hours later, what put out an error, now builds.  and yes, it present the same noon-deadly errors as before.  *so* in the next two or three days, i'll drop in a few lines. if nothing breaks, i will be nearly done.

when i'm this close, it makes all the more sense to alias rm to /bin/rm -r $* ... !

this may be over-caution, but when i do a

   #  shutdown -r now<cr>

i want my desktop box to actually reboot.  is there a way of making sure than my kernel file[s] are actuall there?  i think my buddy upgraded my old 13.10 to 14.04 in may or june.    (in the years  that my server ran freebsd i built everything from src; ubuntu is faster and simpler.  if i need to get the necessarily files for 14.04 LTS, what do i need? and where are these files?)

---

