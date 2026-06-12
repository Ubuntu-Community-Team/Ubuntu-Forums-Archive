---
title: "Help needed"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dimeotane on 2009-09-29
I was running Karmic Ubuntu Netbook Remix quite smoothly.  I did an update and then when I rebooted it only brings me to a terminal login.  No networking.  If I startx then keyboard or mouse is not working.   What on earth happend?  I've never had a sudo apt-get upgrade that did this before.   And how do I fix it?
I don't need to reinstall the system do I?

I thought I could try another update and upgrade to see if that fixes it, but I don't have any ethernet.

---

### Post by fishy6969 on 2009-09-29
[LIST=1]
[*]Does it give a 'HAL' error during boot-up?
[*]Try reverting to an earlier kernel in Grub
[/LIST]

---

### Post by dimeotane on 2009-09-29
I also had to do quite a few fsck.  After those were done I tried booting into the recovery with networking.  Now I'm running a sudo apt-get update and will try to see if there's another upgrade.

I'm fishing through the earlier thread, update broke my boot.  Sounds similar.
[http://ubuntuforums.org/showthread.php?t=1265224](http://ubuntuforums.org/showthread.php?t=1265224)

---

### Post by kansasnoob on 2009-09-29
If you can boot in Recovery Mode, and if it completes, you could try the Shell w/Networking option (not the proper wording but you'll recognize it when you see it).

---

### Post by fishy6969 on 2009-09-29
[http://ubuntuforums.org/showthread.php?t=1267183&highlight=hal+error+karmic&page=2](http://ubuntuforums.org/showthread.php?t=1267183&highlight=hal+error+karmic&page=2)

Post 15 on this thread worked for me.

---

### Post by ranch hand on 2009-09-30
If all you can get to is the text login it should be enough.
```

sudo start udev
sudo start hal
sudo start network-manager
sudo start gdm

```
If you are lucky this will bring up the login screen.

If not you should be on the web and can update.  I would also run "sudo dpkg --configure _a" first to see if you have unfinished business in dpkg.

I would run dist-upgrade in this situation but that is up to you.

---

