---
title: "ffmpeg 2.0 installation in Ubuntu"
date: 2013-07-20
forum: Installation &amp; Upgrades
---

### Post by ras123 on 2013-07-20
Hi,

I compiled ffmpeg 2.0 as per the guide in Ubuntu 13.04

[http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

Now the binaries are installed in ~/bin and other related files are in ~/ffmpeg_build/{include, lib, share}

How can I move these into the default installation locations such as /usr/local without conflicting (if any) with the avconv installed from Ubuntu repository?

Thanking You,
Ras

---

### Post by FakeOutdoorsman on 2013-07-20
If you just want the binary you can simply use checkinstall:
```
sudo checkinstall --pkgname=ffmpeg2 --pkgversion="2.0" --default --backup=no install -Dm755 ~/bin/ffmpeg /usr/local/bin/ffmpeg
hash -r

```
This will add a ffmpeg2 package to your package management system. It may still cause issues for packages that directly use the ffmpeg binary supplied by the so-called "ffmpeg" package.

Another method is to move the files wherever you want and add the directory to your path: [How to add a directory to my path?](http://askubuntu.com/a/60221/59378)

Note that the guide you linked to will install the most recent ffmpeg code, and not necessarily a particular release. This is just fine for normal users since the releases are generally used by distros.

---

