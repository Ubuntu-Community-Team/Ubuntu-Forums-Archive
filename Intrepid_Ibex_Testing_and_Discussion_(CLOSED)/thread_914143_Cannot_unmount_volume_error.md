---
title: "Cannot unmount volume error"
date: 2008-09-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by excogitation on 2008-09-08
I don't know if it's just me, but I always get this error "Cannot unmount volume" when I unmount an SD card from the right-click menu.

The thing is that it gets unmounted correctly afaik (no more "disk" folder in /media).

Running "sudo umount /media/disk/" works without the error.

---

### Post by ronacc on 2008-09-08
don't feel lonley when I mount an internal drive that is not in fstab using places>computer it tells me "cannot mont volume " at the same time it is mounting the volume . I don't know the bug # associated with this search launchpad for it .

---

### Post by excogitation on 2008-09-08
Ok, thanks.

I couldn't find a related bug on launchpad, but I guess it's going to get fixed sometime then.

---

### Post by scaine on 2008-09-08
> I couldn't find a related bug on launchpad, but I guess it's going to get fixed sometime then. 

Sorry for stating the obvious : but clearly this won't be fixed unless someone files a bug...

And since I haven't personally seen this behavior on Intrepid, I'd suggest you go for it.

[Edit] Turns out there is a bug : [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95368](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95368) which details a fairly simple fix - delete stale entries in your /media directory.

---

### Post by Ripfox on 2008-09-08
Is that all it takes? This happens to me too.

---

### Post by ronacc on 2008-09-08
that bug was fixed months ago , go ahead and open a new one.

---

### Post by excogitation on 2008-09-08
> **scaine said:**
> Sorry for stating the obvious : but clearly this won't be fixed unless someone files a bug...

And since I haven't personally seen this behavior on Intrepid, I'd suggest you go for it.

Well that's why I'm asking here first - because it can also be some misconfiguration on my part.
> **scaine said:**
> 
[Edit] Turns out there is a bug : [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95368](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95368) which details a fairly simple fix - delete stale entries in your /media directory.

I dont have any stale entries in /media

```
# ls /media/
cdrom  cdrom0  media  windows
```

---

### Post by scaine on 2008-09-09
> **ronacc said:**
> that bug was fixed months ago , go ahead and open a new one.

True - using [https://bugs.launchpad.net/ubuntu/intrepid](https://bugs.launchpad.net/ubuntu/intrepid), it's clear that there's no bug related to this issue logged against Intrepid itself.

And if you have no stale entries, it's unlikely to be a regression (and even if it was, you'd still want to log a new bug).

Odd that I haven't seen this myself though, since I use USB keys all the time for transferring big files onto my Eee (too slow over wireless).

BTW, what's the "media" entry for?  You have a /media/media directory? :confused:

---

### Post by ronacc on 2008-09-09
this may be one of those that gives different symptoms or maybe more than one bug , I do not get the "cannot unmount volume" warning when I unmount something what I get is an "unable to mount location" when I mount something with places>computer but not when a usb stick automounts if I unmount the usb stick and then remount it with places>computer I do get the "unable to mount location" but it does mount .

---

### Post by excogitation on 2008-09-09
> **scaine said:**
> True - using [https://bugs.launchpad.net/ubuntu/intrepid](https://bugs.launchpad.net/ubuntu/intrepid), it's clear that there's no bug related to this issue logged against Intrepid itself.
[now there is]("https://bugs.launchpad.net/ubuntu/+bug/268356")
> **scaine said:**
> 
And if you have no stale entries, it's unlikely to be a regression (and even if it was, you'd still want to log a new bug).

Odd that I haven't seen this myself though, since I use USB keys all the time for transferring big files onto my Eee (too slow over wireless).

BTW, what's the "media" entry for?  You have a /media/media directory? :confused:
/media/media is just my "media" partition (audio+video)

---

