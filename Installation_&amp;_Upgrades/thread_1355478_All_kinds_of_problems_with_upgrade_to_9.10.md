---
title: "All kinds of problems with upgrade to 9.10"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by jeasha on 2009-12-15
Last Monday, Dec 7, I discovered that Ubuntu was no longer upgraded automatically, at least mine wasn't,  and hadn't been for about two years.  Accordingly, I went through the process of going from 8.04 - 8.10 - 9.04 - 9.10.  The results have been less than stellar.

I have also learned that the boot loader is likewise not upgraded and, never having been told otherwise, I still have GRUB to which I switched from LILO when advised to to so last time a switch was considered good.  Why no advisory this time I have no idea.

As a result of this I now have a system that is all but non-functional.

It takes anywhere from 5 to 25 minutes and from 2 to 5 trys finally to have something running.  Each time I start up Firefox I get a message stating that it is an embarrassment that it can't start loading.

The embarrassment is Ubuntu 9.10.

It is pathetically slow, painfully slow and often, without apparent reason, it simply stops.  

I have had to restart 9.10 more times in the last week than I had to restart 8.04 in over two years and 8.04 only hung twice when I pushed the system much too hard.  Noe all I have to do is leave it for a half hour and it hangs.  I moved to Linux specifically to get away from similar problems.

So far after fighting with a well pre-structured so-called help system that seems not aware that such conditions exist even though I have seen many references to them on blogs, I have managed to get instruction to do:
sudo apt-get upgrade
sudo aptitude upgrade
sudo apt-get autoremove

This seemed to have helped a bit.  The number of retries to boot have been cut in half and I have longer periods of use before system display lock.  I can still move the mouse pointer over the screen but doing so is a waste of time.  Thee is no reaction to any input attempt.  It seems that if I try to do quick input I am getting a way ahead of a system that is far too slow to keep up. 

Other than abandoning Ubuntu for something else, is there anything that can be done?

---

### Post by solar george on 2009-12-15
Well the quickest solution would be to re-install from scratch (backup your data first).

If you want to continue trouble shooting please attach the output of
```
dmesg
```
and post the output of 
```
uname -a
lspci
```

---

