---
title: "Restoring backlight upon resume from suspend to RAM"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by maheshasolkar on 2009-08-15
Up until Jaunty, I used threads like the following, to fix the 'no backlight after resume' issue:

  [http://ubuntuforums.org/showthread.php?t=1174282](http://ubuntuforums.org/showthread.php?t=1174282)

Specifically, the following comment:

  [http://ubuntuforums.org/showpost.php?p=7675526&postcount=3](http://ubuntuforums.org/showpost.php?p=7675526&postcount=3)

The fix here involves setting some quirks in the /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux file.

This method won't work in Karmic.

With all the HAL related changes, I am wondering if this fix is now obsolete. If so, any idea how to restore backlight upon resume from suspend to RAM?

Even with all the HAL changes, I was expecting this to work:

```
  sudo pm-suspend --quirk-s3-bios --quirk-s3-mode --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore

```

But it doesn't.

I am using Sony VAIO VGN-T140P laptop.

---

### Post by gwydionwaters on 2009-10-10
i am having the same issue, i can tell everything but the screen returns from suspend as the hdd light goes a little and the wireless light goes orange > blue etc. i am using an hp dv6404ca running karmic 64b. thanks

---

### Post by cdahmedeh on 2009-10-10
Same problem here on Dell XPS m1530. Any existing bug report for this so that we can comment ?

---

### Post by gwydionwaters on 2009-10-11
there is now
[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/448676](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/448676)

---

### Post by gwydionwaters on 2009-10-26
mine works properly once my restricted 3d drivers are in use

---

### Post by maheshasolkar on 2009-10-26
> **cdahmedeh said:**
> Same problem here on Dell XPS m1530. Any existing bug report for this so that we can comment ?

Here's the bug I had opened for this issue:

  [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/417599](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/417599)

---

### Post by screaminj3sus on 2009-10-26
This probably won't be helpful for most but If you use your laptop plugged in most of the time just unplug and replug in your laptop.

---

