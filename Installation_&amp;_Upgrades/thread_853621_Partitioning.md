---
title: "Partitioning"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by Digital_Terror on 2008-07-08
I'm having trouble manually configuring the partitions during install. I cannot find a setup that lets both my hdd's visible in the gui. Any suggestions for an optimal setup?

---

### Post by Pumalite on 2008-07-08
Dual booting? Vista or XP?
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
I'd leave:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.

---

### Post by Digital_Terror on 2008-07-08
> **Pumalite said:**
> 
I'd leave:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.

No, not dual booting. But would that config let both of my hard drives show up in the gui?

---

### Post by Pumalite on 2008-07-08
Sure. You can also use your 2nd hard drive for /home.

---

### Post by SkonesMickLoud on 2008-07-08
Up in the top right corner of the GParted screen, you should see a box with something along the lines of "/dev/sda (xxxGiB)".  Click on that and a menu listing both drives will drop down.

As far as I know, there isn't a way to show both at once.

---

### Post by Digital_Terror on 2008-07-08
Kthxbai I sold the problem.

---

### Post by SkonesMickLoud on 2008-07-08
Cool.  Mark this thread as solved if you would.

---

