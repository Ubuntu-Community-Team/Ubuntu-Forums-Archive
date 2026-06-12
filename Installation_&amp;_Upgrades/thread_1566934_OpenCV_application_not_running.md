---
title: "OpenCV application not running"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by pravin_tavagad on 2010-09-03
unable to run opencv opllications on ubuntu(10.04)


error:OpenCV Error: Unspecified error (The function is not implemented. Rebuild the library with Windows, GTK+ 2.x or Carbon support. If you are on Ubuntu or Debian, install libgtk2.0-dev and pkg-config, then re-run cmake or configure script) in cvNamedWindow, file /home/p/OpenCV-2.0.0/src/highgui/window.cpp, line 100
terminate called after throwing an instance of 'cv::Exception'
Aborted

please help...!!

---

### Post by davidmohammed on 2010-09-03
what is the application?  Where did you download from?  How did you install it?

---

### Post by 130s on 2011-07-18
Although information provided is not enough, I assume the issue might be the same with the one that I had, judging only from the error msg.

I was able to workaround the error by removing OpenCV installed and re-install it again, following this link: [http://ubuntuforums.org/showthread.php?t=607871](http://ubuntuforums.org/showthread.php?t=607871)

---

