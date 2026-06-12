---
title: "Updates without video upgrade"
date: 2014-09-07
forum: Installation &amp; Upgrades
---

### Post by rlntel on 2014-09-07
**Brief vent:** I left Windows in '08 with plans of never looking back. Things progressed nicely through the years up to Ubuntu 12.04. I even purchased a System76 to reaffirm my dedication. Then, 13.04 came along and I upgraded, but my ability to see my dual monitor vanished. Previously, I would have looked at this as a minor Linux challenge, but on about the 4th day of trying I was now losing time on work I had to complete. In frustration, I dropped back down to 12.04 and all was well. Then, Synaptic unexpectedly updated the video driver in my 12.04 install and my dual monitor was gone again. I was also presented with the opportunity to upgrade to 14.04, so in hopes that driver problem was fixed in this version, I upgraded. As nice as it looked, like 13.04, dual monitoring was not available OOB in 14.04, so I dropped back down to 12.04 and all is right with the world...with the exception of the 357 packages that need to be updated in Synaptic. I don't want to update though, since I know my video driver will get whacked and I'll lose my dual monitor.

****ATTENTION SYSTEM76**: NO THANKS TO YOU FOR COMING OUT WITH SOME LEVEL OF SUPPORT ON THIS!

With no real time available to become the level of Linux admin I'd really like to be, my only alternative is to try to block the update to the driver while allowing updates to everything else. I just don't know how.

Can someone please explain?

Thanks in advance,
Rob

---

### Post by egeezer on 2014-09-07
There is a way to issue a Hold order on packages in Synaptic, which will respond to an update by setting the package update as Recommended and unchecked.  If you want it, check it; if not, don't.  On another computer (I can't access it at the moment, so I don't remember how to mark the Hold) I have been using an ancient fglrx driver update-free for probably a year.

---

### Post by Vladlenin5000 on 2014-09-07
Here's the thing most people forget after upgrading a System76 computer to a new Ubuntu release: [http://knowledge76.com/index.php/Version_Upgrade](http://knowledge76.com/index.php/Version_Upgrade)

---

### Post by rlntel on 2014-09-09
E & V,

Thanks for the replies. I'll try the System76 approach first.

---

### Post by rlntel on 2014-09-09
Vladlenin,

I followed the instructions here, [http://knowledge76.com/index.php/Version_Upgrade](http://knowledge76.com/index.php/Version_Upgrade), but it did not help.

No additional drivers appear.

This sux!

---

### Post by QIII on 2014-09-09
Hello!

Can you give us the specs on your machine?

---

### Post by kansasnoob on 2014-09-09
Take a breath and let's figure out one thing at a time ;)

Regarding 12.04 it sounds like you may be caught in [HWE EOL]("https://wiki.ubuntu.com/1204_HWE_EOL") but I can't be sure until I see the output of:

```
uname -r
```

If that's the case I may be able to help you with 12.04 (Precise) ............. or maybe we should figure out if we can get 14.04 (Trusty) to work on your hardware. If the latter then the output of this command will possibly help us:

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

We can only try :)

---

