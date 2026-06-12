---
title: "How do I install Ubuntu in Virtual Server 2005 R2?"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by webJose on 2006-11-20
Hello everyone.  As the caption clearly states, I am currently unable to install Ubuntu in Virtual Server 2005 R2.

I have tried to install both Ubuntu 6.06 Server and Desktop to no avail.  The problem?  Well, each OS has a different one:  The Server version seems to work, but the selection screens span more than what the Virtual Server 2005 R2 remote control window allow, so I really don't know what I'm doing.  Is there a way to control the display during installation so I can see everything on screen?

The desktop installation goes really bad.  It starts up fine, and I select to Install.  After that, the Ubunto logo appears, and then the remote control window enlarges quite a bit but everything is dark and unreadable.

Please take into account that I'm a Microsoft guy.  I don't know the first thing about Unix, but since Ubuntu is promoted as an easy-to-use OS, I thought it could be my introduction to Unix.

Anyway, your help is very much appreciated.  Thank you!

---

### Post by kacheng on 2007-01-31
This has to do with a fault in Virtual Server 2005 R2 that advertises a 24-bit video depth adapter, but only emulates a 16-bit one.


If you choose (on the boot up window) the F4 option, you can change the video mode used for the install.

I chose a video depth of 16 bit (I used 800x600x16) it worked nicely.

---

### Post by jacobrich on 2007-02-05
I can't seem to get it to work with Virtual Server 2005 R2 using the method above. I have tried all of the display settings to no avail. I am having the same error as the original poster. Is there anything else I can try to get Ubuntu to install on my Virtual Server?

---

### Post by kacheng on 2007-02-05
You can try installing using the Server version and adding in ubuntu-desktop at a later stage - this should at least allow you to get the installation done.

---

