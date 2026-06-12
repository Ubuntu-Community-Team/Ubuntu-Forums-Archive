---
title: "Ubuntu 7.04 on VPC - Mouse issue"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Tinius on 2007-04-19
I was able to get it to work with the following trick as I did with 6.10


> Step 1: Boot Live CD, press F6 (Other Options)
Step 2: Go near the end of the line and remove the word splash, then press Enter.
Step 3: After Ubuntu 6.10 boots, Press Crtl-Alt-F1 to get to a command line interface.
Step 4: Type in the following command to reset defaultdepth from 24 to 16:

sudo sed -e 's/DefaultDepth.*24/DefaultDepth 16/g' -i /etc/X11/xorg.conf

Step 5: Press Ctrl-Alt-F7 to return to the Ubunto Desktop.
Step 6: Press Ctrl-Alt-Backspace to reload the Ubunto Desktop.
Step 7: Graphics should be adjusted, and now you can perform an installation under VPC


However it will not capture the mouse, I am currently doing an install on a virtual HD using the keyboard only, but I am wondering if anybody knows how to get it to capture the mouse.

Any ideas?

---

### Post by mwexler on 2007-04-19
I don't have a solution, but wanted to give a +1; I'm seeing the same thing here.  A live CD booted in Virtual PC 2007 does not allow me to "capture" the mouse in the screen.  In fact, I can't seem to even get the keyboard to work.  This same environment has a great 6.10 install, so something must be very different in how 7.04 talks to the mouse and keyboard. Note that I booted into "safe graphics mode" since Virtual PC cannot emulate a 24 bit screen.

---

### Post by Loki-uk on 2007-04-20
I have a similar issue I changed to 800 x 600 x16 using the f4 menu and then booted using safe graphies I can swicth between desktops but what keys do I use to get to the install prompt?

Thanks

---

### Post by Eagle117 on 2007-04-20
See this post I opened up yesterday: [http://ubuntuforums.org/showthread.php?t=413899](http://ubuntuforums.org/showthread.php?t=413899)

The mouse doesn't work even after the install but here is how you can get the install going if you choose "Graphics Safe Mode" when booting:
Try pressing ALT+F1 when you boot from the CD to switch virtual desktops and then the keyboard will work to select Install and you will be good to go from there... except for having no mouse after the install finishes.

---

### Post by Loki-uk on 2007-04-20
This would appear to be a Feisty issue in general and not a VPC issue. We'll need to be patient whilst they sort it out.

Brian

---

### Post by hinsdale on 2007-04-21
I agree that this is a 7.04 problem.  I had 6.10 working fine in VPC 2007 -- used the instruction in the forum to set the display bit depth to 16 and everything was fine.  I just upgraded the image to 7.04 this morning via Synaptic and have the same problem -- everything works fine (including the keyboard) *except* for the mouse.  I can't capture the mouse in the virtual window.  I can get to a text entry box using the Alt+F2 command, but don't know how to trouble-shoot the mouse problem from there.

---

### Post by Tinius on 2007-04-21
Anybody have any luck finding a solution for this?

---

### Post by mwexler on 2007-04-22
I've created a bug for Ubuntu at [https://bugs.launchpad.net/ubuntu/+bug/109027]("https://bugs.launchpad.net/ubuntu/+bug/109027"), perhaps the more technical folks here could add whatever info I left out.

---

### Post by ChodaBoy on 2007-05-04
What I find particularly frustrating is this problem was reported in JANUARY and has still not been resolved.

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=223606](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=223606)

This should have been caught (and corrected) long before Ubuntu 7.04 was released.  Yet another rock for Windowz to through at Linux.  :(

---

### Post by fjamison on 2007-05-05
I guess I'll have to try and find version 6.10 or 6.03.

I need linux because the university classroom labs use it...but I am new to linux.

Not a great experience for a newbie...

---

### Post by masterots on 2008-02-04
I just came across this blog post and it has the instructions for fixing your mouse -- it's not 100% permanant (you'll need to fix it whenever you update your kernel) but it seems to work well.

[http://blogs.msdn.com/mikekol/archive/2007/08/06/making-ubuntu-7-04-work-under-virtual-pc-2007.aspx](http://blogs.msdn.com/mikekol/archive/2007/08/06/making-ubuntu-7-04-work-under-virtual-pc-2007.aspx)

---

