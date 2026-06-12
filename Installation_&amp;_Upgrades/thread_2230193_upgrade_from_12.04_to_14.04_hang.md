---
title: "upgrade from 12.04 to 14.04 hang"
date: 2014-06-17
forum: Installation &amp; Upgrades
---

### Post by bobwdn on 2014-06-17
I have upgraded a couple of my computers from 12.04 (completely updated before I began 14.04 upgrade) to 14.04 with ```
sudo update-manager -d
``` and everything went fine with these first two machines.

Now, my third machine has hung at "Unpacking python 2.7" and the terminal says ```
GLib-CRITICAL **: g_once_init_leave: assertion `result !=0' failed at /usr/lib/perl/5.18/DynaLoader.pm line 207.
``` and it has been in this state for over two hours as I write this.

I fear the worst. Is there a way to abort and restart the upgrade?

---

### Post by Bucky Ball on 2014-06-17
Details of the problematic machine, thanks. Make, model, CPU, graphics card and amount of installed RAM. Any and/or all of this info and anything else of relevance you can think of please.

---

### Post by bobwdn on 2014-06-18
> **Bucky Ball said:**
> Details of the problematic machine, thanks. Make, model, CPU, graphics card and amount of installed RAM. Any and/or all of this info and anything else of relevance you can think of please. Answering my question with a question . . . :confused:

Hardware . . . the question is, and I will quote my first post, *"Is there a way to abort and restart the upgrade?"*

---

### Post by bobwdn on 2014-06-18
After some logical thought, if the upgrade is "Unpacking Python 2.7" then logically the "install" process has not started and the upgrade process is simply downloading packages in anticipation of installation. So this morning (8 hours later) the screen still says the same thing it did last night (install has not progressed), I ssh into this box and ```
sudo shutdown -h 0
```

And the box did indeed shutdown. Tonight, when I return to this project I will try again. (At this point, if the box will not start on 12.04LTS and allow me to proceed with upgrade I can install 14.04 from a desktop cd as /home is in seperate partiton.)

---

### Post by bobwdn on 2014-06-18
Closing this. System was borked up. Re-installed 14.04 from scratch. Learned my leason.

---

### Post by Bucky Ball on 2014-06-18
*Thread closed.*

Closed it for you as you can't. Good luck.

---

