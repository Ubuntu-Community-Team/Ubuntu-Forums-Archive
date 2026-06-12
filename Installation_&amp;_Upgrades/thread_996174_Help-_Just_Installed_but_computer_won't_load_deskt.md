---
title: "Help- Just Installed but computer won't load desktop"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by kjhughes23 on 2008-11-28
Hi, I just installed Ubuntu on my PC with the Alternate ISO CD and it lets me log in but after that all it shows is the mouse and a beige screen. I haven't even used it yet. I rebooted a few times but still the same. My Install went perfectly but now I can't use Ubuntu

Any Help is greatly appreciated

PS I have a HP Pavilion a1110n

THANKS

---

### Post by Pumalite on 2008-11-28
Try Recovery Mode>'xfix'

---

### Post by AndyCee on 2008-11-28
Try removing compiz, which has been known to cause this problem.


```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

You can log in via terminal by ctrl+alt+F1, then reboot the machine.

Please post back with results.

---

### Post by kjhughes23 on 2008-11-28
Thanks I will try that!

---

### Post by kjhughes23 on 2008-11-28
Thanks, I now have Ubuntu, which I&#7743; typing on

---

### Post by AndyCee on 2008-12-09
Awesome.

---

### Post by spamless on 2010-10-29
> **AndyCee said:**
> Try removing compiz, which has been known to cause this problem.


```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

You can log in via terminal by ctrl+alt+F1, then reboot the machine.

Please post back with results.

Thanks.  Here we are more than two years later, and I have been trying for four days to load Maverick Meerkat from a new installation on an old eMachines laptop.  It was running Lucid more or less successfully before.  Anyway, the Desktop panels would never load.  I tried what seemed like everything for hours.  I read all sorts of threads after searching using the same search terms, or similar ones, that finally now eventually landed me here.  I saw and tried a dozen fixes.  I originally had installed the netbook version of Maverick, but when I couldn't resolve this I trashed that and installed the Alternate version (thinking there were some weird missing drivers).  None of that helped.

Well, your suggestion fixed it instantly.  So if this was "known to cause problems" two years ago, why is it still causing problems two years later in Maverick, and why aren't any of the other dozen threads I read talking about it?  Sheesh!

And what the hell is compiz, and why does it install in the first place if it's known to cause problems, and why don't or do I want it?  Thanks.  (Okay, I see the Wikipedia article on that, [http://www.answers.com/topic/compiz?method=26&initiator=CANS]("http://www.answers.com/topic/compiz?method=26&initiator=CANS") -- so at least I have a vague idea what it is.  But I still don't know if I'll miss it, having now uninstalled it.)

Btw, the reason I left Lucid and went to Maverick in the first place, or tried, is that I turned on the laptop for the first time in 93 days in Lucid and found 158 updates that wanted to be installed.  I did that -- it took quite a while -- and then rebooted as requested.  Kernel was now not found!  I knew I would be able to fix that if I spent about as long as I ended up, anyway, on this new problem, trying to fix it.  But I also knew Maverick was out, so -- since there was absolutely nothing of interest on the machine anyway -- I decided it would be much faster and easier to just install Maverick from scratch.  Wrong!  What a nightmare.  The whole point was, it's an old secondary machine I keep around, and I did not feel like spending days troubleshooting it just to have a working OS.

Thanks again for the fix.

---

