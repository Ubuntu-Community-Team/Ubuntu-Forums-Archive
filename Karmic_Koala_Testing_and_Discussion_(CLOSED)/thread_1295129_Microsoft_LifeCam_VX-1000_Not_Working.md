---
title: "Microsoft LifeCam VX-1000 Not Working"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2009-10-19
In the past I've had very good luck with Ubuntu recognizing my hardware so that it all "just works" out of the box.

I recently got a new Microsoft LifeCam VX-1000 web cam that seems to be detected by Skype..

[IMG]http://img38.imageshack.us/img38/8933/screenshotoptions.png[/IMG]

...but when I click test to view the video, it's all static and corrupt.

[IMG]http://img38.imageshack.us/img38/9964/screenshotoptions1.png[/IMG]

Is there a simple package that I can install to get this working? It looks like some people got it working in Ubuntu 8.10, but I don't want to install anything unnecessary for 9.10 just because I don't know what I'm doing. ;)

Thanks in advanced!

EDIT:
The camera is supposed to be supported as it's listed [here]("https://wiki.ubuntu.com/SkypeWebCams"), but the work around that they are listing isn't working for me.

I tried launching with the following command from a 64-bit machine:
```
env LD_PRELOAD=/usr/lib32/libv4l/v4l2compat.so skype
```

I found that I was already using V4L 2 from 
```
sudo gstreamer-properties
```

The test video in Skype never really changes from the mess it was showing above.

---

### Post by kyleabaker on 2009-10-27
Anyone?

---

