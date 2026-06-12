---
title: "Installing gstreamer0.10-ffmpeg on ubuntu"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by pirpi on 2014-08-22
I am using gstreamer libraries for streaming. I need ffdec_h264 decoder, for this I want to install gtreamer0.10-ffmpeg on ubuntu 14.04. When I enter apt-get install gstreamer0.10-ffmpeg it will say package 'gstreamer0.10-ffmpeg' has no installation candidate. 

Please help me with this....

Thanks
pirpi

---

### Post by kostkon on 2014-08-22
Actually ubuntu has libav and not ffmpeg so you will have to install gstreamer1.0-libav instead.

As you can see it's only for gstreamer 1.x so you'll have to adapt your code / script or find another application, depending on your use case.

---

