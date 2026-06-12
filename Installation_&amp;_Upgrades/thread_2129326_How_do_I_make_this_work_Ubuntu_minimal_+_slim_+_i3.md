---
title: "How do I make this work? Ubuntu minimal + slim + i3"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by isakkeyten on 2013-03-25
I don't know if i should've opened this in absolute beginner section or here, since im not an ABSOLUTE beginner but i am a newbie n_n

So I installed ubuntu minimal 12.10 (the 30 mb version), following this tutorial [http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24) right up to "Post installation".
Now, I don't want to use gdm or open box, id like to use slim as a login manager and i3 as a tiling window manager (and a lot of other programs but they are not the problem).
I reached the post installation part in the tutorial, as ive said, and installed i3 and slim using the apt-get install command from the console mode.
Now i have no idea how to configure ubuntu to start in graphical mode starting slim, trough which i can login and start an i3 session.

Can you please help me? :confused:

---

### Post by ibjsb4 on 2013-03-26
Try

```
sudo dpkg-reconfigure slim
```

---

