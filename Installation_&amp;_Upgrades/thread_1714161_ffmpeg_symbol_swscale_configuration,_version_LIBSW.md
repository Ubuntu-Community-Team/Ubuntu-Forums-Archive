---
title: "ffmpeg: symbol swscale_configuration, version LIBSWSCALE_0 not defined in file libsws"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by sushant.d84 on 2011-03-25
Hi All, 

I am currently facing this problem... 
Please read below.. 

root@user-desktop:~# /usr/local/bin/ffmpeg -f image2 -i /opt/lampp/htdocs/image_overlay/temp/images_overlayed%d.jpg -y -r 30 -f mp4 -sameq /opt/lampp/htdocs/image_overlay/overlay.mpg 2>&1
FFmpeg version 0.6.1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 24 2011 18:35:56 with gcc 4.4.3
  configuration: --enable-shared --enable-gpl --enable-libfaac --enable-nonfree --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-libvorbis --enable-libmp3lame
/usr/local/bin/ffmpeg: relocation error: /usr/local/bin/ffmpeg: symbol swscale_configuration, version LIBSWSCALE_0 not defined in file libswscale.so.0 with link time reference
root@user-desktop:~# 



Anybody have solution for this ?!

---

### Post by FakeOutdoorsman on 2011-03-25
> **sushant.d84 said:**
> Anybody have solution for this ?!

Yes. Uninstall your compiled FFmpeg and follow this guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

