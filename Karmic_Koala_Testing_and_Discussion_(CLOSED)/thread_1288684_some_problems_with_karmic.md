---
title: "some problems with karmic"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bryn_fischer on 2009-10-11
Hello-  I have only been using Ubuntu for about a month now and decided to upgrade to Karmic.  Now it seems as if I can't get my printer working- all it does is say processing and never prints.  Also, no updates have been made sine upgrading and now I get an error to manually check for updates but none are found.  Any help would be greatly appreciated. Thank you.

---

### Post by yeats on 2009-10-11
> Hello- I have only been using Ubuntu for about a month now and decided to upgrade to Karmic.

There are always risks with upgrading to a beta version of a release, especially if you need your computer to work ;-)

> Now it seems as if I can't get my printer working- all it does is say processing and never prints.

Did you upgrade from Jaunty?  Assuming your printer worked before, you might have to re-install the printer.  You've probably thought of that, but just suggesting.  It's possible that Karmic's device drivers are not yet all there...

> Also, no updates have been made sine upgrading and now I get an error to manually check for updates but none are found. Any help would be greatly appreciated. Thank you

You could open a terminal and type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

If there are any errors, report those back - perhaps they are solvable.

I'll also recommend using VirtualBox to test pre-release versions, rather than upgrading your production system.  That way you're on the bleeding edge without the costs :-)

---

### Post by djyoung4 on 2009-10-11
i have never seen a question answered so fully on here

---

### Post by bryn_fischer on 2009-10-11
Thank you.  I am running the apt get at the moment.  A lot to learn about this program, guess I shouldn't have tried to jump the gun.

The apt get worked.  I also noticed that on the boot screen nothing said fail also.  Thanks for your help, I'm looking forward to learning more about Ubuntu.  Loving it so far.

---

### Post by yeats on 2009-10-11
> Thank you. I am running the apt get at the moment. A lot to learn about this program, guess I shouldn't have tried to jump the gun.

Curiosity & taking risks are the only ways to learn ;-)

> The apt get worked. I also noticed that on the boot screen nothing said fail also. Thanks for your help, I'm looking forward to learning more about Ubuntu. Loving it so far.

Great - upgrading to a beta this close to the release date isn't that crazy, but I'm one who waits (or tries to :-) ) until a couple of months into the release to upgrade.  I've been burned a couple of times!

Good luck.

> i have never seen a question answered so fully on here 

Thanks, djyoung4.  Nothing's more frustrating from the asker's point of view than an incomplete answer.

---

