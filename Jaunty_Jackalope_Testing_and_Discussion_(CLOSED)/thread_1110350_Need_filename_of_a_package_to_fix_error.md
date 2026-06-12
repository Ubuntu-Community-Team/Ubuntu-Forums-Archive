---
title: "Need filename of a package to fix error"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cajunaggie on 2009-03-29
In an attempt to deal with some graphics issues, I made things worse. I installed the ATI driver package to see if that would help and uninstalled compiz to cut back on the processor load. When I rebooted, I was fine up until the GUI tried to kick in, at which point the I saw a lot of strange, distorted, and pixelated images, which flickered a bit. Then my screen went dark and I got a monitor message telling me there was no video feed.

I ran LiveCD (with the usual errors) and was able to see things just fine.

Unfortunately I can't remember the name of the package I installed and my only means of removing it is via console. Does anyone have any idea what it might be?

EDIT: I believe it was the ATI Catalyst Driver package.

---

### Post by ktp on 2009-03-29
xorg-driver-fglrx?

---

### Post by xebian on 2009-03-29
> **cajunaggie said:**
> In an attempt to deal with some graphics issues, I made things worse. I installed the ATI driver package to see if that would help and uninstalled compiz to cut back on the processor load. When I rebooted, I was fine up until the GUI tried to kick in, at which point the I saw a lot of strange, distorted, and pixelated images, which flickered a bit. Then my screen went dark and I got a monitor message telling me there was no video feed.

I ran LiveCD (with the usual errors) and was able to see things just fine.

Unfortunately I can't remember the name of the package I installed and my only means of removing it is via console. Does anyone have any idea what it might be?

To search for installed packages with say 'fglrx' in their name execute this code

```

dpkg -l | grep fglrx

```

You might search also for 'xorg-video' by replacing 'fglrx' above.

---

### Post by Bakon Jarser on 2009-03-29
```
cd /var/cache/apt/archives
ls -t
```

That will list all downloaded packages in the order they were last modified.  The packages most recently modified will be listed first.

ls -u -lt will sort by access time.

---

### Post by cajunaggie on 2009-03-29
Fixed! Thanks for the help guys.

---

