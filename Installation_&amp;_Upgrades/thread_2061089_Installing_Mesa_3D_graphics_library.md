---
title: "Installing Mesa 3D graphics library?"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by Byron Blue on 2012-09-21
Howdy
I'm new to Ubuntu (2nd day today), have managed to get through many issues: GCC is installed and running, I have Code::Block installed and running. I'm quite happy so far with the experience. Except for:
How do I install the Mesa 3D graphics library? I've downloaded the package and tried to make sense of it (I write software for a living) but could not either make sense of it or find legible information on the web to help me out.
Isn't there simply a sudo type command that I can use in the terminal to install and set it up for compiling code?
Sorry to be so new but any help would be appreciated...
Byron

---

### Post by josephmills on 2012-09-21
1st) Welcome to the Ubuntu Community! We need more devs :) 

libmesa Open{gl,gles} libs are all over the place, But One can install Or look for packages using some nifty commands 

like 
```
apt-cache search <name of something that you want to find>
```

example  
```

apt-cache search opengles
kde-window-manager-common - K window manager (KWin) Common Files
libkwinactiveglesutils1 - library used by accellaration for the KDE window manager Active
libkwinglesutils1 - library used by accellaration for the KDE window manager
[COLOR="red"]mesa-utils-extra[/COLOR] - Miscellaneous Mesa utilies (opengles, egl)
```


and there is one 

```
 apt-cache search libmesa
libglu1-mesa-dev - Mesa OpenGL utility library -- development files
```

But you can also install synaptic package manager and look for libgles{1,2} stuff using the search functions.
see pictures attached  



hope that this helps :)

EDIT 

but What I think you are looking for is 
```
 sudo apt-get install libgles2-mesa libgles2-mesa-[dbg,dev]
```

---

### Post by Byron Blue on 2012-09-21
I really appreciate the help!
I've installed Synaptics, searched for Mesa 3D and installed (most) of the packages found.
Thank you once again!

---

### Post by josephmills on 2012-09-21
NP and again welcome to Ubuntu Forums and do you think that you could 

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)



Thanks

---

### Post by Byron Blue on 2012-09-23
I've managed to guess and gosh my way through (I think) most of the installation but have hit a snag:
./configure ran fine. When I went to make install I get the following error(s) beginning with this one:
*nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_pushbuf_flush'*
There are lots (about 10-15) similar errors following this one. Obviously, I've missed something here and cannot locate a solution to this on the 'net.
Any solutions/suggestions?
Thanks for all your help this far. I really am quite new to Linux - the operating system I write is currently based in DOS: I'm attempting to re-code it in Linux to take advantage of the speed, graphics and drivers - much of which DOS simply cannot handle.
Being new to Linux I really would like to help others along but am simply a "newbie" at this point. Give me a bit of time. Thanks...

---

### Post by Albertmekki on 2013-04-29
hello, 
I get the code source of Mesalib 7.11 and i configure this code 

export NOUVEAU_CFLAGS="-I/usr/include/drm/"
export NOUVEAU_LIBS="-L/usr/local/lib/"

./confgure 

when i run make i get this errors :

nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_pushbuf_flush'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_bo_pending'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_pushbuf_marker_undo'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_grobj_autobind'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_pushbuf_marker_emit'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_bo_unmap'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_channel_free'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_grobj_free'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_device_open_existing'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_pushbuf_emit_reloc'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_device_close'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_channel_alloc'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_bo_handle_get'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_bo_map'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_bo_new'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_bo_ref'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_bo_handle_ref'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_notifier_alloc'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_bo_new_tile'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_grobj_alloc'
nouveau_vieux_dri.so.tmp: undefined reference to `nouveau_notifier_free'
collect2: ld returned 1 exit status
make[6]: *** [nouveau_vieux_dri.so] Error 1
make[6]: Leaving directory `/home/administrateur/Bureau/Mesa-7.11/src/mesa/drivers/dri/nouveau'

---

