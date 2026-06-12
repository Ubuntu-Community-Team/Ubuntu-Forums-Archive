---
title: "Do not load persistent file on Live USB install?"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by Fraoch on 2012-03-06
I seem to remember there's a boot parameter you can set to not load the persistent/settings files reserved on the USB stick.

Unfortunately my searching today isn't turning up anything.  Did I imagine it?

I think my persistent file is corrupted and it won't allow the install to proceed.

---

### Post by Lasall on 2012-03-06
Hi Fraoch,

just remove "persistent" kernel option.


Kind regards

Lasall

---

### Post by C.S.Cameron on 2012-03-06
When booting your flash drive, press F6 then edit to delete the word "persistent".

If your casper-rw file is full, say from trying to do an update, Persistent Ubuntu will not boot.

You can mount casper-rw and delete stuff off it to make it smaller:

```
sudo mkdir /media/casper
```

and then mount it:

```

sudo mount -o loop casper-rw /media/casper/
```


You could also just delete casper-rw to make the drive boot.

---

### Post by Fraoch on 2012-03-06
Thank you for all the responses!

I guess that should have been obvious.:oops:

I did end up re-writing the USB key which reformatted the persistent file.  The install went well and everything is now back to normal.

Thanks again.

---

