---
title: "Removal of IgnoreABI"
date: 2009-01-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gspat on 2009-01-23
When will this be a possibility? 

I thought I might be able to do it now, but the latest round of updates didn't do it.

I had to boot into the 28.4 kernal to change it back, seems to not want to update the screen once you hit the bottom.

---

### Post by Timon&amp;Pumba on 2009-01-24
Why boot to another kernel to change a non-critical configuration?
You know you can boot to a root console with appropriate grub settings?

On default, grub creates kernel startup entries with "recovery mode" as option. Also manually, you can 'e' edit a grub entry, and add 'single root' to the option list, and then 'b' boot into the current used kernel to repair something.

Here is this described as well:
[Grub rescuemode]("http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-rescuemode-booting-single.html")

---

### Post by gspat on 2009-01-24
No I can't, unfortunately...

That was the first thing I tried,

but, like I said, in my earlier post, the terminal screen won't update once the screen fills. (it just sits there and beeps once text reaches the bottom of the screen)

I've been taking that to mean there's something not yet complete in the kernel, and I don't want to report something that's not fully in the repos yet.

So, I boot to a root shell in 28.4 to use vi to edit the line back and it works again.

---

### Post by plun on 2009-01-24
You have a comment in the master bug for this (at the end from "A Plattner")

> I got word from the X.org folks that ABI 5 is frozen, so the next round of driver releases will no longer require -ignoreABI. I *believe* there were no breakages between the version 180.22 was complied against and the frozen version, but I haven't verified that. I still don't recommend disabling the ABI check if you're not actively developing the X server.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/308410](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/308410) 


According to nVidias forum a new driver is coming, "soon" they also writes from nVidia.

---

### Post by gspat on 2009-01-24
I saw that post a few days ago, but couldn't find it again quickly... 

I guess I was thinking "soon" a few days ago might equate to "now" since kernal updates and such came down.

---

### Post by plun on 2009-01-24
Well, he works for nVidia and Xorg 1.6 is delayed, nothing nVidia can do about that.

More comments from him within this thread

[http://www.nvnews.net/vbulletin/showthread.php?t=126623](http://www.nvnews.net/vbulletin/showthread.php?t=126623)

---

### Post by gspat on 2009-01-24
No worries... :)

I'm really just waiting because compositing isn't working on compiz, so I can't use the cube (or docky) with it...

Back to using metacity composting until it's done then!

---

