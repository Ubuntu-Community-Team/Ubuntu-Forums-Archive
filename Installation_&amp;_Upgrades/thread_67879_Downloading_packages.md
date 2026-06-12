---
title: "Downloading packages"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by markr on 2005-09-21
Hi,

My laptop does not have internet access at the moment, but I need to download a number of packages to get multimedia working properly (ie. play avi, mp3, dvd etc).  

Can I access the packages via my web browser so I can copy them across to my laptop and install via dpkg?

If this is possible, can someone provide a URL where I can get the w32codec, libdvd* and gstreamer stuff (for Amarok mp3 playing)?

Thanks

MArk.

---

### Post by devkelso on 2005-09-21
You can indeed grab the packages from a source and install them with "dpkg -i <path/to/package.deb>"  The packages will have a .deb extension.  Perusing a debian or ubuntu repository (such as "http://archive.ubuntu.com/ubuntu") will have some directory entries.  the "pool" directory will contain all the packages in the subdirectories.  lib prefix denotes libraries but not all libraries are in them.

I cannot help you with the multimedia packages.

---

### Post by John.Michael.Kane on 2005-09-21
Use the ubuntu add on cd [http://ubuntuforums.org/showthread.php?t=30147](http://ubuntuforums.org/showthread.php?t=30147) Should get you going..

---

### Post by bsussman on 2005-09-21
You may have some dependency issues when you install since you are downloading without the download process knowing what is installed/missing from your laptop. This is not deadly - just means you may need to iterate the process, getting more packages from the net.

I do not know of a way to make this easier, except laptop internet access.

---

### Post by markr on 2005-09-22
Okay, looked at the links to the add-on CD,  this is such a good idea, the hassle I used to go through using Fedora; I think the Ubuntu (I'm fairly new to this) community is shaping up to be a big player.

I noticed the Link above is for 5.04,  is an add-on CD available for 5.10 yet (I know it's a preview release)?

Thanks

Mark.

---

