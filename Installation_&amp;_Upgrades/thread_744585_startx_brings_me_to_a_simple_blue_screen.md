---
title: "startx brings me to a simple blue screen"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by Rizla on 2008-04-03
I finally got the nvidia drivers installed for my integrated nvidia geforce 7150 and was able to type "startx" without getting errors.


Now that i'm in "x" I dont really see much.  Its a nice looking blue background, with a bar along the bottom with the time.  How do i pull up a terminal?  do i just close x with ctrl+alt+backspace?

Also, this is a server that i installed x on, i tried playing a video file with mplayer and it was giving me a video out error..  Any help?

---

### Post by dstew on 2008-04-04
Did you reconfigure your xserver after you installed the drivers? You need to do that. From a command line enter```
sudo dpkg-reconfigure xserver-xorg
```When you get to the video display part, choose the name of the driver you installed (probably fglrx), and pick for the highest resolution the resolution that you actually use. When you are done reconfiguring, press ctrl-alt-backspace to restart the xserver and see if it works.

---

### Post by Rizla on 2008-04-04
I caved in an put xubuntu on the server..

---

