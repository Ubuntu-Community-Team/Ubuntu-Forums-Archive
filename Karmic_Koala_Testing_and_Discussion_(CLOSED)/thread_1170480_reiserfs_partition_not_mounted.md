---
title: "reiserfs partition not mounted"
date: 2009-05-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xfranky on 2009-05-26
When trying to mount a reiserfs partition through gnome's interface, mounting fails telling that the 'reiser' filesystem is not supported.
Trying to mount the partition manually (mount on a precise mount point) worked, but I had to specify 'reiserfs' with -t; without it, it was autodetected as 'reiser'.
Any suggestions on where the problem lies and how to correct it?

Karmic updated today (26/5/2009); works as expected on Jaunty.

---

### Post by xfranky on 2009-05-27
> **xfranky said:**
> When trying to mount a reiserfs partition through gnome's interface, mounting fails telling that the 'reiser' filesystem is not supported.
Trying to mount the partition manually (mount on a precise mount point) worked, but I had to specify 'reiserfs' with -t; without it, it was autodetected as 'reiser'.
Any suggestions on where the problem lies and how to correct it?

Karmic updated today (26/5/2009); works as expected on Jaunty.

Is there anybody else having this problem, so we can confirm it's a bug somewhere?

---

### Post by davideotape on 2009-05-27
> **xfranky said:**
> Is there anybody else having this problem, so we can confirm it's a bug somewhere?

It might be worth filing a bugreport just to see if anyone esle has this problem. I doubt many people use reiserfs file systems though.

---

### Post by azhang2110 on 2009-05-28
> **xfranky said:**
> Is there anybody else having this problem, so we can confirm it's a bug somewhere?

yes, i have the same problem. and when i try to mount reiserfs filesystem the os mistakes it for reiser. it just say"cannot mount volume.  the volume uses the reiser file system which is not supported by your system. "

---

### Post by Hausi on 2009-05-28
silly thing tries to mount with filesystem-type "reiser". if you mount manually with -t reiserfs it works perfect.
_hans

---

