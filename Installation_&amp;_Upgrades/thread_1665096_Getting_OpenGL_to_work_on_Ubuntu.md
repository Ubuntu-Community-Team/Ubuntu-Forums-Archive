---
title: "Getting OpenGL to work on Ubuntu"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by Keand64 on 2011-01-11
EDIT: I got it to work.  It turns out that mesa-common-dev works with my nVidia drivers.

I'm new here, and to Linux/Ubuntu in general, so I apologize if this is in the wrong section or something.

Anyways, I'm trying to get the OpenGL SDK to work on my computer.  I've already gotten gcc/++ and whatnot, and I'm fairly sure I've upgraded my graphics drivers to the most current possible.

A quick check reveals that my graphics card is nVidia:
```
01:00.0 VGA compatible controller: nVidia Corporation NV41.8 [GeForce Go 6800] (rev a2)
```So I assume that I need to get the nVidia OpenGL packages:
```
sudo apt-get install nvidia-glx-dev
```However, that nets me this error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'nvidia-glx-dev' has no installation candidate
```Does anyone have any suggestions as to how to fix this? My only other thought is to apt-get mesa-common-dev, but I don't know if that will work with nVidia.   (And this is a rather old computer, so the problem might just be one of obsoleteness, but it doesn't seem like so, from the error I'm getting).

Thanks in advanced.

---

### Post by mikewhatever on 2011-01-11
Where did you get the nvidia-glx-dev? Run **apt-cache search nvidia-glx*** to see the packages with that name pattern.

Edit: What you probably want is nvidia-current-dev.

---

### Post by Keand64 on 2011-01-12
I checked out nvidia-current-dev, but it looks like that installs the headers to include/**nvidia-current**/GL, which, while not unworkable, is something I would like to avoid dealing with if there is an alternative solution.  It also lacks the glu.h header file, another problem I'd have to deal with.  I'll keep this in mind if I can't find a better solution, but until then..

apt-cache search reveals a number of files, most of the type nvidia-glx-#, nvidia-glx-#-dev, or nvidia-#-kernel-source.  Are any of these usable?  And is it completely unworkable to use the Mesa package on an nVidia card, or just undesirable?

Thanks again for the help.

---

### Post by efflandt on 2011-01-13
I don't really know what you are trying to do, but if you are looking for something for the default nouveau driver, instead of nvidia drivers, you might take a look at libgl1-mesa-dri-experimental.  Although, that would tend to be much slower than nvidia drivers.

---

### Post by Keand64 on 2011-01-13
> **efflandt said:**
> I don't really know what you are trying to do...
I'm trying to get the OpenGL headers gl.h, glu.h, and glut.h, and whatever other dependencies I need to program with OpenGL, if that clears things up.

---

