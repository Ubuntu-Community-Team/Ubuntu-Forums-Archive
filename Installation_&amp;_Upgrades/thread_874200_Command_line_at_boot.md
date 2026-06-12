---
title: "Command line at boot"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by chejose on 2008-07-29
I just finished installing 8.04 on a new HP 2133. Everything seemed to go normal, but when I boot up it runs command line, asks for name and key, and then ends up at command line. In other words, no graphic screens even show up.

So "something" is missing, and hope one of you will know what.

Thanks, 

José

---

### Post by tuxxy on 2008-07-29
Try entering this command and GNOME should load up,

```
startx
```

If no luck you could try;

```
sudo startx
```

If still no luck log down the error and print it here.

---

### Post by chejose on 2008-07-29
Thanks for getting back on this.

I tried using startx, but the response was "command not found".

And I will need help to find the error log... I could find it with locate, but don't remember its exact name.  So back to you.

José

---

### Post by Mothinator on 2008-07-29
Which version of 8.04 did you install--Desktop or Server?

I don't believe the Server edition comes with a graphical display manager.

If you installed the server addition, try running:
```

sudo apt-get update&&sudo apt-get install ubuntu-desktop

```

---

### Post by chejose on 2008-07-29
It is the desktop version. When I used apt-get to install startx, a batch of files seem to be missing. I installed a couple of others that it said were missing, but it looks like the installation itself is flawed.

José

---

### Post by chejose on 2008-07-29
OK... I think the best would be to simply do a new installation. If that doesn't work, back to the forum!

José

---

