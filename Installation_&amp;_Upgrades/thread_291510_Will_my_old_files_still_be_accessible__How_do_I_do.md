---
title: "Will my old files still be accessible?  How do I do it?"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by r2debo on 2006-11-02
I'm new to Linux and am attempting to install Ubuntu.  I currently run Windows and use 50GB, with 10GB remaining.  When I establish the partitions for installation and set everything up, will I be able to access the files contained in the Windows partition?  (By files I mean, .office, .movies, .mp3s, etc.)  And how will I be able to access Windows again to use programs I need that Ubuntu does not yet support?

Thanks!

---

### Post by taurus on 2006-11-02
You can mount your Windows partition and you will have full access to everything in it from Ubuntu!  If you need to run some Windows programs from Ubuntu, you need to install some type of emulator like wine!  And if you can tell use what Windows programs you need to run in Ubuntu, I am sure somebody will tell you some equivalent native programs in Ubuntu...

---

### Post by r2debo on 2006-11-02
Taurus - thanks!  I was going to create 2 seperate partitians, one of ubuntu and one for the swap.  When you say that I need to mount Windows, what do I tag it with?  /, /windows?  Sorry for my ignorance and thanks for your help.

---

### Post by taurus on 2006-11-02
Chances are the installer will find your Windows partition and creates and entry in /etc/fstab for your Windows.  It would be mounted automatically upon boot and if it doesn't, then you just edit /etc/fstab and add a line to it.  Read this link below if you want to know more about mounting Windows partitions...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, post it back here and either I or somebody else will show you how to do it.  ;)

---

### Post by r2debo on 2006-11-02
I'll give it a shot.  Thanks for your help!

---

### Post by taurus on 2006-11-02
Good luck.

---

