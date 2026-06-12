---
title: "[SOLVED] Desktop not refreshing properly"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by psyphen on 2008-10-10
I just recently upgraded to Intrepid, but am having some problems. It all started when I "partially upgraded" and it removed compiz. I reinstalled with basically no problems, except now it seems like the screen doesn't refresh properly when new content is shown.

Firefox is one of the first offenders, although file browsing and basically everything else suffers almost equally. Only part of the page shows up (usually whatever part I'm hovering over) until I scroll or somehow cause the entire window's contents to change. Is there an easy way to fix this? It seems like there should be, but I can't find any setting to change that would solve it...

I tried to take a screenshot with no luck, because it redraws the screen before taking the snapshot.

Thanks much for your help,
Jake (psyphen).

---

### Post by overdrank on 2008-10-10
Moved :)

---

### Post by tim1 on 2008-10-10
Do you have a geforce 8400 by any chance?

I and someone else have the exact same problem as described here in this thread: [http://ubuntuforums.org/showthread.php?t=943896](http://ubuntuforums.org/showthread.php?t=943896)

---

### Post by loomsen on 2008-10-10
I wouldn't upgrade to a verion which is yet to be provided. A fresh install would have done it, I'm sure. Just yesterday a friend of mine did exactly the same. She tried upgrading from hardy, and afterwards wasn't able to get the driver for her nvidia set up correctly. 
Then she installed from a cd today, and everyting worked just fine.

So, with upgrades, which also work fine in most of the times, you gotta be careful as long as it's still testing, tho I didn't have any problems in debian. Started off with the stable, upgraded to testing, and a couple of days l8r I yet again upgraded to unstable, and everything worked fine actually. Perhaps pinning would have been a better choice here...

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

Point 3.8 could be of interest:

How to keep a mixed system.

---

### Post by psyphen on 2008-10-11
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904)

This fixed it for me. Edit /usr/bin/compiz and change line 80 to INDIRECT="yes".

[http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)
That also may be of assistance.

---

### Post by minisori on 2008-10-12
I have this problem to with a fresh install of intrepid in the laptop, mine is a 9600 GT and latest driver.

---

