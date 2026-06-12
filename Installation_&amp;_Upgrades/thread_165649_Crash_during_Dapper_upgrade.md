---
title: "Crash during Dapper upgrade"
date: 2006-04-24
forum: Installation &amp; Upgrades
---

### Post by cesoid on 2006-04-24
Yes, technically this is not a Breezy Badger upgrade question, but I'm guessing it's pretty elementary, so I'm posting it here anyway.

I was following the simple directions to upgrade to Dapper Beta on [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta) under "Upgrading from Ubuntu 5.10" which basically tells you to "gksudo "update-manager -d"" and use the graphical interface to start the upgrade. It successfully downloaded all the files (something like 1,110) and got about halfway through the upgrade and then totally froze. I doubt that the upgrading process itself was to blame, because this happens to me on a regular basis.

Anyway, as you might expect, when I restarted the computer it was not happy. But I did get a command prompt, so I think I should be able to reinstall, since I have all of the files floating around somewhere, and I figure I should be able to do this through apt-get, but being a linux newbie, I can only guess as to how (and as to whether this is actually possible). (I probably should have taken note of what thing it was installing when it froze, but of course, I didn't.)

If I can't do this, I'm probably just going to use the computer I'm typing on right now to burn the cd and install that way.

---

### Post by Sef on 2006-04-25
> ...now to burn the cd and install that way.

That is the best way to update your system.

> But I did get a command prompt, so I think I should be able to reinstall, since I have all of the files floating around somewhere....

Do you have a back up copy of your files?  If not back them up, if possible, before trying to install the desktop again.

sudo apt-get update

sudo apt-get install ubuntu-desktop

Note:  If everything is ok, then this should work.

---

