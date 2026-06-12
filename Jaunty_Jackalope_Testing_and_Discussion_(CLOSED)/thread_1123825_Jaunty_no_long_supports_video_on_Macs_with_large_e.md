---
title: "Jaunty no long supports video on Macs with large external displays"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Harkins on 2009-04-12
I tested Jaunty and [filed a bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359831") when I found it could no longer play back video. It turns out xvideo's new dependency on DRI means that I can't really play video any more (the software driver works, but quality is very low).

I'm posting for two reasons: first, I'm hoping that someone knows of a workaround.

Second, I think it likely this affects most other models. I've updated the [wiki page for my model](https://help.ubuntu.com/community/MacBook1-1/Jaunty) but I'm pretty sure the more recent Macbooks and iMacs also use Intel graphics cards that are affected by this. I wanted folks to know, and if you have one, please test with a beta CD and update the wiki pages if those are broken as well.

---

### Post by cyberdork33 on 2009-04-13
Thanks.

I added the "Mactel-Support" project to your bug, so hopefully, you will get some more eyes on it. Also, you should look into filing (or finding) a bug in the upstream bugtracker (I believe this is the freedesktop.org bugzilla) and linking it in launchpad. That should move things along a bit faster.

---

### Post by Harkins on 2009-04-13
Thanks for your suggestions, I'm pretty unfamiliar with the process and appreciate the guidance.

I found two related bugs in the freedesktop bugzilla and linked them from a comment.

---

