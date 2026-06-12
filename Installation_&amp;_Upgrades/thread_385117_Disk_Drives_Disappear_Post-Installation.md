---
title: "Disk Drives Disappear Post-Installation"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Kaphix on 2007-03-15
After installing Ubuntu, my hard drive disappears, and it says I have 2 CD drives. I can only access my hard drive from windows now. And I think my preferences get reset every time I restart.

This makes it so I can't save or download any files.

---

### Post by taurus on 2007-03-15
You probably just need to mount your Windows partition before you can access it.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Kaphix on 2007-03-15
Thanks. I'll try that.

[EDIT] What in the crap? My partition editor isn't showing up anymore..
[EDIT2] Seems I just need the terminal.

---

### Post by taurus on 2007-03-15
If you need to open a terminal, click Applications -> Accessories -> Terminal.

---

### Post by Kaphix on 2007-03-15
> **taurus said:**
> You probably just need to mount your Windows partition before you can access it.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Heres the output.

[IMG]http://i25.photobucket.com/albums/c69/Kaphix/bla-1.png[/IMG]

---

