---
title: "tx2 karmic and suspend"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekknokrat on 2009-10-09
I have a touchsmart tx2. So far most of the hardware issues are solved with it. Now I gave karmic beta a try via upgrade-manager and I must admit its very promising.

One issue I now have is suspend which worked fine in jaunty. Now in karmic having suspend state via g-p-m (lid / suspend button in menu) works. But on resume it suspends a second time. 
Only after second resuming everything is working. I am wondering what causes this second suspend. A suspend via sudo pm-suspend resumes correctly on the first sight. Not found any existing bugs in launchpad. Any hints?

---

### Post by tekknokrat on 2009-10-10
This issue is discussed in more detail in this bug report:

 [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/425411](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/425411)

---

### Post by Favux on 2009-10-10
Hi tekknokrat,

I don't know if this site will help you with the bug or not.  But maybe worth a look?  The HAL quirk site:  [http://hal.freedesktop.org/quirk/](http://hal.freedesktop.org/quirk/)

---

### Post by tekknokrat on 2009-10-13
Hi Favux,

thanks for the link. I was trying to downgrade g-p-m to jaunty's version and then recognised that it depends on devicekit-power which is imo replacement for hal. Perhaps you know some info you can point me about the hal - devicekit transition state in ubuntu?

Cheers,
tekknokrat

---

### Post by Favux on 2009-10-13
Hi tekknokrat,

Here's where David Zeuthen (Red Hat dev.) announces DeviceKit replacing HAL:  [http://lists.freedesktop.org/archives/hal/2008-May/011560.html](http://lists.freedesktop.org/archives/hal/2008-May/011560.html)

Here's where he says DeviceKit is going into udev extras:  [http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html](http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html)

Here's the DeviceKit site with some documentation links:  [https://fedoraproject.org/wiki/Features/DeviceKit](https://fedoraproject.org/wiki/Features/DeviceKit)

I haven't followed the Ubuntu dev.s discussion of implementing Device Kit in Karmic.  I could probably locate some stuff if you need it.

---

### Post by tekknokrat on 2009-10-14
Hey Favux, thanks for your input.
It's nice that at least Fedora has a lot of pages concerning that topic.

At this link

[https://fedoraproject.org/wiki/Features/DeviceKit](https://fedoraproject.org/wiki/Features/DeviceKit)

developers list some tests that should be done:

... 
8. Check that gnome-power-manager provides the same functionality it had in previous releases

How can I provide developer with more deep insight of what gnome-pwoer-manager does on my laptop when lids closed/opened. I don't see any commandline parameter for g-p-m regarding verbosity and/or debugging.

---

### Post by Favux on 2009-10-14
Hi tekknokrat,

lol!  You'd expect Fedora to have stuff, it's their project.

Sorry I don't know.  I know how to up the verbosity on HAL.  I don't know if that works for DeviceKit.

Would Apport pick up what's needed?  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)  Linked here:  [http://ubuntuforums.org/showthread.php?t=1280021](http://ubuntuforums.org/showthread.php?t=1280021)  and here:  [http://ubuntuforums.org/showthread.php?t=1161570](http://ubuntuforums.org/showthread.php?t=1161570)

Maybe this might be of some help?:  [http://ubuntuforums.org/showthread.php?t=1076486](http://ubuntuforums.org/showthread.php?t=1076486)

---

### Post by tekknokrat on 2009-10-15
> **Favux said:**
> Hi tekknokrat,
lol!  You'd expect Fedora to have stuff, it's their project.


Sorry my ignorance, was not aware that this was born in Redhat Labs. What annoys me is that Ubuntu only mentions little notice in their [release notes]("http://www.ubuntu.com/testing/karmic/alpha4#hal%20deprecation") and still no update of the bug in #2 post :(

> Maybe this might be of some help?:  [http://ubuntuforums.org/showthread.php?t=1076486](http://ubuntuforums.org/showthread.php?t=1076486)

Looks good, will have a look what acpi_listen spits out.

---

### Post by Favux on 2009-10-15
Hi tekknokrat,

There's been activity on the bug!  They may have it or be close.  And they answered one of your questions:

> killall gnome-power-manager
gnome-power-manager --verbose 2>&1 | tee ~/gpm.log

then reproduce the problem, press Control-C, and attach ~/gpm.log here.

Then press Alt+F2, run "gnome-power-manager" to get it back in normal shape.
It looks like progress anyway.

---

### Post by tekknokrat on 2009-10-16
Thanks Favux for notify, it seems I fall from subscription for some reason.
The issue unfortunately still exists. First time opening the lid is discovered as lid-down event. I attached my log to the bug.

---

