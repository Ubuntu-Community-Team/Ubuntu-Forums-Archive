---
title: "Unable to Mount USB Flash Drive"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iaskedalice09 on 2009-03-13
Hello,
Ubuntu's not automatically mounting my USB drive. It did before, I assume, because I could always browse files.

Any idea why this might be happening?

I tried manually mounting and unmounting and no luck.

Attached is the output of dmesg. Please feel free to review.

By the way, there was a previous thread that didn't work for me.

---

### Post by iaskedalice09 on 2009-03-14
bump

---

### Post by iaskedalice09 on 2009-03-14
*sigh* I found a fix [https://bugs.launchpad.net/ltsp/+bug/273147](https://bugs.launchpad.net/ltsp/+bug/273147)

How do I implement it?

---

### Post by scaine on 2009-03-14
The fix in that bug report appears to be for Hardy.  I don't know if it's still relevant, given that we've had Intrepid since then and you appear to be running Jaunty now.

Your dmesg looks fine, although I'm no expert.  What command did you use to try to manually mount the drive and what output did you get when it failed?  And what file system is on your usb stick?

I don't understand your reference to a previous thread?

---

### Post by cariboo on 2009-03-14
Your device is being mounted as a cdrom drive because of U3, Linux is giving it a device label of /dev/sdb1,

You could check /media/cdrom0 to see if it is mounted there, or you could try manually mounting the device:

```
sudo mount /dev/sdb1 /mnt
```

If you intend on using the device for storage, I would advise getting rid of U3. The easiest way to get rid of U3 is if you have a computer running WIndows use the disk management tools to reformat the device. It should them automagically mount.

Jim

---

### Post by iaskedalice09 on 2009-03-14
Removed the U3 partition after you suggested. Still won't mount. *sighs*

---

### Post by scaine on 2009-03-17
Ah well.  So what command did you try to mount the drive and what was the output?

Would also be interesting to see dmesg again now that you've removed the U3 stuff.

This is really odd.  I mean, I've had issues with permissions on certain USB keys when I plug them in, but I've never experienced a simple USB key that wouldn't mount before?!?

---

