---
title: "Remote (partial) reinstall"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bryanchapman9999 on 2009-10-08
Hi,

Is there a way, remotely, to remove all but essential base system - down to a standard server install I guess?

My apt-get upgrade produces so many errors about incomplete packages that I don't know how to resolve.

It complains mainly about python being broken, but I've attached a log if anyone has any ideas.

I don't want to do a cd / usb install if I can help it, just strip it down to the bare minimum via ssh.

Cheers
Bryan

---

### Post by slakkie on 2009-10-08
You could try to:

```

aptitude reinstall ubuntu-desktop ubuntu-minimal ubuntu-standard 

```

Why the hell you said yes to the changes is beyond me.

---

### Post by bryanchapman9999 on 2009-10-08
> **slakkie said:**
> 

Why the hell you said yes to the changes is beyond me.

It broke python after an update, I'm in the state I'm in because I tried to fix it myself.

Thanks for your help though:roll:

---

### Post by bryanchapman9999 on 2009-10-08
> **slakkie said:**
> You could try to:

```

aptitude reinstall ubuntu-desktop ubuntu-minimal ubuntu-standard 

```


Need to get 0B of archives. After unpacking 74.5MB will be freed.
Do you want to continue? [Y/n/?] Y
E: I wasn't able to locate file for the gnome-session-bin package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the gnome-session-bin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download


Oh well....

---

### Post by bryanchapman9999 on 2009-10-09
Anyone? 

I guess I'm doing a reinstall tonight then :-(

---

