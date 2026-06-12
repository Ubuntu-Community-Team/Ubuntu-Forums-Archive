---
title: "Stable installation gst-vaapi on Ubuntu x64"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by ArtProf on 2013-03-22
Hi guys!
My idea is to provide my own opengl texture for gstreamer to play vaapi-decoded video.

I have installed Linux 11.10 x64, have  compiled gstreamer and gstreamer-vaapi from this git://[gitorious.org/vaapi/gstreamer-vaapi.git]("http://gitorious.org/vaapi/gstreamer-vaapi.git").
There were some troubles with compilation, but I had solved they.

I want to be able to output video to my window, I've tried this but without any success
gst-launch-0.10  -v filesrc location=/path/to/file.mp4 ! qtdemux ! vaapidecode !  vaapidownload | y4menc ! filesink location=decoded-video.y4m

Does anybody know a working recipe of gstreamer-vaapi installation?

---

