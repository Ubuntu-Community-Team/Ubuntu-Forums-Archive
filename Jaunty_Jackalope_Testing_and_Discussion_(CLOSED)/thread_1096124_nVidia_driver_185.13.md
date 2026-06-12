---
title: "nVidia driver 185.13"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Sockerdrickan on 2009-03-14
**64 bit** [ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/)
**32 bit** [ftp://download.nvidia.com/XFree86/Linux-x86/185.13/](ftp://download.nvidia.com/XFree86/Linux-x86/185.13/)

:popcorn:

---

### Post by jfernyhough on 2009-03-14
More information:

[http://www.nvnews.net/vbulletin/showthread.php?p=1957328](http://www.nvnews.net/vbulletin/showthread.php?p=1957328)

First release from new driver cycle, so this one could be quite buggy.

--edit
Been looking for a changelog, the only information I have found so far is that the driver has two new xorg.conf options and it fixes some speed issues with Compiz and VPDAU.

[http://www.nvnews.net/vbulletin/showthread.php?t=130008](http://www.nvnews.net/vbulletin/showthread.php?t=130008)

---

### Post by plun on 2009-03-14
It works just fine but gave me some trouble during install

nvidia-glx-180 and dkms removed and also 180.37 from nVidia earlier installed.

also sanitized all nVidia.ko
```

locate nvidia.ko
```


```
sudo sh NVIDIA-Linux-x86_64-180.37-pkg2.run **--uninstall**
```

after that it was OK with a install....  "snappy" and good performance including Compiz.   

;)

---

### Post by thefirstM on 2009-03-14
You could just use the packages I have compiled in [my PPA]("https://launchpad.net/~thefirstm/+archive/ppa").  I always try to keep the latest Nvidia drivers there.

---

### Post by ruik on 2009-03-14
> **thefirstM said:**
> You could just use the packages I have compiled in [my PPA]("https://launchpad.net/~thefirstm/+archive/ppa").  I always try to keep the latest Nvidia drivers there.

Thanks! Installing the latest Nvidia drivers now. :)

---

### Post by jfernyhough on 2009-03-14
I've just restarted with 185.13 installed from thefirstM's PPA (thanks by the way) and although my ttys are still blank the overall effect is striking. Vastly reduced CPU usage (no more Xorg sitting with 5-15% CPU) and Firefox scrolls quickly.

Nice.

---

### Post by paul_in_london on 2009-03-14
> **jfernyhough said:**
> I've just restarted with 185.13 installed from thefirstM's PPA (thanks by the way) and although my ttys are still blank the overall effect is striking. Vastly reduced CPU usage (no more Xorg sitting with 5-15% CPU) and Firefox scrolls quickly.

Nice.

Yeah, installed from the same PPA and it's working Ok.

I also find that tty1 is blank unless I select another tty first and go back to it.

---

### Post by plun on 2009-03-15
> **paul_in_london said:**
> 
I also find that tty1 is blank unless I select another tty first and go back to it.

I noticed the same behavior with 180.37 and if I press Ctrl-alt-f1 (f2-f6)**twice** the tty works...

Great driver anyway..;)

---

### Post by Nullack on 2009-03-15
Yeah, the tty is a standard bug :)

This latest revision appears to be working ok so far on my test system.

---

### Post by biasquez on 2009-03-15
for me, tty doesn't work with this driver...

---

### Post by Ng Oon-Ee on 2009-03-15
> **biasquez said:**
> for me, tty doesn't work with this driver...
Has it ever?

My tty works only in single-monitor. Never gotten it to work on dual-head.

---

### Post by biasquez on 2009-03-15
> **Ng Oon-Ee said:**
> Has it ever?

My tty works only in single-monitor. Never gotten it to work on dual-head.

i have laptop, so single-monitor..with all nvidia drivers tty doesn't work..with nv driver it works...i don't know how solve this problem

p.s. is it possible to send this problem/bug to nvidia?

---

### Post by Ng Oon-Ee on 2009-03-15
> **biasquez said:**
> i have laptop, so single-monitor..with all nvidia drivers tty doesn't work..with nv driver it works...i don't know how solve this problem

p.s. is it possible to send this problem/bug to nvidia?

Of course. Nvidia is actually quite responsive to its Linux users (well, except for open-sourcing their drivers). Go to the nvidia forums, there's a Linux Drivers section. I read there for updates on GC-specific issues, have also posted some stuff there. Registration requires a non-free email address though (or a lesser known free one that's not on their blacklist).

One thing to note, if you post a bug on those forums please be polite. There's a whole lot of total asses there who basically use bugs as an excuse for abusing the linux devs for nvidia.

[Link for you.]("http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14")

Oh, and I use a laptop as well, with an external screen (for dual-head). If the external screen is plugged in I can't ever get it to work, but with only the DFP I have all my ttys no problem.

---

