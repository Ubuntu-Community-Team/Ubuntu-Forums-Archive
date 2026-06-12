---
title: "Mouse Jerk"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Arador Aristata on 2008-06-06
Hello again

So I've got Hardy installed and I will do the rest like my dial up bluetooth networking later.

I do have one issue and I could not find a thread about it. The mouse movement is very jerky and slow. Like Windows would do if it was working hard in the background. Now here is the strange part. While the OS is loading and while it is working, loading a program,  the mouse moves fine. Once it stops loading and the hard drive goes silent, the mouse jerks again. Very weird.

It's an old A4Tech 5 button mouse. about 8 years old. Optical. Dual Wheel 4D++

The buttons and wheels work fine. Just the motion and click response.

---

### Post by hal8000 on 2008-06-06
Have you tried:
system/preferences/mouse
and adjusting pointer speed?

---

### Post by Arador Aristata on 2008-06-07
Yes. Tried various settings and it still keeps jerking. :(

---

### Post by dstew on 2008-06-07
You might try reconfiguring your xorg.conf file to see if you can get better settings. To do that, on a command line enter```
sudo dpkg-reconfigure xserver-xorg
```Pay particular attention to the mouse pointer section. Maybe you can pick your exact model, or at least try different settings.

If you are not able to make progress that way, you can try directly editing the xorg.conf file. [Here is a thread]("https://answers.launchpad.net/ubuntu/+question/9761") that gives an example. Although the tread is old, and the problem different (buttons not working) maybe you can use a different protocol and get better behavior.

p.s. Here is [another thread]("http://www.backports.ubuntuforums.org/showthread.php?t=2880")...

---

