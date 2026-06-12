---
title: "ffmpeg installation on Ubuntu 8.04"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by jsia18 on 2008-06-21
Hi I tried to install ffmpeg from synaptic manager it works but it does not set --enable liblame so there is no sound after I encode the video.  How do I do this from installing by source.  I've already installed ffmpeg previously in ubuntu 7 and it works fine however upon upgrading to ubuntu 8.04 it produced an error in libavcode.so can't expalin why. Could someone help me so that I can install ffmpeg properly?  Thanks

---

### Post by startherepodcast on 2008-06-21
Maybe this could help you:

[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

It tells you how to make it compile with all the stuff that could be illegal in you country.

So please check with your local authorities first :)

---

### Post by jsia18 on 2008-06-21
Thanks, I tried it but I got errors when performing make install

---

### Post by Pumalite on 2008-06-21
Make Medibuntu your repository and install all the codecs:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)
Run also:
sudo aptitude install ubuntu-restricted-extras

---

### Post by FakeOutdoorsman on 2008-06-22
If you don't want to use a third-party repository such as Medibuntu, then you can compile it yourself:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

---

