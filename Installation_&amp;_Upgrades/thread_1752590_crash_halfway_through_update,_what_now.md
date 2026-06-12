---
title: "crash halfway through update, what now?"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by chrisbay90 on 2011-05-08
I was upgrading my laptop from 10.10 to 11.04. The laptop crashed part way through the upgrade (fairly far in, at least an hour after downloads completed, a few minutes after grub installer asked some questions). The crash was from [another issue]("http://ubuntuforums.org/showthread.php?p=10785588") besides the update

Now when the computer boots it immediately goes into kernal panic (black screen, flashing caps lock light). when selecting recovery mode, it boots for about a 5 seconds then hangs.

I can however at grub select Previous versions of ubuntu > 2.6.35-28 and it will boot succesffully and run without error. Currently running like this to post this message. For the most part everything looks as if it has upgraded. To things worth mentioning.
```
$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found
$ 
```and, apt db is broken
 ```
$ sudo apt-get update
```runs most of the way through then returns the error
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```I backed up my home folder just in case but didn't do a system backup. Wasn't worried if I broke it and had to reinstall, but this doesn't look in my (possibly incorrect) to bad.

Any idea's where to go from here?

---

### Post by carl4926 on 2011-05-08
Install from the CD and keep /home if it's separate

---

### Post by chrisbay90 on 2011-05-08
> **carl4926 said:**
> Install from the CD and keep /home if it's separate
Thank you for the suggestion carl. Yes that will give me a functional system, and it is plan C. However if anyone has any suggestions an a plan A and B that would fix my current install i would be really greatfull.

---

### Post by Quackers on 2011-05-08
Have you run ```
sudo dpkg --configure -a
``` in a terminal as the error message suggests?

---

### Post by chrisbay90 on 2011-05-08
> **Quackers said:**
> Have you run ```
sudo dpkg --configure -a
``` in a terminal as the error message suggests?

No, I was worried I would break the usable version of Ubuntu I have. Now that I think about it, it is the only logical first step forwar. Will post back with results.

---

