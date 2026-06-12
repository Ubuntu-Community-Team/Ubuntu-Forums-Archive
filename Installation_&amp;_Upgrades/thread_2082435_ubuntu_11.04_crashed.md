---
title: "ubuntu 11.04 crashed"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by 333ameeth on 2012-11-09
Hi,
I had Ubuntu 11.04 previously it was running good,
but yesterday there are few problems like the top right corners volume,date,log out,etc options are gone,
then when i clicked on "system testing" it wasn't responding(i mean no result),
and after some time when i tried to restart there wasn't any movement of mouse system was hanged,
then I restarted from CPU(by pressing the button) then there was nothing only black screen and cursor. 

what is the problem with my ubuntu,
now what i have can do is there any solution.

thank you for your time.

---

### Post by Frogs Hair on 2012-11-09
11.04  reached end of life last month so you may want to install a newer version of Ubuntu.You can try the following.

Unity Not Working 

Login to Ubuntu use Ctrl + Alt + F1 to enter TTY. Next enter user name, password, and run the following command.

```
unity --reset
```


Wait until the process is complete and your user name appears again. Use Ctrl + Alt + F7 to renter the desktop environment.

If there is error reporting wait until finished. If Unity doesn't appear within a minute or two restart and login to Ubuntu.

---

### Post by Mr_JMM on 2012-11-09
> **Frogs Hair said:**
> 11.04  reached end of life last month so you may want to install a newer version of Ubuntu.

Sorry, just have to ask, apologies but what do you mean it's end of life? Isn't that an LTS release?

---

### Post by jerome1232 on 2012-11-09
not it's not, 12.04 is an LTS release, 11.04 is an old regular release.

It would probably be best to shift to 12.04

Release Schedule
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Mr_JMM on 2012-11-09
Ah, thanks for that, I always thought x.04 were always LTS releases. 

On topic, if resetting unity doesn't work and you (OP) decide to upgrade, bearing in mind the issues you have I'd opt for a fresh install rather than upgrade.

I'll go back to my hole now. Sorry for jumping in to this thread. *jumps out*

---

### Post by 333ameeth on 2012-11-22
Thank you,
  upgraded to 12.04LTS.

---

