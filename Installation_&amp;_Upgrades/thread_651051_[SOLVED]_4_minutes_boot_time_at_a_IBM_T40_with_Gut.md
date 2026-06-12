---
title: "[SOLVED] 4 minutes boot time at a IBM T40 with Gutsy"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by thefriend on 2007-12-27
Hello,

I want to shorten the boot time of my T40.
I have a fresh installation of Ubuntu 7.10 there.
It takes 3 minutes to the login screen and another minute to have the complete desktop.
XP boots normal on the same t40 so I think hardware should be ok.
When Ubuntu has started it seems to operate normally.

Can somebody help me to speed up the boot process?

---

### Post by seshomaru samma on 2007-12-27
did you try installing BUM?

if you are more comfortable with the command line you can try installing sysvconfig
and run it with the command
```
sudo sysvconfig
```

---

### Post by Partyboi2 on 2007-12-27
> **thefriend said:**
> Hello,

I want to shorten the boot time of my T40.
I have a fresh installation of Ubuntu 7.10 there.
It takes 3 minutes to the login screen and another minute to have the complete desktop.
XP boots normal on the same t40 so I think hardware should be ok.
When Ubuntu has started it seems to operate normally.

Can somebody help me to speed up the boot process?
Here is a how-to for speeding up boot
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
you also might want to check out this one concerning slow login to desktop (known bug)
[http://ubuntuforums.org/showthread.php?t=585635](http://ubuntuforums.org/showthread.php?t=585635)

---

### Post by thefriend on 2008-01-01
First of all I want to thank you for your posts.
I tried a few days to enable / disable several tasks using BUM and SYSVCONFIG.

But i had no success.
The results differed only a few Seconds.

Then I asked myself why I don't see a bootsplash while booting and tested to[B] remove the splash entry in the /boot/grub/menu.lst
[/B]
That was a success!

Now my T40 boots in about 1 minute!


The only thing is: I have no bootsplash now while booting ;)

---

