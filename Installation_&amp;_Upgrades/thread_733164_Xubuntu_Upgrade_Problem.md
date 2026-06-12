---
title: "Xubuntu Upgrade Problem"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by Tony89 on 2008-03-23
I attempted upgrading to Xubuntu 6.10 and I just let it sit. When I came back to the computer it had the screen saver up. I tried my password but it did not work, so I restarted the system. After rebooting, it goes to a black screen and just sits there. The initial page loads up, but it never actually makes it to the login screen.

It is similar to this problem: [http://ubuntuforums.org/showthread.php?t=420586](http://ubuntuforums.org/showthread.php?t=420586)

But the computer is not a Mac, and all the fixes there are for people with macs.

EDIT:

Apparently, I have access only to the command line. I hit the power switch and a bunch of errors printed, then I had access to the command line.

---

### Post by overdrank on 2008-03-23
> **Tony89 said:**
> I attempted upgrading to Xubuntu 6.10 and I just let it sit. When I came back to the computer it had the screen saver up. I tried my password but it did not work, so I restarted the system. After rebooting, it goes to a black screen and just sits there. The initial page loads up, but it never actually makes it to the login screen.

It is similar to this problem: [http://ubuntuforums.org/showthread.php?t=420586](http://ubuntuforums.org/showthread.php?t=420586)

But the computer is not a Mac, and all the fixes there are for people with macs.

EDIT:

Apparently, I have access only to the command line. I hit the power switch and a bunch of errors printed, then I had access to the command line.

HI and if you have access to the command prompt then you may try the command
```
sudo dpkg --configure -a
or
sudo apt-get install -f
```

---

### Post by Tony89 on 2008-03-23
The first command did the job.

---

