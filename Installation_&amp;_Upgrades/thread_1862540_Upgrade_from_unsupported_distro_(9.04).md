---
title: "Upgrade from unsupported distro (9.04)"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by Chocrates on 2011-10-16
Long story short, I lost my root partition and my cd drive broke, so I ran to Unetbootin, and 9.04 was the only one i could get to boot.

Now i would like to do some development again, and need a more recent version.  Does anyone know how i can upgrade from 9.04 to 10.04 or 11.10?

I have tried mounting 9.10 and pointing the upgrade manager at it, but it doesn't seem to recognize the mounted cd.

---

### Post by Bölvaður on 2011-10-17
What I am doing right now is upgrading from 9.04 to 9.10 and then Im planning on going further... got both 10.04 and 11.04 but am searching the forums to see if I need to upgrade to the next release or if I can jump into the latest one.

Try mounting the same way as I did (you can see here below).

I downloaded the 9.10 alternate cd and then...

```
sudo mount -o loop ~/ubuntu-9.10-alternate-i386.iso /media/cdrom
gksu "sh /media/cdrom/cdromupgrade"
```I'll let you know how it will go.

---

### Post by Chocrates on 2011-10-17
Hey thanks!

I think i didn't get the alternate .iso so i couldn't find the cdromupgrade.

Turns out the new unetbootin installs 11.10 fine.  (whether its because i get to use it on linux this time, or it fixed some bugs, i cannot say)

---

### Post by Bölvaður on 2011-10-17
> **Chocrates said:**
> 
I think i didn't get the alternate .iso so i couldn't find the cdromupgrade.

[http://old-releases.ubuntu.com/releases/karmic/](http://old-releases.ubuntu.com/releases/karmic/)

If you still haven't found it try that link. It is where I got my iso from. To get newer releases just remove "old-" from the url, or just find other downloads on the ubuntu.com website.

---

